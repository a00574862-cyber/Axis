# -*- coding: utf-8 -*-
"""Prueba 2 - Reconocer figuras por FORMA y ejecutar un movimiento corto con el DJI Tello.

Señales (solo por forma, no depende del color):
    Circulo                    -> CONTINUAR  -> avanza 50 cm
    Triangulo hacia arriba     -> CONTINUAR  -> avanza 50 cm
    Triangulo hacia la IZQ.    -> IZQUIERDA  -> gira 90° a la izquierda y avanza 50 cm
    Triangulo hacia la DER.    -> DERECHA    -> gira 90° a la derecha y avanza 50 cm

Uso en la terminal de VS Code:
    python prueba_vuelo_figuras.py          # SOLO camara: muestra que haria, NO vuela
    python prueba_vuelo_figuras.py --fly    # VUELO REAL: despega, lee una señal, actua y aterriza

Q o ESC en la ventana para terminar la prueba de camara.
"""
import argparse
import math
import sys
import time

import cv2
import numpy as np

# --- 1. CONFIGURACION ---
VENTANA = "Tello - Prueba 2 - Figuras"
CONFIRMACIONES = 5          # fotogramas consecutivos con la misma señal
TIEMPO_CONFIRMACION = 0.5   # s minimos reconociendo la misma señal
SEGUNDOS_SIN_VIDEO = 4      # salir si el stream deja de actualizarse
TIEMPO_MAX_LECTURA = 10.0   # s maximos esperando una señal en vuelo
BATERIA_MIN = 60            # % minimo para volar
VELOCIDAD = 30              # cm/s
AVANCE_CM = 50              # distancia de cada avance
GIRO_GRADOS = 90            # giro de la prueba

# Que hace el dron con cada señal (nombre de metodo djitellopy, argumento)
ACCIONES = {
    "CONTINUAR": [("move_forward", AVANCE_CM)],
    "IZQUIERDA": [("rotate_counter_clockwise", GIRO_GRADOS), ("move_forward", AVANCE_CM)],
    "DERECHA":   [("rotate_clockwise", GIRO_GRADOS), ("move_forward", AVANCE_CM)],
}


# --- 2. RECONOCER POR FORMA ---
def detectar_senal(imagen_bgr):
    """Devuelve (señal o None, lista de (señal, contorno))."""
    gris = cv2.cvtColor(imagen_bgr, cv2.COLOR_BGR2GRAY)
    desenfocado = cv2.GaussianBlur(gris, (5, 5), 0)
    _, umbral = cv2.threshold(desenfocado, 0, 255, cv2.THRESH_BINARY_INV + cv2.THRESH_OTSU)

    alto, ancho = imagen_bgr.shape[:2]
    area_minima = 0.01 * alto * ancho
    contornos, _ = cv2.findContours(umbral, cv2.RETR_EXTERNAL, cv2.CHAIN_APPROX_SIMPLE)
    detectados = []

    for contorno in contornos:
        area = cv2.contourArea(contorno)
        perimetro = cv2.arcLength(contorno, True)
        if not area_minima <= area <= 0.65 * alto * ancho or perimetro == 0:
            continue

        x, y, w, h = cv2.boundingRect(contorno)
        if x <= 2 or y <= 2 or x + w >= ancho - 2 or y + h >= alto - 2:
            continue

        vertices = cv2.approxPolyDP(contorno, 0.025 * perimetro, True)
        area_convexa = cv2.contourArea(cv2.convexHull(contorno))
        solidez = area / area_convexa if area_convexa else 0
        circularidad = 4 * math.pi * area / (perimetro ** 2)

        # CIRCULO -> CONTINUAR
        if circularidad >= 0.72:
            if 0.75 <= float(w) / h <= 1.30 and solidez >= 0.85:
                detectados.append(("CONTINUAR", contorno))

        # TRIANGULO -> direccion segun hacia donde apunta el vertice
        elif len(vertices) == 3 and cv2.isContourConvex(vertices) and solidez >= 0.85:
            m = cv2.moments(contorno)
            if m["m00"] == 0:
                continue
            cx, cy = m["m10"] / m["m00"], m["m01"] / m["m00"]
            dx = (cx - (x + w / 2)) / w   # >0: masa a la derecha -> vertice a la IZQUIERDA
            dy = (cy - (y + h / 2)) / h   # >0: masa abajo -> vertice ARRIBA
            if abs(dx) >= abs(dy):
                detectados.append(("IZQUIERDA" if dx > 0 else "DERECHA", contorno))
            elif dy > 0:
                detectados.append(("CONTINUAR", contorno))   # triangulo hacia arriba
            # triangulo hacia abajo: se ignora

    decisiones = {s for s, _ in detectados}
    decision = next(iter(decisiones)) if len(decisiones) == 1 else None
    return decision, detectados


