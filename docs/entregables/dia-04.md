---
kaizen_dojo: "2026"
formato: "Entregable diario G2"
evidencia: "E4"
dia: 4
responsable_registro: "equipo"
estado: "PENDIENTE"
fecha: "2026-10-30"
revision_docente: "PENDIENTE"
---

# E4 · Día 4 — ITERAR | Kaizen 2, robustez y preparación de demostración

> **Regla:** sustituir los corchetes, registrar lo realmente observado y enlazar a evidencias del repositorio. **No inventar datos ni marcar pruebas no realizadas.** Los archivos del equipo resumen el trabajo compartido; las reflexiones y evidencias personales van en `participantes/<alias>/dias/E4.md`.

> **Estado de este borrador:** lo escrito abajo viene de lo que el equipo observó en los vuelos. Todo lo marcado **⚠ PENDIENTE** requiere un dato real (cifras de ensayos, IDs de commit, observaciones de pares) y **no debe llenarse hasta que exista**.

## 0 · Contexto

**Fecha y dōjō:** 2026-10-30 (confirmar) · **Equipo/misión:** Equipo Axis (Drones Axis, Tec Campus León) · Misión M04 · Reto *Decide & Fly* con DJI Tello, Python y OpenCV.

**Versiones trazables** (V = versión inicial; K = ciclo Kaizen, es decir, una mejora sobre la versión anterior):

| Versión | Qué era (según lo observado en los vuelos) | Id de commit |
|---|---|---|
| V1 | Primer vuelo con `--fly`: el dron **solo despegaba**, no avanzaba | ⚠ PENDIENTE |
| K1 | Primera mejora: el dron **ya avanzaba y la cámara detectaba**, pero el video salía con los **colores invertidos** (todos nos veíamos azules). Después se corrigió el orden de canales de color (`FRAME_ES_RGB`) y volvió a detectar | ⚠ PENDIENTE |
| K2 | Segunda mejora: con color corregido, **solo detectaba bien el círculo**; se cambió a **detección por forma** y **ya funcionó bien** | ⚠ PENDIENTE |

> ⚠ Confirmar con el equipo que esta división V1/K1/K2 es la que quieren registrar.

**Integrantes (todos de Ingeniería en Mecatrónica, IMT):**

| Integrante | Matrícula | Correo Tec | Rol |
|---|---|---|---|
| Carlos Tadeo Garay Durán | A00574676 | A00574676@tec.mx | Capitán |
| Karol Daniel Cabrera Ramirez | A00574791 | A00574791@tec.mx | Finanzas |
| Andrés Alejandro Sánchez Rábago | A00574862 | a00574862@tec.mx | Vinculación y difusión |
| Pedro Hernández | A00575206 | A00575206@tec.mx | Programación |
| Adrián Navarro Romo | A00575101 | A00575101@tec.mx | Hardware y pruebas |

**Profesor asesor:** Camilo René Duque Becerra · camilo.duque@tec.mx

## 1 · Ruta de actividades del Día 4 (180 min)

| Actividad | Minutos | Registro requerido |
|---|---|---|
| Revisión por pares y retroalimentación | 0–20 | Observaciones internas del equipo y retroalimentación del profesor, con sus decisiones (sección 2) |
| Diseño/ejecución Kaizen 2 | 20–70 | K2: pasar de detección por **color** a detección por **forma** (sección 3) |
| Comparación V1–K1–K2 | 70–115 | Descripción de lo observado en cada versión (sección 4); ⚠ PENDIENTE las cifras |
| Ensayo de robustez | 115–145 | ⚠ PENDIENTE: perturbación controlada y seguridad (sección 5) |
| Preparación de demo | 145–165 | Guion y responsables propuestos en la sección 6; confirmar |
| Gate de preparación | 165–180 | ⚠ PENDIENTE: decisión y pendientes (sección 7) |

## 2 · Revisión por pares

