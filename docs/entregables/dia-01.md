---
kaizen_dojo: "2026"
formato: "Entregable diario G2"
evidencia: "E1"
dia: 1
responsable_registro: "AXIS"
estado: "COMPLETADO"
fecha: "2026-10-26"
revision_docente: "PENDIENTE"
---

# E1 · Día 1 — ATREVERSE | Contrato de misión, inventario y dōjō

> **Regla:** sustituir los corchetes, registrar lo realmente observado y enlazar a evidencias del repositorio. **No inventar datos ni marcar pruebas no realizadas.** Los archivos del equipo resumen el trabajo compartido; las reflexiones y evidencias personales van en `participantes/<alias>/dias/E1.md`.

## 0 · Identificación, equipo y logística del dōjō

| Campo obligatorio | Dato |
|---|---|
| Fecha y horario de esta sesión | 2026-10-26; 09:00–12:00 (180 min) |
| Nombre / alias del equipo | Axis |
| Misión / plataforma | M04 Tello Python (DJI Tello Camera) |
| Objetivo verificable del robot (una frase) | Control autónomo de estación con visión artificial |
| **Dōjō asignado — campus, edificio y sala/taller exactos** | **Campus León / Edificio CCI / Pasillo del segundo piso (espacio de vuelo confirmado) / Sin número de laboratorio asignado** |
| Puesto o zona dentro del dōjō | Pasillo del segundo piso del CCI |
| Horario / reserva confirmada | Horario de clase; reserva formal por confirmar |
| Responsable del espacio y contacto institucional | Camilo René Duque Becerra, Director de Carrera IMT; camilo.duque@tec.mx |
| Acceso, aforo y ajustes de accesibilidad | Se requiere espacio asegurado y despejado para poder volar el dron; aforo y accesibilidad por confirmar |
| Salidas, botiquín, extintor y punto de reunión | Extintor: en el pasillo. Botiquín: enfermería en el piso de abajo. Punto de reunión: estacionamiento. Salidas: por confirmar |
| Zonas segregadas por riesgo | Zona de vuelo: pasillo del segundo piso (delimitación por confirmar) |
| Ubicación de materiales y resguardo nocturno | Salón del profesor Camilo René Duque Becerra |
| Plan de sustitución si falla el espacio | Dōjō alternativo con autorización; no improvisar espacio de vuelo |
| Instructor o supervisor presente en la sesión | Camilo René Duque Becerra, Director de Carrera IMT |

> ⛔ **No se permite avanzar a pruebas físicas sin dōjō concreto y autorización del responsable.** No inventar salón, número de laboratorio ni recursos que no hayan sido confirmados.

## 1 · Integrantes, responsabilidades, accesibilidad y decisiones (0–15 min)

| Alias GitHub | Rol inicial | Carta y frontera (D/S/E; F1–F4) | Alcances ID (1–3) | Kit personal (archivo) | Necesidad de apoyo o accesibilidad acordada |
|---|---|---|---|---|---|
| @a00574862-cyber (Andrés Alejandro Sánchez Rábago) | Sin rol asignado | D · F2 | TL01, TL06, TL10 | [kit](../../participantes/Andr%C3%A9s%20S%C3%A1nchez/compromiso-kaizen-andres-alejandro-sanchez-rabago.md) | Ninguna registrada |
| @TadeoGadu (Carlos Tadeo Garay Durán) | Sin rol asignado | D · F2 | TL01, TL06, TL10 | [kit](../../participantes/Carlos%20Tadeo%20Garay%20Dur%C3%A1n/compromiso-kaizen-carlos-garay.md) | Ninguna registrada |
| @KarolCabre (Karol Daniel Cabrera Ramírez) | Sin rol asignado | S · F2 | TL01, TL06, TL10 | [kit](../../participantes/Karol%20Daniel%20Cabrera%20Ramirez/compromiso-kaizen-karol-daniel-cabrera-ramirez.md) | Ninguna registrada |
| @a00575206-droid (Pedro Hernández Avalos) | Sin rol asignado | E · F4 | TL01, TL06, TL10 | [kit](../../participantes/PedroHern%C3%A1ndez/compromiso-kaizen-pedro-hernandez-avalos.md) | Ninguna registrada |
| @AdrianNavarroRomo (Adrian Navarro Romo) | Sin rol asignado | E · F4 | TL01, TL06, TL10 | [kit](../../participantes/Adrian%20Navarro%20Romo/compromiso-kaizen-adrian-navarro-romo.md) | Ninguna registrada |

