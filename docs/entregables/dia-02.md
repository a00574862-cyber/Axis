---
kaizen_dojo: "2026"
formato: "Entregable diario G2"
evidencia: "E2"
dia: 2
responsable_registro: "AXIS"
estado: "COMPLETADO"
fecha: "2026-10-27"
revision_docente: "PENDIENTE"
---

# E2 · Día 2 — HACER | Primera integración funcional y línea base V1

> **Regla:** sustituir los corchetes, registrar lo realmente observado y enlazar a evidencias del repositorio. **No inventar datos ni marcar pruebas no realizadas.** Los archivos del equipo resumen el trabajo compartido; las reflexiones y evidencias personales van en `participantes/<alias>/dias/E2.md`.

## 0 · Identificación y continuidad

| Campo | Dato |
|---|---|
| Fecha, equipo, misión y plataforma | 2026-10-27 · Axis · M04 · DJI Tello Camera (Python) |
| Dōjō real y mesa/zona utilizada | Campus León, Edificio CCI, pasillo del segundo piso (mismo lugar que el Día 1) |
| Estado del gate E1 / cambios desde D1 | Aprobado (ver [E1](dia-01.md)). Cambios: llegaron los carteles con las figuras |
| Kit por integrante / compromisos modificados | Sin modificaciones registradas. Kits en [`participantes/`](../../participantes/README.md) |
| Materiales recibidos y pendientes | Recibido: carteles de las figuras (MAT-005). Pendiente: baterías extras, que llegarán en unas dos semanas (MAT-002). Una de las baterías disponibles está en mal estado (rota) |
| Objetivo técnico del Día 2 | Que los 5 integrantes probaran las misiones de vuelo. El equipo indica que se avanzó "hasta V2"; por confirmar qué incluye esa V2 |

## 1 · Ruta de las actividades de hoy (180 min)

| Bloque | Minutos | Registro requerido / evidencia |
|---|---:|---|
| Revisión de misión y compromisos | 0–15 | Por confirmar |
| Microlección aplicada | 15–35 | Cómo completar las misiones. Referencia exacta por confirmar |
| Katas de integración | 35–105 | Los 5 integrantes: conexión del dron, vuelo, seguimiento de rutas de misión y paso de código por bloques a Python. Sin archivo ni foto enlazados |
| Ensayos iniciales / línea base | 105–145 | Rutas específicas indicadas por el profesor: avances de 50 cm, subida a 80 cm y giros de 90°. Sin valores medidos |
| Consolidación de evidencia | 145–170 | El código quedó en las laptops; sin commit en el repositorio |
| Gate E2 | 170–180 | El profesor otorgó el gate el Día 4 (ver sección 5) |

## 2 · Microlección e integración por alcances

**Tema que resolvió un problema real del equipo:** Cómo completar las misiones de vuelo. **Material / referencia utilizada:** Rutas específicas indicadas por el profesor; referencia por enlazar.

| Alias | Alcance | Kata seleccionado / nuevo | Acción técnica ejecutada | Archivo, commit o plano | Estado (pendiente/probado/bloqueado) | Dependencia de otro integrante |
|---|---|---|---|---|---|---|
| @a00574862-cyber | TL01, TL10 | Por confirmar cuál | Conexión del dron, vuelo, seguimiento de rutas y paso de código por bloques a Python | Código en mi laptop; sin ruta en el repositorio | Probado: conexión segura, avance y giro | Ninguna registrada |
| @TadeoGadu | TL01, TL10 | Por confirmar cuál | Conexión del dron, vuelo, seguimiento de rutas y paso de código por bloques a Python | Código en su laptop; sin ruta en el repositorio | Probado: conexión segura, avance y giro | Ninguna registrada |
| @KarolCabre | TL01, TL10 | Por confirmar cuál | Conexión del dron, vuelo, seguimiento de rutas y paso de código por bloques a Python | Código en su laptop; sin ruta en el repositorio | Probado: conexión segura, avance y giro | Ninguna registrada |
| @a00575206-droid | TL01, TL10 | Por confirmar cuál | Conexión del dron, vuelo, seguimiento de rutas y paso de código por bloques a Python | Código en su laptop; sin ruta en el repositorio | Probado: conexión segura, avance y giro | Ninguna registrada |
| @AdrianNavarroRomo | TL01, TL10 | Por confirmar cuál | Conexión del dron, vuelo, seguimiento de rutas y paso de código por bloques a Python | Código en su laptop; sin ruta en el repositorio | Probado: conexión segura, avance y giro | Ninguna registrada |

## 3 · Estado de integración V1