# --- 3. VIDEO CON RESULTADO ---
def mostrar_video(imagen_bgr, detectados, mensaje, pie):
    vista = imagen_bgr.copy()
    colores = {"CONTINUAR": (0, 200, 0), "IZQUIERDA": (255, 165, 0), "DERECHA": (0, 0, 255)}
    for senal, contorno in detectados:
        cv2.drawContours(vista, [contorno], -1, colores.get(senal, (255, 255, 255)), 3)
    cv2.rectangle(vista, (0, 0), (vista.shape[1], 63), (25, 25, 25), -1)
    cv2.putText(vista, mensaje, (12, 25), cv2.FONT_HERSHEY_SIMPLEX, 0.58, (255, 255, 255), 2)
    cv2.putText(vista, pie, (12, 51), cv2.FONT_HERSHEY_SIMPLEX, 0.52, (255, 255, 255), 1)
    cv2.imshow(VENTANA, vista)


def frame_bgr(lector, ultima):
    """Devuelve un fotograma nuevo en BGR (640 px de ancho) o None."""
    frame = lector.frame
    if frame is None or not frame.size or not np.any(frame) or frame is ultima:
        return None, ultima
    img = cv2.cvtColor(frame.copy(), cv2.COLOR_RGB2BGR)     # el Tello entrega RGB
    alto = round(img.shape[0] * 640 / img.shape[1])
    return cv2.resize(img, (640, alto)), frame


class Confirmador:
    """Acepta una señal solo tras varias lecturas iguales seguidas."""
    def __init__(self):
        self.candidata, self.contador, self.inicio = None, 0, 0.0

    def actualizar(self, decision, ahora):
        if decision is None:
            self.candidata, self.contador = None, 0
            return None, "Sin una figura valida"
        if decision != self.candidata:
            self.candidata, self.contador, self.inicio = decision, 1, ahora
        else:
            self.contador += 1
        if self.contador >= CONFIRMACIONES and ahora - self.inicio >= TIEMPO_CONFIRMACION:
            return decision, f"CONFIRMADA: {decision}"
        return None, f"Confirmando {decision}: {min(self.contador, CONFIRMACIONES)}/{CONFIRMACIONES}"


# --- 4. EJECUTAR LA ACCION ---
def ejecutar(senal, dron=None):
    """Con dron=None solo imprime lo que haria."""
    for metodo, valor in ACCIONES[senal]:
        print(f"   -> {metodo}({valor})" + ("" if dron else "   [SIN VOLAR]"))
        if dron is not None:
            getattr(dron, metodo)(valor)