| Persona o equipo observador (alias) | Evidencia revisada | Observación útil / pregunta | Respuesta técnica y decisión | Cambio aceptado o descartado |
|---|---|---|---|---|
| Andrés Alejandro Sánchez Rábago | Primer vuelo real con `--fly` | El dron solo se levantaba y no avanzaba | Se corrigió el código para que avanzara | Aceptado: el dron ya avanza |
| Carlos Tadeo Garay Durán | Video de la cámara del Tello durante el vuelo | Los colores salían invertidos (todos se veían azules) | Se corrigió el orden de canales de color (`FRAME_ES_RGB`) | Aceptado: corrección de colores; la detección volvió a funcionar |
| Pedro Hernández y Adrián Navarro Romo | Reconocimiento de las figuras con la cámara | Con los colores corregidos solo se reconocía bien el círculo; verificaron que la figura se identificara bien | Se cambió a detección por forma (K2) | Aceptado: detección por forma; las figuras ya se reconocen bien |
| Karol Daniel Cabrera Ramirez y Pedro Hernández | Recorrido completo del dron | Verificaron que el dron cumpliera el recorrido; **no podía avanzar por la batería (pila)** | Se corrigió el código: versión final `prueba_vuelo_figuras.py` (despega, lee la señal, avanza 50 cm o gira 90° y avanza, y revisa la batería antes de volar) | Aceptado: el dron ya avanza |
| Camilo René Duque Becerra (profesor asesor) | Prueba de vuelo del dron | Es necesario que el dron **detecte mejor las figuras** y que el **avance sea correcto** | Detección: se cambió a detección por forma (K2). Avance: se corrigió el código (`prueba_vuelo_figuras.py`) porque el dron no podía avanzar por la batería (pila), en la parte de Pedro y Karol | Detección: aceptado (K2). Avance: aceptado |

*Las cuatro primeras filas son observaciones internas del equipo durante los vuelos reales. La del profesor es la única revisión externa; ningún otro equipo los ha revisado.*

**Acuerdo de colaboración:** El equipo se repartió la observación de los vuelos por aspecto: Carlos Tadeo los colores, Andrés que el dron se levantara y avanzara, Pedro y Adrián que la figura se reconociera bien, y Karol que se cumpliera el recorrido. Cada observación se convirtió en un ajuste del código. El profesor Camilo fue el único que revisó la prueba y pidió mejor detección de las figuras y un avance correcto; el equipo tomó esa retroalimentación para ajustar el código. ⚠ PENDIENTE: agregar cómo se escucharon y se repartieron las respuestas a esa retroalimentación.

## 3 · Segundo ciclo Kaizen (K2)

| Campo experimental | Completar |
|---|---|
| Limitación o nueva oportunidad detectada en K1 | Con los colores ya corregidos, el dron avanzaba y detectaba, pero **solo reconocía bien el círculo**; los triángulos no se detectaban de forma confiable. La detección por color (HSV) dependía de la luz y del color de cada figura. |
| Hipótesis K2 y fundamento | Si el reconocimiento se hace por **forma** (escala de grises + umbral de Otsu + número de vértices + circularidad) y no por color, entonces el sistema reconocerá círculo y triángulos sin depender del color ni del orden de canales RGB/BGR. Fundamento: un código por forma del equipo (`tello_camara_gate1.py`) sí detectó las figuras en la cámara. |
| Variable modificada y controles | **Modificada:** método de detección (color HSV → forma). **Controlados (propuesta):** misma cámara del Tello, misma distancia a la figura (~1 m), figura centrada sobre papel blanco, misma iluminación, misma impresión de las figuras. |
| Requisitos de seguridad antes del cambio | Probar primero sin motores (`prueba_vuelo_figuras.py` sin `--fly`). Vuelo solo con batería ≥ 60 %, protectores de hélice, zona libre y confirmación escrita `VOLAR`. Si no hay señal confiable, el dron aterriza sin moverse. |
| Personas responsables y alcances implicados | Pedro Hernández y Adrián Navarro Romo: verificar que la figura se reconozca bien. Andrés Alejandro Sánchez Rábago: que el dron se levante y avance. Carlos Tadeo Garay Durán: colores. Karol Daniel Cabrera Ramirez: que cumpla el recorrido. |
| Cambio exacto de código/CAD/configuración | Archivo `prueba_vuelo_figuras.py`: función `detectar_senal()` por forma. Círculo → CONTINUAR (avanza 50 cm). Triángulo a la izquierda → IZQUIERDA (gira 90° izq. y avanza 50 cm). Triángulo a la derecha → DERECHA (gira 90° der. y avanza 50 cm). Triángulo hacia arriba → CONTINUAR. Triángulo hacia abajo → se ignora. Exige 5 lecturas iguales y 0.5 s antes de actuar. Antes de despegar revisa la batería y cancela el vuelo si está por debajo de 60 %; fija la velocidad en 30 cm/s. **Origen del código:** elaborado con ayuda del asistente Claude (IA) a partir del detector por forma del equipo (`tello_camara_gate1.py`) y probado por el equipo en vuelo real. |
| Enlace a commit, PR y versión K2 | ⚠ PENDIENTE: pegar enlace al commit/PR |
| Métrica, unidad y criterio para declarar éxito | **Métrica (propuesta):** señales correctas / ensayos, por figura (aciertos de N). **Criterio (propuesta, el equipo debe confirmarlo):** al menos 4 de 5 ensayos correctos por figura. ⚠ PENDIENTE: contar cuántos ensayos hicieron en realidad. |