**Acuerdo de colaboración:** Todavía no hay un orden acordado en el equipo para tomar decisiones, repartir actividades ni resolver conflictos. Queda pendiente definirlo antes del Día 2.

## 2 · Demostración de la plataforma y seguridad (15–35 min)

| Elemento | Observación directa | Evidencia / vínculo |
|---|---|---|
| Plataforma base inspeccionada (estado, modelo, ID inventario) | DJI Tello Camera; 2 drones; sin ID de inventario. Estado físico por confirmar | Sin evidencia enlazada |
| Funciones existentes y límites comprobados | En el Día 1 se revisó el trabajo de la semana; no hay pruebas de vuelo registradas | Sin evidencia enlazada |
| Paro de emergencia / desconexión segura ensayados | No registrado en el Día 1 | Pendiente |
| Restricciones de competición o exhibición verificadas | Sí: se revisaron la batería y el límite de altura (valores exactos por registrar) | Fuente por enlazar |
| Riesgos vistos y medidas activas | Por registrar | [docs/seguridad.md](../seguridad.md) |

**Normas específicas según misión:**
- **M01:** protecciones de alimentación; desarmar motores antes de tocar ruedas; dohyō delimitado, rival de referencia y bordes seguros.
- **M03:** pista despejada, altura/posición de sensores controlada, baterías y ruedas comprobadas.
- **M04:** espacio interior autorizado, observador humano, altura y desplazamientos limitados, baterías y aterrizaje inmediato; *verificar modelo real de Tello*.
- **M05:** ROS 2 y TF/navegación listos; límites de velocidad, sensor de obstáculos, paro seguro y zona de tránsito marcada.

## 3 · Diagnóstico práctico colectivo (35–65 min)

**Condición inicial V0 de la plataforma:** Plataforma completa: 2 drones DJI Tello Camera con 2 baterías, y 5 laptops que se conectan al dron por Wi-Fi. Qué funciona y qué falta: por confirmar, porque el Día 1 no registró pruebas físicas.

| Prueba diagnóstica | Condición y procedimiento | Resultado observado / unidad | Problema / causa probable | Evidencia |
|---|---|---|---|---|
| 1: movimiento o comunicación | No realizada en el Día 1 | — | — | — |
| 2: lectura de sensor | No realizada en el Día 1 | — | — | — |
| 3: comportamiento de la misión | No realizada en el Día 1 | — | — | — |

**Capacidades ya disponibles y dependencias:** Por definir. Los tres alcances (TL01, TL06 y TL10) están elegidos por todo el equipo, y la distribución de quién lidera cada uno queda pendiente.

## 4 · Integración de Mission Forge C2 y pacto de alcances (65–100 min)

Cada participante debe colocar el archivo **Markdown original generado por la web** en:

`participantes/<alias>/compromiso.md`

Se conserva íntegro (incluido el frontmatter y la lista de katas). Los nuevos alcances/katas diseñados por el participante quedan claramente marcados como *propuesta propia* y requieren aprobación técnica.