| Subsistema | Entrada | Salida esperada | Responsable | Prueba de integración y observación | Evidencia |
|---|---|---|---|---|---|
| Estructura/mecánica | Dron DJI Tello Camera | Plataforma en condiciones de vuelo | Por confirmar | Sin observación registrada | Sin evidencia |
| Energía y accionamiento | 2 baterías | Vuelo sin interrupciones | Por confirmar | Las baterías no estaban en buen estado y una estaba rota; las extras llegan en unas dos semanas | Sin evidencia |
| Sensores/percepción | Cámara del Tello | Lectura de figuras | Por confirmar | No probada en el Día 2 | Sin evidencia |
| Control/software | Código por bloques pasado a Python | Conexión, avance y giro | Los 5 integrantes | Funcionaron la conexión segura, el avance y el giro. Las librerías no estaban actualizadas en Visual Studio | Código en las laptops |
| Integración global | Rutas indicadas por el profesor | Cumplir la ruta | Los 5 integrantes | Se cumplieron avances de 50 cm, subida a 80 cm y giros de 90°, sin medición | Sin evidencia enlazada |

**Versión identificable:** Sin commit ni etiqueta; el código está en las laptops de los integrantes. **Comportamiento que SÍ demuestra V1:** Conexión segura, avance y giro. Nada más. **Lo que aún falla:** Las librerías no estaban actualizadas en Visual Studio. No se probaron la cámara ni la detección de figuras.

## 4 · Protocolo y línea base del robot (datos observados)

Completar también [`pruebas/protocolo.md`](../../pruebas/protocolo.md) y registrar datos crudos en [`datos/ensayos.csv`](../../datos/ensayos.csv).

| Campo de validez experimental | Respuesta obligatoria |
|---|---|
| Pregunta y resultado que se quiere medir | No se definió una pregunta de medición. Se verificó que el dron cumpliera las maniobras de las rutas del profesor |
| Métrica primaria + unidad (segundos, %, cm, rad, etc.) | No medida |
| Éxito/fallo (criterio cuantitativo u observable) | Observable: que el dron cumpla el avance, la subida y el giro indicados |
| Lugar, configuración, pista/dohyō/estaciones/marcadores | Pasillo del segundo piso del CCI. Configuración exacta de la pista por confirmar |
| Configuración del robot: batería, firmware y sensores | DJI Tello Camera. Baterías en mal estado, una rota. Firmware y sensores sin registrar |
| Condiciones controladas: luz, rival, posición de inicio, etc. | Sin registro |
| Número de corridas planeadas / ejecutadas | Sin registro de corridas. No se llegó a 5 ensayos medidos |
| Procedimiento reproducible, responsable y seguridad/aborto | Maniobras de las rutas del profesor. Responsable y aborto: por confirmar |
| Datos sin procesar y video/foto corta | No se registraron datos en [`datos/ensayos.csv`](../../datos/ensayos.csv) |

Los ensayos no fueron exactos ni medidos. No se registraron valores, así que no hay datos que anotar en la tabla de ensayos.

| Ensayo | Condición inicial | Valor (+ unidad) | Éxito/fallo | Observación relevante / incidencia |
|---:|---|---|---|---|
| 1 | Maniobra de avance de la ruta | No medido | Cumplido (observado) | Avance de 50 cm |
| 2 | Maniobra de subida de la ruta | No medido | Cumplido (observado) | Subida a 80 cm |
| 3 | Maniobra de giro de la ruta | No medido | Cumplido (observado) | Giro de 90° |
| 4 | — | — | No realizado | No hubo más ensayos registrados |
| 5 | — | — | No realizado | No hubo más ensayos registrados |

**Línea base resumida (no fabricada):** No hay línea base cuantitativa. No se midieron valores, así que no hay media ni dispersión ni tasa de éxito. Qué sí se observó: las maniobras indicadas se cumplieron. No se descartó ningún ensayo.

## 5 · Decisiones al cierre, bloqueos y Kaizen de mañana

| Fallo o cuello de botella observado | Hipótesis preliminar | Prioridad | Responsable | Material / apoyo necesario |
|---|---|---|---|---|
| Las librerías no estaban actualizadas en Visual Studio | Versiones desactualizadas en las laptops | Por confirmar | Por confirmar | Actualizar las librerías |
| Una batería rota y solo 2 disponibles | Desgaste o daño de la batería | Por confirmar | Por confirmar | Baterías extras (llegan en unas dos semanas) |
| Sin evidencia ni commits en el repositorio | El código está en las laptops | Por confirmar | Por confirmar | Subir el código a `codigo/tello/` |

- [x] Hay prototipo V1, subsistema funcional verificable o fallo reproducible con condiciones registradas.
- [x] Existen archivos fuente o evidencia técnica enlazada, además de videos de uso controlado cuando correspondan.
- [x] Hay protocolo reproducible y valores basales con unidad o justificación de lo que no pudo medirse.
- [x] Cada alumno actualizó su [E2 personal](../../participantes/_plantilla/dias/E2.md) con contribución propia y límite de capacidad actual.
- [x] Se mantuvieron límites de seguridad y protección de datos.

**Gate E2:** Otorgado por el profesor el Día 4, según informa el equipo (estado exacto por confirmar). **Revisor:** Camilo René Duque Becerra. **Fecha:** Día 4.

**Próxima prioridad de Kaizen 1:** Por confirmar. **Enlace al commit/PR:** Por enlazar.