## 4 · Comparación de evolución

**Qué se observó en cada versión (sin cifras):**

| Etapa | Qué pasó en el vuelo real |
|---|---|
| V1 | El dron solo se levantaba; no avanzaba. |
| K1 | Ya avanzaba y la cámara detectaba, pero los colores estaban invertidos (se veían azules). Al corregir el orden de canales volvió a detectar. |
| K2 | Con colores corregidos solo detectaba bien el círculo. Con detección por forma, ya funcionó bien con las figuras. |

**Qué observó cada integrante durante las pruebas:**

| Integrante | Qué observó |
|---|---|
| Carlos Tadeo Garay Durán | Los colores (la inversión de colores en el video) |
| Andrés Alejandro Sánchez Rábago | Que el dron se levantara y avanzara |
| Pedro Hernández y Adrián Navarro Romo | Que verificara bien la figura |
| Karol Daniel Cabrera Ramirez | Que cumpliera el recorrido |

**Tabla de ensayos pareados:**

| Ensayo/condición equivalente | V1 (valor + unidad) | K1 (valor + unidad) | K2 (valor + unidad) | Incidencias o validez |
|---:|---|---|---|---|
| 1 | ⚠ PENDIENTE | ⚠ PENDIENTE | ⚠ PENDIENTE | ⚠ PENDIENTE |
| 2 | ⚠ PENDIENTE | ⚠ PENDIENTE | ⚠ PENDIENTE | ⚠ PENDIENTE |
| 3 | ⚠ PENDIENTE | ⚠ PENDIENTE | ⚠ PENDIENTE | ⚠ PENDIENTE |
| 4 | ⚠ PENDIENTE | ⚠ PENDIENTE | ⚠ PENDIENTE | ⚠ PENDIENTE |
| 5 | ⚠ PENDIENTE | ⚠ PENDIENTE | ⚠ PENDIENTE | ⚠ PENDIENTE |

**Registros fuente:** [`datos/ensayos.csv`](../../datos/ensayos.csv) y protocolo [enlace ⚠ PENDIENTE].

**Síntesis (método, n, media/mediana, dispersión y éxito cuando proceda):** ⚠ PENDIENTE: no se registraron cifras; si no se anotaron aciertos por ensayo, hacerlo en una repetición corta (por ejemplo 5 intentos por figura) y registrarlos aquí.

**¿Qué mejora, qué empeora y qué no podemos concluir?** Mejora (observado): el dron pasó de solo despegar a avanzar, y de detectar solo el círculo a funcionar bien con las figuras. Lo que no podemos concluir todavía: cuántas veces acierta de cada 10 y si resiste cambios de luz o distancia, porque no hay cifras.

*Nota:* además, `prueba_vuelo_figuras.py` se verificó con imágenes sintéticas generadas por computadora (círculo, triángulos izquierda, derecha y arriba correctos; triángulo hacia abajo y fondo vacío sin señal). Eso **no es un ensayo con el dron** y no cuenta como dato de la tabla.