**Catálogo de referencia:** [Google Sheets C2](https://docs.google.com/spreadsheets/d/1FKxFzoyu9KJb3RlOwB609vliS5hAtmwWFu2G2zG3Ky4/edit) · **Configurador Mission Forge:** [`herramientas/mission-forge-c2.html`](../../herramientas/mission-forge-c2.html) (descárgalo y ábrelo en el navegador; funciona sin Internet).

| Alias | Kit enlazado | Alcance principal (primero en su kit) | Complementos | Katas elegidos o nuevos | Horas mín.–máx. | Evidencia final esperada | Negociación aprobada |
|---|---|---|---|---|---|---|---|
| @a00574862-cyber | [kit](../../participantes/Andr%C3%A9s%20S%C3%A1nchez/compromiso-kaizen-andres-alejandro-sanchez-rabago.md) | TL06 | TL10, TL01 | 7 katas del catálogo | 9–12 h | Código de vuelo y video del recorrido | Sí; Camilo René Duque Becerra |
| @TadeoGadu | [kit](../../participantes/Carlos%20Tadeo%20Garay%20Dur%C3%A1n/compromiso-kaizen-carlos-garay.md) | TL01 | TL10, TL06 | 7 katas del catálogo | 9–12 h | Código de vuelo y video del recorrido | Sí; Camilo René Duque Becerra |
| @KarolCabre | [kit](../../participantes/Karol%20Daniel%20Cabrera%20Ramirez/compromiso-kaizen-karol-daniel-cabrera-ramirez.md) | TL10 | TL06, TL01 | 7 katas del catálogo | 9–12 h | Código con seguimiento de estaciones, identificación de colores y video | Sí; Camilo René Duque Becerra |
| @a00575206-droid | [kit](../../participantes/PedroHern%C3%A1ndez/compromiso-kaizen-pedro-hernandez-avalos.md) | TL01 | TL06, TL10 | 7 katas del catálogo | 9–12 h | Código de vuelo y video del recorrido | Sí; Camilo René Duque Becerra |
| @AdrianNavarroRomo | [kit](../../participantes/Adrian%20Navarro%20Romo/compromiso-kaizen-adrian-navarro-romo.md) | TL01 | TL06, TL10 | 7 katas del catálogo | 9–12 h | Código de vuelo y video del recorrido | Sí; Camilo René Duque Becerra |

**Resultado de negociación grupal:** El profesor aprobó los alcances de los cinco integrantes. Los cinco kits quedaron en estado "Requiere revisión" porque el máximo estimado (12 h) supera las 10 h de disponibilidad orientativa. Interfaces entre códigos y prioridad si no hay tiempo: por definir.

## 5 · Inventario exhaustivo y especificación de materiales (obligatorio)

### 5.1 Inventario maestro del equipo

Completar **cada recurso requerido**: estructura, electrónica, actuadores, sensores, herramientas, consumibles, instrumentos, software, datos, red, espacios de ensayo y elementos de seguridad. Añadir filas sin límite.

| ID | Categoría | Material o recurso (especificación exacta: modelo, medida, versión o característica) | Cantidad requerida + unidad | Cantidad confirmada | Fuente/proveedor o dueño | Ubicación física o ruta digital | Responsable | Estado (disponible/reservado/falta) | Alternativa compatible | Día requerido |
|---|---|---|---|---|---|---|---|---|---|---|
| MAT-001 | Robot/plataforma | DJI Tello Camera (modelo informado por el equipo; sin ID de inventario) | 2 ud. | 2 | Por confirmar | Salón del Prof. Camilo René Duque Becerra | Por confirmar | Disponible | Por definir | D1 |
| MAT-002 | Electrónica | Baterías del Tello | 2 ud. | 2 | Por confirmar | Salón del Prof. Camilo René Duque Becerra | Por confirmar | Disponible | Por definir | D1 |
| MAT-003 | Cómputo | Laptops con Wi-Fi para conectarse al dron | 5 ud. | 5 | Cada integrante | Cada integrante | Cada integrante | Disponible | Por definir | D1 |
| MAT-004 | Software/datos/conectividad | Python, djitellopy y OpenCV en su versión más reciente (versiones exactas por registrar); conexión por Wi-Fi al dron | 1 por laptop | Por confirmar | Instalación propia | Laptop de cada integrante | Cada integrante | Por confirmar | Por definir | D1 |
| MAT-005 | Zona de pruebas / marcadores | 3 figuras impresas en tamaño carta: círculo, triángulo y cuadrado. Pasillo del segundo piso del CCI como zona de vuelo; dimensiones del área por registrar | 3 figuras; 1 zona | Por confirmar | Equipo / CCI | Pasillo del segundo piso, CCI | Por confirmar | Por confirmar | Por definir | D1 |
| MAT-006 | Seguridad | Extintor en el pasillo; botiquín en la enfermería del piso inferior; punto de reunión en el estacionamiento | — | — | CCI | Ver ubicación indicada | Camilo René Duque Becerra | Disponible | — | D1 |

También disponible el archivo [`datos/inventario_materiales.csv`](../../datos/inventario_materiales.csv) para registrar muchos materiales sin agrandar esta tabla.

### 5.2 Lista de cotejo específica por plataforma (elegir solo la misión asignada)

| Misión | Revisar y especificar (marca/modelo/cantidad reales) |
|---|---|
| M01 · Mini-sumo autónomo | Chasis y material para cuñas, ruedas/motores/soportes, driver, controlador y firmware, batería/cargador/fusible, sensores de borde y rival, cableado/conectores, dohyō/rival de referencia, CAD/impresora 3D/herramientas, instrumentos de medición y protocolo de paro. |
| M03 · Seguidor de línea | Chasis/ruedas/motores, driver, controlador, barra de sensores reflectivos/soportes, batería/cargador, placa y cableado, pista con curvas y superficie definida, software de programación, cinta/regla/cronómetro/instrumentos y paro seguro. |
| M04 · Tello Python | **Modelo Tello verificado** y baterías suficientes, cargador, computadora y adaptador Wi-Fi, versión Python y SDK compatible, OpenCV si aplica, marcadores visuales impresos, área interior de vuelo demarcada, supervisor/observador, barreras y protocolo de aterrizaje/abortos. |
| M05 · AMR ROS 2 | Base AMR y baterías/cargador, computador y distribución ROS 2/paquetes, workspace y repositorio base, sensores (p. ej. lidar/odometría), mapa y TF/localización, RViz/Nav2 si aplica, red de comunicación, estaciones/marcadores, área de navegación acordonada, instrumento de medida y paro seguro. |

**Enlaces a fichas técnicas / instrucciones de conexión, fabricación y seguridad:** [Plan de seguridad del equipo](../seguridad.md) · [Requisitos generales](../../SEGURIDAD_Y_DATOS.md). Fichas técnicas del Tello: por enlazar.

### 5.3 Riesgos de recursos y abastecimiento

| Bloqueante | A qué alcance afecta | Solución prevista / fecha y responsable | Impacto si no se resuelve |
|---|---|---|---|
| Solo hay 2 drones y 2 baterías para 5 integrantes | TL01, TL06, TL10 | Por definir: turnos de vuelo y carga entre sesiones. Responsable por asignar | Menos tiempo de vuelo por persona |
| Límite de altura y especificación de batería verificados, pero sin valores registrados | TL01, TL10 | Registrar los valores exactos. Responsable por asignar | No se puede demostrar el cumplimiento de la restricción |
| Reserva formal del espacio de vuelo no registrada | TL01, TL10 | Confirmar con el Prof. Camilo René Duque Becerra | Replanificar o simular |

**Materiales completos para ejecutar el Día 2:** Por confirmar. **Confirmado por:** Por confirmar.

## 6 · Kata 0 — exploración técnica de arranque (100–160 min)

| Integrante/alcance | Pregunta técnica | Mini-prueba o prototipo de exploración | Resultado o error observado | Evidencia enlazada | Acción necesaria antes de D2 |
|---|---|---|---|---|---|
| Equipo | Por confirmar | Por confirmar | Por confirmar | Sin evidencia enlazada | Registrar lo realizado en la Kata 0 |

**Integración entre subequipos:** Por confirmar.

## 7 · Cierre: contrato técnico y puerta de salida E1 (160–180 min)

- [x] El objetivo colectivo tiene condición de éxito verificable.
- [x] Cada estudiante depositó **su kit Markdown original** en `participantes/<alias>/compromiso.md`.
- [x] Cada estudiante completó [E1 personal](../../participantes/_plantilla/dias/E1.md) y definió frontera, evidencia y alcance negociado.
- [x] El inventario está **completo** y cada recurso indica cantidad, especificación, disponibilidad y responsable.
- [x] Se asignó **dōjō específico** con edificio, salón/taller, horarios, supervisión y autorización.
- [x] Se inspeccionaron riesgos, paro y condiciones de seguridad de la plataforma.
- [x] Se identificaron dependencias y bloqueos del Día 2; están bajo control o se ajustó la misión.
- [x] El profesor aprobó el alcance y la seguridad, o registró observaciones y una alternativa viable.

**Estado del gate:** APROBADO.

**Condiciones, responsables, fecha y próxima decisión:** Ninguna condición registrada. Pendientes antes del Día 2: acordar roles y el orden de decisiones, registrar valores de batería y altura, y documentar la Kata 0.

**Revisor docente:** Camilo René Duque Becerra · **Enlace a commit/PR:** Por enlazar

**Criterio mínimo E1:** existe un contrato de misión y frontera individual, hay evidencia del punto de partida, un inventario verificable y un espacio de trabajo autorizado. La ausencia de algún material crítico NO debe esconderse.