# --- 5. MODO CAMARA (sin volar) ---
def modo_camara():
    from djitellopy import Tello
    dron = Tello(retry_count=1)
    print("Conectando al Tello por Wi-Fi...")
    try:
        dron.connect()
        print(f"Bateria: {dron.get_battery()}%  |  MODO CAMARA: no despega")
        dron.streamon()
        lector = dron.get_frame_read()
        cv2.namedWindow(VENTANA, cv2.WINDOW_AUTOSIZE)
        conf, ultima, ultimo_video, reportada = Confirmador(), None, time.monotonic(), None
        while True:
            ahora = time.monotonic()
            img, ultima_nueva = frame_bgr(lector, ultima)
            if img is None:
                if ahora - ultimo_video > SEGUNDOS_SIN_VIDEO:
                    raise RuntimeError("No llegan imagenes nuevas del Tello.")
                if cv2.waitKey(1) & 0xFF in (ord("q"), ord("Q"), 27):
                    break
                time.sleep(0.04)
                continue
            ultima, ultimo_video = ultima_nueva, ahora
            decision, detectados = detectar_senal(img)
            senal, mensaje = conf.actualizar(decision, ahora)
            if senal and reportada != senal:
                print(f"DECISION: {senal}")
                ejecutar(senal, None)
                reportada = senal
            elif senal is None and decision is None:
                reportada = None
            mostrar_video(img, detectados, mensaje, "Q / ESC: salir - SIN DESPEGAR")
            if cv2.waitKey(1) & 0xFF in (ord("q"), ord("Q"), 27):
                break
            if cv2.getWindowProperty(VENTANA, cv2.WND_PROP_VISIBLE) < 1:
                break
    finally:
        try:
            dron.end()
        except Exception as e:
            print(f"Aviso al cerrar: {e}")
        cv2.destroyAllWindows()
        print("Prueba finalizada.")


# --- 6. MODO VUELO ---
def modo_vuelo():
    print("ATENCION: zona libre, helices con proteccion, figura frente al dron a ~1 m.")
    print("Secuencia: despega -> lee UNA señal -> actua -> aterriza.")
    if input("Teclee VOLAR para confirmar: ").strip() != "VOLAR":
        return
    from djitellopy import Tello
    dron = Tello(retry_count=1)
    aire = False
    try:
        dron.connect()
        nivel = dron.get_battery()
        print(f"Bateria: {nivel}%")
        if nivel < BATERIA_MIN:
            raise RuntimeError(f"Bateria inferior a {BATERIA_MIN}%; vuelo cancelado")
        dron.set_speed(VELOCIDAD)
        dron.streamon()
        lector = dron.get_frame_read()
        time.sleep(2)

        dron.takeoff()
        aire = True
        time.sleep(1.5)                       # estabiliza antes de leer

        cv2.namedWindow(VENTANA, cv2.WINDOW_AUTOSIZE)
        conf, ultima = Confirmador(), None
        t0, senal = time.monotonic(), None
        while time.monotonic() - t0 < TIEMPO_MAX_LECTURA and senal is None:
            ahora = time.monotonic()
            img, nueva = frame_bgr(lector, ultima)
            if img is None:
                cv2.waitKey(1)
                time.sleep(0.04)
                continue
            ultima = nueva
            decision, detectados = detectar_senal(img)
            senal, mensaje = conf.actualizar(decision, ahora)
            mostrar_video(img, detectados, mensaje, "Leyendo señal en vuelo...")
            if cv2.waitKey(1) & 0xFF in (ord("q"), ord("Q"), 27):
                print("Cancelado por el operador.")
                break

        if senal is None:
            print("SIN SEÑAL CONFIABLE: aterrizando sin moverse.")
        else:
            print(f"DECISION: {senal}")
            ejecutar(senal, dron)

        dron.land()
        aire = False
    finally:
        if aire:
            try:
                dron.land()
            except Exception as e:
                print(f"ALERTA: no se pudo confirmar aterrizaje: {e}", file=sys.stderr)
        try:
            dron.streamoff()
            dron.end()
        except Exception:
            pass
        cv2.destroyAllWindows()
        print("Prueba finalizada.")


if __name__ == "__main__":
    ap = argparse.ArgumentParser()
    ap.add_argument("--fly", action="store_true", help="vuelo real (pide escribir VOLAR)")
    args = ap.parse_args()
    modo_vuelo() if args.fly else modo_camara()