## 5 · Ensayo de robustez o variación de condiciones

| Cambio controlado de entorno (luz, suelo, batería, posición, rival, obstáculo o carga) | Riesgo y límite seguro | Predicción | Resultado / unidad / éxitos | ¿Se mantiene el objetivo? | Evidencia |
|---|---|---|---|---|---|
| Propuesta: cambiar la **iluminación** y la **distancia** a la figura (0.5 m a 1.5 m), con el dron en el suelo y **sin motores** | Sin despegar: riesgo bajo. No volar con baja luz ni con batería < 60 % | La detección por forma se mantiene mientras la figura esté completa y centrada; se degrada con poca luz o si la figura toca los bordes de la imagen | ⚠ PENDIENTE | ⚠ PENDIENTE | ⚠ PENDIENTE (foto o video) |

**Límites de inferencia:** ⚠ PENDIENTE: indicar cuántas pruebas se hicieron, si el cambio de entorno impide comparar V1–K2 directamente y qué hay que repetir.

## 6 · Ensayo general de demostración

> Los responsables son una **propuesta** basada en los roles del equipo y en lo que cada uno observó. Confirmar con el equipo.

| Segmento | Qué se demostrará en 20–60 s | Integrante responsable | Versión/código usado | Material requerido | Plan B ante fallo |
|---|---|---|---|---|---|
| Inicio / contexto | El reto: un dron que decide solo su camino a partir de señales visuales | Carlos Tadeo Garay Durán (capitán) | — | Plano del circuito y figuras impresas | Explicar con el plano impreso |
| Prueba principal | El dron despega, lee una figura con la cámara y actúa: avanza, o gira y avanza | Pedro Hernández (programa) y Adrián Navarro Romo (dron y figuras) | `prueba_vuelo_figuras.py --fly` (K2) | Tello con batería ≥ 60 %, protectores de hélice, figuras, zona libre | Mostrar el video de una prueba exitosa o correr `--ver-camara` sin volar |
| Evidencia de mejora | Mostrar la evolución: V1 solo despegaba → K1 avanzaba → K2 detecta bien por forma | Karol Daniel Cabrera Ramirez (recorrido) | V1, K1 y K2 (IDs ⚠ PENDIENTE) | Tabla de la sección 4 | Mostrar fotos o capturas de la detección |
| Defensa de fronteras | Qué no se garantiza: posición exacta, deriva del dron, luz, obstáculos | Andrés Alejandro Sánchez Rábago | — | Tabla de robustez y límites de inferencia | Responder con la sección 5 |

**¿Robolympics es el evento externo posterior?** Por confirmar. El equipo planea participar en Robolympics (Tec Campus León); confirmar con el profesor Camilo René Duque Becerra si ese es el evento posterior. Si es posterior, D5 documenta una **demostración/calificación interna**; no registrar participación externa como realizada.

## 7 · Gate E4

- [ ] Existe un ciclo K2 explícito, con hipótesis, modificación y datos. *(Hipótesis y modificación sí; faltan las cifras de ensayos.)*
- [ ] Se conservan V1, K1, K2 y, en su caso, reversiones para reproducibilidad. *(Faltan los IDs de versión.)*
- [ ] Se efectuó una prueba de robustez documentada o se justificó por qué no era segura/factible.
- [ ] El equipo tiene guion, responsabilidades y plan de contingencia para D5. *(Propuesta en sección 6, falta confirmarla.)*
- [ ] Cada participante actualizó [E4 personal](../../participantes/_plantilla/dias/E4.md).

**Estado de preparación:** CON RESTRICCIONES (el dron ya despega, avanza y detecta por forma, pero faltan cifras de ensayos y la prueba de robustez). **Pendientes y responsables:** (1) registrar aciertos por figura en una repetición corta · Pedro Hernández y Adrián Navarro Romo; (2) pegar IDs de commit/PR · Pedro Hernández; (3) prueba de robustez de luz y distancia · Adrián Navarro Romo; (4) confirmar si Robolympics es el evento posterior · Carlos Tadeo Garay Durán con el profesor. **Revisor:** Camilo René Duque Becerra (profesor asesor).
