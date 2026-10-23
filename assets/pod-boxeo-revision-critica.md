# Revisión crítica de arquitectura, escalabilidad y viabilidad
**Complemento al diseño técnico del pod de boxeo y artes marciales** · Fecha de consulta de fuentes: 1 de octubre de 2026

> **Etiquetas:** **[Confirmado]** = verificado en una fuente consultada hoy (ver "Fuentes" al final). **[Estimado]** = cálculo o rango propio, sin verificar. **[Hipótesis]** = supuesto por validar. **[Pendiente]** = no se pudo verificar; se indica cómo hacerlo.
>
> **Sobre el PDS:** no tengo el PDS en esta conversación. Usé como fuente los requerimientos del primer prompt y el documento técnico previo. Si el PDS dice algo distinto (por ejemplo prioridades o cifras), avísame y ajusto este documento.
>
> **Tipo de cambio supuesto:** 18.5 MXN/USD **[Pendiente: verificar el día de compra]**. Todos los precios en MXN son derivados de ese supuesto o estimados.

---

## Decisiones vigentes (actualización posterior a la revisión)

Estas decisiones **prevalecen** sobre cualquier texto anterior, de este documento o del diseño técnico inicial, que las contradiga.

| Tema | Decisión | Motivo |
|---|---|---|
| Comunicación | Un solo pod (gateway) se conecta por BLE al teléfono; los demás se comunican con él por ESP-NOW. Cualquier pod puede asumir el rol; la app elige el de mayor batería | iOS maneja mal varias conexiones BLE y eso no se puede corregir. La coexistencia BLE + ESP-NOW es firmware propio |
| Plan B de comunicación | BLE entre pods (máximo 3–4 seguidores) | Más robusto ante interferencia y consume menos en los seguidores, pero tiene peor sincronía y es más complejo. Se activa si falla la prueba de la semana 4 |
| Entrega de eventos | Confirmación en la aplicación con la clave (`dev_id`, `boot_id`, `seq`). El seguidor borra el evento tras la confirmación del gateway, y este tras la de la app. Si el gateway falla, la app reconecta con otro pod | ESP-NOW no garantiza entrega de extremo a extremo |
| Carga | USB-C en cada pod (vía base) y apilamiento con pogo magnéticos y contactos rehundidos | El apilamiento es requisito del PDS. El desnivel protege contactos y mano |
| Diseño del apilamiento | Labio perimetral más alto que el aro de contacto; hombro mecánico que soporta la carga; sensor Hall que habilita la salida superior; MCU alimentado por la batería; carga por pod ≈ 500 mA; modo carga que apaga estímulos y duerme el acelerómetro | Tolerancias, energía en contactos expuestos, corriente acumulada y falsos positivos en pods apilados |
| Hito del apilamiento | Prototipo en las semanas 4–5; continuar o descartar al cierre de la semana 5: carga estable ≥ 30 min con 2 pods, contactos < 45 °C, resistencia estable tras 500 ciclos | Criterios propuestos por mí |
| Hito de ESP-NOW | Prueba en la semana 4 con 2–3 pods durante 30 min: pérdida < 1 %, 0 eventos BLE perdidos y consumo medido | Criterios propuestos por mí |
| Regulador | AP2112K-3.3 u otro LDO de baja caída; **no AMS1117** | La caída de ~1.1 V del AMS1117 no permite 3.3 V con una celda de 1S |
| Cargador | TP4056 USB-C **con protección** (DW01 + 8205). No hay gestión de energía: el pod no se usa mientras carga (LEDs y estímulos apagados) | La terminación de carga se confunde con la carga conectada |
| Acelerómetro | Módulo ADXL375 ($344) para el prototipo y las primeras 5 unidades, verificando autenticidad (≈ 20.5 LSB/g en reposo); CI en PCB propia para una segunda tirada | Reduce el riesgo de soldadura LGA y de calendario |
| Batería | Celda protegida con pestañas y cables; medir la capacidad real con una descarga | El portacelda de resorte puede perder contacto con los golpes. La capacidad anunciada no está verificada |
| App | React Native | Capacidades del equipo |
| HarmonyOS | Fuera de las 8 semanas | HarmonyOS NEXT no ejecuta APK de Android de forma nativa **[Confirmado]** |

---

## 0. Qué cambia respecto al documento anterior

Esta revisión corrige decisiones de mi propuesta previa. Las más importantes:

| # | Decisión previa | Cambio | Por qué |
|---|---|---|---|
| 1 | App en **Flutter** | **React Native** | Dart no está entre las capacidades del equipo (sí lo están React y React Native). Fue una decisión mía sin considerar el equipo. |
| 2 | **ESP-NOW** entre pods con "pod maestro" | **Se mantiene: un pod hace de gateway BLE y los demás se comunican con él por ESP-NOW.** El rol es intercambiable; plan B: BLE entre pods | iOS maneja mal varias conexiones BLE y eso no se puede corregir. La coexistencia BLE + ESP-NOW es firmware propio y se mide en la semana 4. El "maestro" fijo se sustituye por un rol que cualquier pod puede asumir. |
| 3 | Módulo **ADXL375** por pod | **Módulo ($344, Amazon MX, verificar autenticidad) para el prototipo y las primeras 5 unidades; CI en PCB propia para una segunda tirada** | Con el precio cotizado por el equipo, diez módulos suman ≈ $3,440 MXN (sin confirmar descuento ni stock para 10). El módulo evita soldar un LGA en la primera tirada. |
| 4 | Portacelda para la 18650 | Celda **con pestañas y cables**, o LiPo con soporte | Un portacelda de resorte puede perder contacto con los golpes. |
| 5 | Carga por apilamiento como función "importante" | **Se mantiene** con pogo magnéticos y contactos rehundidos; USB-C en cada pod como vía base; decisión de continuar o descartar al cierre de la semana 5 | Responde al PDS. El desnivel protege los contactos del golpe y de la mano. Sigue siendo el subsistema con más riesgo. |
| 6 | HarmonyOS "deseable" | **Fuera del alcance de las 8 semanas** | HarmonyOS NEXT no ejecuta APK de Android de forma nativa **[Confirmado]**. |
| 7 | Presupuesto de $1,500 MXN | Se separa: **$1,500 = prototipo (1 unidad)**; el lote de 10 requiere **≈ $10,000–13,000 MXN** **[Estimado]** | Los $1,500 no alcanzan para 10 unidades. |

---

# PASO 1 — Auditoría de la arquitectura preliminar

| Decisión actual | Justificación existente | Problema detectado | Consecuencia | Alternativa propuesta |
|---|---|---|---|---|
| ESP32-WROOM-32E como MCU | BLE + Wi-Fi, ecosistema, el equipo lo domina | Bien justificada. Riesgo: coexistencia BLE + ESP-NOW y consumo con el radio activo, sin medir | Autonomía y latencia podrían quedar por debajo de lo esperado | Mantenerlo. Medir consumo y estabilidad BLE en la **semana 2**, antes de congelar la PCB |
| Acelerómetro ±200 g (ADXL375) | Los acelerómetros de ±16 g se saturan en golpes | Justificado técnicamente, **no económicamente en módulo**. Un solo proveedor (Analog Devices) y es el componente más caro | Riesgo de importación y de presupuesto. Con 10 unidades el módulo no cabe | CI en PCB propia (≈ USD 6–7 por pieza en LCSC **[Confirmado]**, existencias pendientes). Plan B: otro acelerómetro de alta g **[Pendiente]** |
| Piezo como segundo canal | Detecta toques ligeros y da inicio rápido | Parcialmente justificado: añade diseño analógico y ajuste de umbral | Más tiempo de integración y de calibración | Probarlo en la semana 2. **Si el ADXL375 detecta toques ligeros de forma fiable, se elimina** |
| Índice de fuerza a partir de aceleración | Única vía barata | Correlación con fuerza dependiente del montaje y del material; el 90 % no aplica | Se puede prometer más de lo que se mide | Reportar un **índice relativo** (g e impulso). La fuerza en newtons queda como estimación calibrada y diferida |
| Flutter | Una sola base para Android/iOS | **Sin justificación para este equipo** | Curva de aprendizaje de Dart en 8 semanas | React Native (ver Paso 4) |
| ESP-NOW + gateway BLE de un solo pod | Evita las conexiones BLE múltiples en iOS, que el equipo no puede corregir | Un solo radio compartido entre BLE y ESP-NOW en el gateway; mayor consumo en el gateway; sin entrega garantizada de extremo a extremo | Latencia, pérdidas y autonomía podrían salir peor de lo esperado | **Se mantiene.** Rol intercambiable, confirmación de eventos en la aplicación, prueba en la semana 4 y plan B con BLE entre pods (3–4 seguidores) |
| Carga por apilamiento con pogo magnéticos y contactos rehundidos | Diferenciador del producto y requisito del PDS | Contactos en la cara de golpeo, corriente acumulada, tolerancias (la compresión del pad puede superar el desnivel) y energía en contactos expuestos | Cortos, desgaste, retrasos | **Se mantiene como hito con decisión al cierre de la semana 5.** Hombro mecánico que soporta la carga, sensor Hall que habilita la salida, MCU alimentado por la batería y USB-C en cada pod como vía base |
| 18650 con portacelda | Robusta ante golpes | El resorte del portacelda puede perder contacto con los impactos. Riesgo de celdas falsificadas | Reinicios inesperados, seguridad | Celda protegida **con pestañas y cables** de proveedor confiable, o LiPo en soporte rígido |
| Aro WS2812B | Un solo pin, fácil | Los LED de este tipo pueden fallar si la temporización depende del CPU y el BLE interrumpe | Parpadeos y errores visuales | Controlarlo con **RMT/I2S** (periférico de hardware) |
| PCB propia desde la semana 4 | Integración y robustez | Depende del equipo de laboratorio; para 10 unidades el fresado/ataque químico no escala | Retrasos y repetibilidad baja | Para el lote: PCB fabricada por un servicio externo (JLCPCB u otro). Para el prototipo: módulos |
| Carcasa impresa en PETG + TPU | Se fabrica en casa | **Tiempo de impresión para 10 unidades** (cuerpo, tapa, difusor, base) | Cuello de botella, variación entre piezas | Medir el tiempo real de una pieza en la semana 2. Si excede ≈ 8 h por pod **[Estimado]**, repartir impresoras o simplificar |
| Supabase + SQLite + LLM | Postgres, auth, bajo costo | Bien justificada. Riesgos: pausa del plan gratuito, clave de API del LLM y privacidad | Servicio no disponible durante el piloto | Ver Paso 4: plan de pago durante el piloto y respaldo con plantillas por reglas |
| HarmonyOS | Mercado objetivo | HarmonyOS NEXT no corre APK de Android de forma nativa **[Confirmado]** | App Android actual no instalable en esos equipos | Posponer; evaluar una app nativa o una PWA solo para consulta de resultados |
| Presupuesto de $1,500 MXN | Restricción del proyecto | Solo aplica a 1 unidad | Falta de fondos para el lote | Pedir presupuesto aparte para 10 unidades |

**Puntos únicos de falla identificados:** (1) el ADXL375 (proveedor único, importación); (2) la batería (seguridad, calidad); (3) el rol de gateway BLE (mitigado: cualquier pod puede asumirlo y la app reconecta con otro); (4) la cuenta de Supabase (pausa por inactividad); (5) el backend para la generación de recomendaciones (mitigado con un modo sin conexión).

**Qué cabe en 8 semanas:** un pod con LEDs, impacto, tiempo de reacción, BLE, app con historial y gráficas, análisis con reglas y recomendaciones con LLM, y 5 unidades si la PCB se ordena a más tardar en la semana 4 (ver Paso 6). Como entregables paralelos con decisión de continuar o descartar: ESP-NOW con 2 pods (semana 4) y prototipo de apilamiento (semana 5). **Para la v2:** HarmonyOS, fuerza en newtons, leaderboard en línea, ML propio.

**Conflictos entre requerimientos:** (a) 10 unidades vs. $1,500 MXN; (b) apilamiento y superficie de golpeo en la misma cara; (c) 3 h de autonomía vs. LEDs al brillo máximo; (d) 90 % de precisión "global"; (e) 5–10 unidades vs. 8 semanas con PCB propia.

---

# PASO 2 — Validación de la arquitectura de IA

**Estrategia recomendada: híbrida y mínima.** El microcontrolador mide, el teléfono calcula, la nube solo redacta recomendaciones a partir de métricas ya agregadas.

| Función | ¿Requiere IA? | Procesamiento | Input | Output | Latencia objetivo | Alternativa sin IA |
|---|---|---|---|---|---|---|
| Detección del impacto | **No** (umbral + reglas) | MCU | Aceleración (±200 g) y señal del piezo | Evento válido/no válido y marca `t1` | ≤ 2 ms hasta la marca [Hipótesis] | Es la solución base. ML (TFLite Micro) solo si hay muchos falsos positivos |
| Cálculo de pico, impulso, duración y tiempo de reacción | **No** (determinista) | MCU | Ventana de muestras y marcas `t0`/`t1` | Valores por evento | ≤ 5 ms tras el impacto [Hipótesis] | Cálculo directo |
| Índice de fuerza | **No** (función de calibración) | Teléfono (o MCU) | Pico, impulso, modo de montaje | Índice relativo | < 100 ms | Regresión lineal calibrada |
| Identificación de errores y patrones (fatiga, asimetría) | **Parcial** | Teléfono | Métricas de la sesión | Banderas y valores | < 1 s tras terminar | Umbrales y percentiles personales |
| Comparación histórica | **No** | Teléfono (SQLite) y nube | Sesiones previas | Diferencias, gráficas | < 1 s | Consultas SQL |
| Recomendaciones personalizadas | **Sí, acotada** (LLM) | Nube (función de borde) | JSON de métricas agregadas, sin datos personales | Texto estructurado | ≤ 5–10 s, asíncrona [Hipótesis] | Plantillas de texto activadas por reglas (modo sin conexión) |
| Predicción de tendencias | **No justificada en el MVP** | — | — | — | — | Regresión lineal o media móvil. Con pocas sesiones por usuario un modelo no aporta valor |

**Reparto de procesamiento:**
- **MCU:** marcas de tiempo, detección, métricas por evento, rutina autónoma y almacenamiento temporal.
- **Teléfono:** persistencia, gráficas, comparaciones, índice de fuerza, reglas y recomendaciones de respaldo.
- **Nube:** autenticación, respaldo, sincronización y llamadas al LLM.

**Tiempo de reacción:** `RT = t1 − t0`, ambos con `esp_timer_get_time()` en el mismo pod. Ni BLE ni Internet intervienen.

**IA generativa sin datos innecesarios:** la función de borde recibe solo estadísticos (medias, desviaciones, tendencias, número de eventos) y un identificador seudónimo. No recibe nombre, correo, ubicación ni series completas. La clave de la API vive en el servidor, nunca en la app. Si el servicio falla, la app muestra el texto de respaldo generado por reglas.

**Validación (cuatro niveles distintos, ningún porcentaje general):**

| Nivel | Métrica | Conjunto de validación | Procedimiento |
|---|---|---|---|
| Medición de sensores | Error de RT vs. referencia; error de aceleración; CV del índice | ≥ 200 pruebas de RT en banco y 10 series de 30 impactos por montaje | Analizador lógico o cámara de alta velocidad; péndulo/caída de masa conocida |
| Exactitud de clasificación | Precisión, sensibilidad y F1 del detector de impacto | ≥ 300 eventos etiquetados con video (golpes, toques, vibración, caídas), separados por usuario | Matriz de confusión; división entrenamiento/prueba por usuario |
| Consistencia de recomendaciones | (a) 100 % de cifras del texto presentes en el JSON; (b) misma entrada → mismas banderas; (c) acuerdo entre revisores | 50 sesiones (reales y sintéticas) | Verificador automático; rúbrica de 2–3 entrenadores; kappa de acuerdo |
| Utilidad percibida | Escala Likert, comprensión y uso posterior | Piloto con usuarios reales | Cuestionario y observación (Paso 8) |

Ningún modelo recibe un porcentaje de "precisión" mientras no se defina el conjunto de datos y el procedimiento anteriores.

---

# PASO 3 — Arquitectura de datos y operación sin conexión

## 3.1 Flujo y formatos

`Pod → (BLE GATT) → App (SQLite) → (HTTPS) → Supabase (Postgres) → función de borde → LLM`

**Evento de impacto en el pod (binario, little-endian, ≈ 40 bytes):**

| Campo | Tipo | Nota |
|---|---|---|
| `ver` | u8 | Versión del formato |
| `dev_id` | 6 bytes | MAC del ESP32 (identificador de fábrica) |
| `boot_id` | u32 | Aleatorio en cada arranque |
| `seq` | u32 | Contador de eventos desde el arranque |
| `sess` | u16 | Identificador corto de sesión asignado por la app |
| `stim` | u16 | Número de estímulo en la rutina |
| `rt_us` | u32 | Tiempo de reacción en µs |
| `peak_dg` | u16 | Pico de aceleración (0.1 g) |
| `impulse` | u32 | Integral de aceleración (unidad definida en firmware) |
| `dur_us` | u16 | Duración del impacto |
| `flags` | u8 | Válido, saturado, doble golpe, sin estímulo |
| `batt` | u8 | Porcentaje |
| `crc` | u16 | Detección de errores |

**Clave de deduplicación:** (`dev_id`, `boot_id`, `seq`). Es única por evento y sobrevive reinicios del pod.

**Identificadores:**
- *Dispositivo:* MAC del ESP32 más un nombre amigable en la app.
- *Usuario:* UUID de Supabase Auth. Nunca se envía al pod.
- *Sesión:* UUID v4 creado por la app. El pod recibe un identificador corto (`sess`) y la app lo mapea.

**Frecuencia de envío:** una notificación BLE por evento (a lo sumo unos pocos por segundo en entrenamiento) y una de estado cada ≈ 30 s. **Marcas de tiempo:** el pod usa reloj relativo; la app asigna la hora real al recibir y calcula el desfase con un mensaje de sincronización al inicio.

## 3.2 GATT propuesto
- **Control** (escritura): iniciar/detener sesión, cargar rutina, sincronizar hora, solicitar reenvío desde `seq = N`.
- **Eventos** (notificación): paquetes de arriba; la app responde con **ACK** del último `seq` recibido.
- **Estado** (lectura/notificación): batería, versión de firmware, eventos pendientes, causa del último reinicio.

## 3.3 Alternativas evaluadas

| Tecnología | Papel | Decisión y motivo |
|---|---|---|
| **BLE GATT** | Pod ↔ teléfono | **Sí.** Nativo en ambos sistemas, bajo consumo, suficiente para eventos pequeños |
| ESP-NOW | Pod ↔ pod | **Sí (base).** Un pod hace de gateway BLE hacia el teléfono y los demás se comunican con él por ESP-NOW, con confirmación de eventos a nivel de aplicación |
| BLE entre pods | Pod ↔ pod (plan B) | **Respaldo.** Más robusto ante interferencia (salto de canal) y menor consumo en los seguidores, pero peor sincronía y más complejo (cada pod central y periférico). Máximo de 3–4 seguidores **[Pendiente: confirmar]**. Se activa si falla la prueba de la semana 4 |
| **HTTPS** | App ↔ Supabase | **Sí.** Simple, soportado por todo, con reintentos |
| MQTT | Dispositivo ↔ nube | **No.** Los pods no tienen salida a Internet propia y exigiría un broker |
| WebSocket | Tiempo real en la nube | **No en el MVP.** BLE ya entrega eventos en vivo. Más adelante, Supabase Realtime para un leaderboard en vivo |
| **Almacenamiento local (SQLite)** | App y pod | **Sí.** Base de la operación sin conexión |

## 3.4 Seguridad básica
- **BLE:** emparejamiento con cifrado (LE Secure Connections) y clave impresa en la etiqueta del pod **[Pendiente: verificar soporte en la librería BLE elegida]**. "Just Works" no protege contra interceptación activa.
- **ESP-NOW:** claves PMK/LMK; el número de pares cifrados es limitado **[Pendiente: verificar en la documentación de Espressif]**.
- **Nube:** HTTPS/TLS, Row Level Security por usuario en Postgres, JWT de Supabase, clave del LLM solo en el servidor.
- **Firmware:** actualizaciones firmadas y arranque seguro quedan fuera del piloto. Se documenta como riesgo conocido.

## 3.5 Qué ocurre ante cada falla

| Falla | Comportamiento esperado | Qué se conserva |
|---|---|---|
| **1. El teléfono pierde la conexión con el pod** | El pod continúa la rutina cargada (autónomo) y guarda los eventos con `seq` | Eventos en flash del pod hasta recibir ACK. Al reconectar, la app pide reenvío desde su último `seq` |
| **2. El usuario pierde Internet** | La app funciona completa: sesiones, gráficas y comparaciones locales; recomendaciones con plantillas | Todo en SQLite. La cola de sincronización (outbox) espera la conexión |
| **3. El backend no responde** | Igual que el punto 2. La app reintenta con espera creciente | Sesiones locales; los envíos son idempotentes gracias a la clave de deduplicación |
| **4. La app se cierra durante el entrenamiento** | El pod sigue y acumula eventos. Al reabrir, la app detecta la sesión pendiente y reconstruye desde el pod | Eventos en el pod (≈ 2,000 eventos ≈ 80 KB **[Estimado]**) |
| **5. El pod se reinicia inesperadamente** | Nuevo `boot_id`; el pod marca la causa del reinicio; la sesión se divide en segmentos | Eventos previos ya enviados y con ACK. Los no confirmados se pierden si no se guardaron en flash (el registro en flash se escribe por lotes para limitar el desgaste) |

**Política de sincronización:** eventos inmutables y solo se agregan; inserción con `ON CONFLICT DO NOTHING` por la clave de deduplicación; las sesiones sincronizan por lotes cuando hay red y energía; en conflictos de metadatos (nombre de rutina, notas) gana la última edición. **En el teléfono se conserva** todo el historial hasta que el usuario lo borre. **En el pod** solo se conservan eventos no confirmados. Las ondas crudas se guardan únicamente en modo de diagnóstico.

---

# PASO 4 — Arquitectura completa de software

## 4.1 Hardware y firmware

| Función | Decisión |
|---|---|
| Entorno | PlatformIO con Arduino-ESP32 o ESP-IDF; C/C++ (el equipo lo domina) |
| Lectura de sensores | ADXL375 por **SPI**, FIFO e interrupción de umbral; piezo con comparador si se conserva |
| Temporización | `esp_timer_get_time()` en µs; interrupción en IRAM que solo guarda `t1` |
| Tareas | Núcleo 1: sensado y eventos. Núcleo 0: BLE y comunicación **[Hipótesis: validar en banco]** |
| Control de LEDs | **RMT/I2S**, no bit-banging, para que el BLE no altere la señal |
| Energía | Brillo máximo limitado (≈ 40 %), modem-sleep, suspensión tras inactividad y despertar por interrupción del acelerómetro **[Verificar viabilidad en banco]** |
| Comunicación | BLE GATT al teléfono desde un solo pod (gateway); ESP-NOW entre pods; el gateway es intercambiable |
| Almacenamiento temporal | Registro circular en LittleFS/NVS por lotes |
| Diagnóstico | Causa de reinicio, contador de reinicios, voltaje de batería, autodiagnóstico del acelerómetro en el arranque, versión de firmware |

## 4.2 Aplicación: React Native vs. PWA

| Criterio | React Native | PWA |
|---|---|---|
| Android 8+ / iOS 14+ | Sí (según versión del framework y plugins) **[Pendiente: verificar mínimos]** | Depende del navegador |
| Bluetooth | Plugins nativos de BLE maduros | **Web Bluetooth no está disponible en iOS Safari** **[Pendiente: confirmar en caniuse.com]** |
| Segundo plano | Servicios en primer plano en Android; iOS limitado | Muy limitado |
| Almacenamiento local | SQLite nativo | IndexedDB (menos confiable) |
| Notificaciones | Soportadas | Limitadas en iOS **[Pendiente]** |
| Complejidad | Compilaciones nativas (cuenta de Apple para iOS) **[Pendiente: costo vigente]** | Más simple, pero sin BLE en iOS |
| HarmonyOS | **No hay soporte oficial.** HarmonyOS NEXT no ejecuta APK de Android de forma nativa **[Confirmado]**. Existen proyectos comunitarios **[Pendiente]** | El navegador podría servir para consulta, sin garantía de BLE **[Pendiente]** |

**Decisión: React Native** (con *development build*, no con Expo Go, por el BLE) y una librería de BLE mantenida **[Pendiente: confirmar la versión compatible]**. El piloto en Android puede distribuirse por APK directo; en iOS, por TestFlight. **Justificación:** el equipo ya domina React, el BLE es indispensable y la PWA no lo ofrece en iOS. HarmonyOS queda fuera del MVP.

## 4.3 Backend

| Opción | Ventajas | Desventajas | Veredicto |
|---|---|---|---|
| **Supabase** | Auth, Postgres, RLS, almacenamiento y funciones de borde en un solo servicio | Plan gratuito: 2 proyectos, 500 MB de base de datos y **pausa tras 1 semana sin actividad** **[Confirmado]**. Pro cuesta USD 25/mes más uso **[Confirmado]** | **Elegido** |
| Firebase | Auth y sincronización ágiles | Modelo NoSQL; consultas de series temporales menos naturales; dependencia de Google | Alternativa |
| Python propio (FastAPI + VPS) | Control total | Mantener servidor, parches, TLS y respaldos; innecesario para 10 unidades | Descartado |

**Uso para el piloto:** autenticación por correo, tablas `devices`, `sessions`, `impacts` (con clave única de deduplicación), una función de borde para el LLM y almacenamiento para los archivos de firmware si se usa OTA. Para evitar la pausa durante el piloto, contratar el plan Pro el mes de pruebas (≈ USD 25, ≈ $460 MXN **[Estimado]**).

## 4.4 Página de venta (separada de la app)
- **Solución:** sitio estático con React (Vite o similar) en un servicio gratuito de alojamiento estático, más un formulario de contacto y un enlace directo de WhatsApp (canal habitual en México) **[Hipótesis]**.
- **Contenido:** propuesta de valor, demostración en video, funciones, especificaciones honestas (marcando lo que está en validación), preventa o lista de espera y aviso de privacidad.
- **Costos:** dominio ≈ $200–400 MXN al año **[Estimado; verificar]**. Alojamiento: nivel gratuito **[Pendiente: verificar condiciones de uso comercial]**.
- **Sin pagos en línea en el piloto.** Si se requiere cobro, usar un enlace de pago de un procesador local más adelante.
- **Independencia:** no comparte base de datos ni cuentas con la app; solo un enlace a la descarga.

---

# PASO 5 — Flujo de datos y latencia

Caso: el usuario inicia una rutina, recibe un estímulo, golpea y consulta sus resultados. **Todas las latencias son estimaciones o metas de diseño, no mediciones.**

| Etapa | Componente | Dato | Protocolo | Latencia estimada | Falla posible | Fallback |
|---|---|---|---|---|---|---|
| 1. Inicio de rutina | App → Pod | Rutina y `sess` | BLE (escritura) | 15–100 ms [Estimado; depende del intervalo de conexión] | Pod desconectado | Reintento; el pod ejecuta la última rutina cargada |
| 2. Activación del estímulo | Firmware → LEDs | Patrón | RMT | ≈ 1 ms para 16 LEDs [Estimado] | Error de datos del LED | Reenvío del cuadro |
| 3. Registro temporal `t0` | Firmware | µs | Interno | < 0.1 ms [Hipótesis] | Marca tomada antes de que el LED cambie | Se calibra el desfase fijo con un fotodiodo en banco |
| 4. Detección del impacto `t1` | Acelerómetro → MCU | Interrupción | SPI/GPIO | ≈ 1–3 ms de retardo del sensor y el elastómero [Hipótesis: medir] | Falso positivo por vibración | Reglas de duración y de ventana post-estímulo |
| 5. Procesamiento de la señal | MCU | Ventana de muestras | SPI | < 5 ms [Hipótesis] | Saturación del sensor | Bandera `saturado` |
| 6. Cálculo de métricas | MCU | RT, pico, impulso | Interno | < 2 ms [Estimado] | Evento sin estímulo previo | Bandera `sin_estimulo` |
| 7. Transmisión a la app | Pod → App | Evento de ≈ 40 B | BLE (notificación) | 15–50 ms [Estimado] | Pérdida de paquetes | Reenvío por `seq` |
| 8. Almacenamiento | App | Fila SQLite | Local | < 20 ms [Estimado] | Almacenamiento lleno | Aviso y exportación |
| 9. Sincronización | App → Supabase | Lote de sesión | HTTPS | Segundos, diferida | Sin Internet | Outbox y reintentos |
| 10. Análisis | App y función de borde | Métricas agregadas | HTTPS | < 1 s (reglas); 2–10 s (LLM) [Estimado] | Fallo del LLM | Plantillas por reglas |
| 11. Presentación | App | Gráficas | Local | < 1 s [Meta] | — | Resultados básicos sin recomendación |

**Latencia de medición local (afecta a los datos):** etapas 3 a 6. El tiempo de reacción solo depende de ellas. Un **sesgo fijo** por retardo del sensor y del elastómero se mide en banco y se compensa. **Latencia de visualización y sincronización (no afecta a los datos):** etapas 1, 7 a 11. Un retraso en el inicio del estímulo no es un error de medición, porque `t0` se toma en el pod.

---

# PASO 6 — Escalabilidad de 1 a 10 unidades

## 6.1 Tres componentes críticos

| | **ADXL375 (acelerómetro)** | **ESP32-WROOM-32E-N4 (MCU)** | **Celda Li-ion 18650 protegida** |
|---|---|---|---|
| Disponibilidad en México (≥ 10 u.) | **[Pendiente]** No se verificó stock en tiendas mexicanas. Mouser muestra existencias del ADXL375BCCZ en sus sitios regionales de Ecuador y Honduras, no en el de México **[Confirmado en esas páginas]** | **[Pendiente]** en tiendas locales; el módulo y las DevKit son comunes, pero no se verificó stock | **[Pendiente]** No se consultó |
| Precio unitario / volumen | LCSC: USD 7.44 (1 u.), 6.38 (10 u.), 5.74 (30 u.), 5.20 (100 u.) con **0 unidades en inventario** al consultar **[Confirmado]**. Módulo Adafruit: USD 24.95 (1–9) y 22.46 (10–99) **[Confirmado]** | LCSC: ≈ USD 3.1–3.8 (1 u.) y 2.6–3.3 (10 u.), con miles de unidades en inventario según la página **[Confirmado; varía por página y fecha]** | **[Pendiente]** Rango propio: $100–200 MXN **[Estimado]** |
| Entrega a México | **[Pendiente]** (Mouser, LCSC, Adafruit: verificar con el cálculo de envío) | **[Pendiente]** | Compra local recomendada (restricciones de envío de baterías de litio **[Pendiente: verificar por proveedor]**) |
| Alternativas | Módulo (más caro). Otros acelerómetros de alta g **[Pendiente]** (el ADXL372 podría incumplir el pitch ≥ 0.8 mm **[Pendiente]**) | ESP32-WROOM-32D/32UE u otras variantes del mismo ecosistema | LiPo con protección, de otro proveedor |
| JLCPCB PCBA | La pieza existe en LCSC (C662206). **Su estado en la biblioteca de ensamblaje de JLCPCB: [Pendiente]** | **Parte "Extended" con número C701341** **[Confirmado]** | No aplica (montaje manual) |
| Ensamblaje | LGA-14 de 3×5 mm: requiere horno/aire caliente y pasta. **Pitch del encapsulado: [Pendiente: leer el datasheet]** | SMD castelado, apto para soldadura manual | Soldadura de cables o conector, con cuidado |
| Riesgo de sustitución | **Alto** (proveedor único, sin existencias en LCSC al consultar) | **Bajo** | Medio (calidad y falsificaciones) |

**Cómo verificar:** pedir cotización con 12 unidades (10 + 2 de repuesto) en Mouser México, LCSC, Adafruit y las tiendas locales; guardar capturas con fecha, precio con envío e impuestos y tiempo de entrega.

## 6.2 Estrategia de fabricación para el lote

| Opción | Ventajas | Desventajas | Recomendación |
|---|---|---|---|
| Fabricar todo en el laboratorio | Control y bajo costo en efectivo | Poco repetible para 10 unidades; vías sin metalizar; mucho tiempo | Solo para PCB v1 de 1–2 unidades |
| PCB externa + ensamblaje manual | Calidad de PCB con vías metalizadas; el equipo ya suelda SMD | Plazos de envío **[Pendiente]**; 10 ensamblajes manuales con LGA | **Recomendada para las primeras 5–10 unidades** |
| JLCPCB PCBA | Menos errores de soldadura | Cuotas por partes "Extended" y por montaje **[Pendiente]**; el calendario de 8 semanas es ajustado | Para una segunda tirada |
| Módulos comerciales | Menos riesgo electrónico | El costo del acelerómetro en módulo no cabe (≈ $4,150 MXN por 10) | Solo para la semana 3 |
| PCB propia que integre todo | Menor costo y mayor robustez | Más riesgo en la primera versión | Sí, para el lote, con una **v0 de módulos** como respaldo |

## 6.3 Qué cambia al pasar de 1 a 10 unidades
1. Pasar de módulos a **un solo diseño de PCB** con ESP32, acelerómetro, cargador, LDO y conectores.
2. Definir una **prueba de fin de línea**: autodiagnóstico, medición de corriente en reposo, prueba de LEDs y verificación del acelerómetro con una sacudida estándar.
3. **Calibración por unidad:** el cero y la ganancia del sensor y una verificación contra el mismo péndulo para todas.
4. **Registro por unidad** (hoja de control): lote de la celda, versión de firmware, versión de la PCB, fecha de prueba.
5. **Jigs y plantillas** de impresión y de montaje; tiempo de impresión y de ensamblaje por unidad.
6. **Piezas de repuesto** (20 %) de los componentes críticos.
7. **Firmware idéntico en todas las unidades**, con versión visible en la app.
8. **Calendario realista:** 5 unidades en la semana 8 requieren pedir las PCB a más tardar en la semana 4 y recibirlas en la semana 6 **[Pendiente: verificar plazos de fabricación y envío]**. **Diez unidades probablemente requieran las semanas 9–12.**

---

# PASO 7 — Viabilidad económica y precio de venta

**Supuestos:** lote de 10 con PCB externa y ensamblaje manual; mano de obra propia (no desembolso, pero se valora aparte). Los precios del ESP32, el ADXL375, la 18650, el aro LED, el piezo, el TP4056 y los pogo son los **cotizados por el equipo** para 1 unidad; el precio por volumen y el stock para 10 piezas están **[Pendientes]**. El resto son **[Estimados]**.

| Concepto | Costo unitario MXN | Costo para 10 unidades | Observaciones |
|---|---:|---:|---|
| ESP32-WROOM-32E | 70 | 700 | Cotizado: $281 en Mouser MX (1 u.; verificar volumen, envío e IVA). En LCSC ≈ USD 3.1–3.8 **[Confirmado]** ≈ $57–70 con importación |
| Pasivos, LDO AP2112K-3.3, comparador, protecciones, conectores, programador USB-UART | 60 | 600 | **[Estimado]**. Reemplaza al AMS1117 de la cotización |
| Módulo ADXL375 | 344 | 3,440 | Cotizado por el equipo (Amazon MX, 1 u.); stock y precio para 10 **[Pendiente]**. Verificar autenticidad (≈ 20.5 LSB/g). Alternativa CI en PCB propia: ≈ 120 |
| Piezo 27 mm | 10 | 100 | Cotizado (Unit). Opcional si se elimina el canal |
| Aro de 16 LEDs WS2812B | 29 | 290 | Cotizado (Unit); confirmar que sean 16 LEDs. Con tira de 300 LEDs ($356 para 18 pods): ≈ 19 |
| Celda 18650 protegida con pestañas y cables | 125 | 1,250 | Cotizado (Steren/ML); medir capacidad real |
| TP4056 USB-C con protección | 9 | 90 | Cotizado (Unit); verificar versión con DW01 + 8205 |
| Contactos de apilamiento (pines sueltos + imanes) | 30 | 300 | Estimado del equipo para producción. El prototipo usa un par comercial (≈ 150 por par, cotizado) |
| PCB de 2 capas (lote de 10, prorrateado con envío) | 45 | 450 | **[Pendiente: cotizar]** |
| Carcasa (PETG/ASA) | 75 | 750 | ≈ 150 g por pod |
| Superficie de golpeo (TPU 95A y EVA) | 85 | 850 | |
| Tornillería, imanes, silicona, cableado | 60 | 600 | |
| **Subtotal materiales (BOM)** | **942** | **9,420** | |
| Importación, envíos e impuestos | 50 | 500 | ≈ 15–20 % de lo importado |
| Contingencia (10 % de materiales) | 94 | 940 | Piezas dañadas, errores de soldadura |
| Pruebas y calibración (consumibles) | 20 | 200 | Excluye banco de calibración (gasto único) |
| Empaque (caja, espuma, cable USB-C) | 70 | 700 | |
| **Costo de fabricación en efectivo** | **≈ 1,176** | **≈ 11,760** | **±25 %** |
| Ensamblaje (mano de obra propia) | no es desembolso | — | ≈ 1 h por unidad **[Hipótesis]**; valorarla si hay pago |
| Software y servicios recurrentes | — | ≈ 460 MXN/mes (Supabase Pro) + dominio + LLM | Fijo; **no es costo por unidad**. Supabase Pro: USD 25 **[Confirmado]**; LLM **[Pendiente: estimar por sesión]** |
| Banco de calibración (péndulo, celda de carga, HX711) | — | ≈ 150–350 (único) | Fuera del costo por unidad |

**Precio de referencia (regla BOM ≤ 30 %), sin IVA:**
- Con BOM de materiales (942): 942 / 0.30 ≈ **$3,140 MXN**. Con el CI del acelerómetro en lugar del módulo (BOM ≈ 718): ≈ **$2,390 MXN**.
- Con costo de fabricación completo (1,176): 1,176 / 0.30 ≈ **$3,920 MXN**.
- Con IVA del 16 %, aproximadamente $3,640–$4,550 MXN con el módulo **[Estimado]**.

**Esto es una referencia inicial, no un precio rentable.** No incluye mano de obra, garantía, soporte, comisiones de venta, financiamiento ni costos de software.

**Distinciones:**
- *Costo de fabricación:* ≈ $1,176 MXN por unidad en efectivo en el lote de 10 (con módulo ADXL375).
- *Precio de venta:* decisión comercial que depende del segmento y de lo que paguen los competidores. **El precio de BlazePod u otros pods en México no se verificó [Pendiente]; hay que cotizarlo antes de fijar precio.**
- *Margen bruto:* ejemplo hipotético: precio sin IVA de $3,200 y costo directo con mano de obra y reserva de garantía de ≈ $1,390 deja ≈ 57 % de margen bruto **[Hipótesis]**.
- *Costos recurrentes:* fijos pequeños con 10 usuarios (≈ $46 MXN por usuario al mes en infraestructura, a 10 usuarios **[Estimado]**), por lo que la suscripción **no está justificada por costos**, sino, en su caso, por valor del servicio.
- *Suscripción:* solo si el piloto demuestra que las recomendaciones y el historial aportan valor. Se prueba con preguntas de disposición de pago en el piloto.

**Coherencia con el segmento:** el segmento objetivo no está definido en el prompt. **Asumo gimnasios y estudios de boxeo y funcional y entrenadores personales [Hipótesis: confírmalo].** Un gimnasio compraría varios pods (por ejemplo, 4–6), de modo que el precio por juego sería del orden de **$12,500–$23,500 MXN** al precio de referencia, que puede ser una barrera. No lo fuerzo; alternativas:
1. **Versión "reacción" sin acelerómetro** (solo piezo, LEDs, RT): materiales ≈ $598 y precio de referencia ≈ $1,990 (con costo completo ≈ $800, ≈ $2,660). Es la línea de entrada.
2. **Versión "pro" con aceleración e índice de fuerza** como paquete superior.
3. **Paquetes** (2, 4 o 6 pods) con descuento y cargador compartido.
4. **Funciones premium** (análisis con IA y comparación) como suscripción opcional.
5. **Renta o piloto pagado** a gimnasios para validar disposición de pago antes de invertir en un lote mayor.
6. **Desarrollo gradual:** vender primero lo que está validado (RT) y añadir fuerza cuando haya calibración sólida.

---

# PASO 8 — Validación con usuarios reales

**Alcance:** 5–10 unidades con 8–15 personas **[Hipótesis]**, entre entrenadores y practicantes, durante 3–4 semanas. Todos firman consentimiento informado y aviso de privacidad. **[Pendiente: confirmar con asesor/institución los requisitos de datos personales y de seguridad]**; la ley mexicana de protección de datos fue reformada en 2025 **[Pendiente: verificar la versión vigente]**. El dispositivo no debe describirse como un instrumento médico.

## 8.1 Procedimiento sin asistencia
1. **Configuración:** tarjeta con código QR a la descarga, pasos numerados, 5 minutos.
2. **Emparejamiento:** encender el pod, abrir la app, aceptar permisos de Bluetooth, elegir el pod por su nombre amigable e ingresar la clave de la etiqueta.
3. **Rutina:** elegir una rutina predefinida (3 plantillas) o crear una sencilla.
4. **Entrenamiento:** iniciar, golpear los estímulos y finalizar. El pod funciona aunque el teléfono se desconecte.
5. **Resultados:** pantalla de resumen y gráficas con comparación con la sesión anterior.
6. **Errores comunes:** guía en la app para batería baja, pod no encontrado, permisos denegados, sin conexión y reinicio del pod. Sin respuesta, el usuario escribe a un canal de soporte (WhatsApp).
7. **Firmware:** en el piloto, actualización por USB-C por el equipo en una visita; OTA por Wi-Fi solo si el tiempo lo permite **[Hipótesis]**.
8. **Comentarios:** cuestionario breve en la app tras cada sesión y entrevista final.

## 8.2 Métricas

**Pruebas técnicas** (metas propuestas, no resultados):

| Métrica | Meta propuesta | Cómo se mide |
|---|---|---|
| Tiempo hasta el primer entrenamiento | ≤ 10 min en ≥ 80 % de usuarios | Cronómetro y registro en la app |
| Sesiones completadas sin asistencia | ≥ 90 % | Registro de sesiones y soporte |
| Tasa de desconexiones | < 1 por sesión de 30 min | Registro de eventos de conexión |
| Pérdida de datos | 0 eventos perdidos tras la sincronización | Comparación de `seq` en el pod y en la base |
| Repetibilidad de mediciones | CV < 10 % en impactos de referencia | Banco y verificación periódica |
| Autonomía real | ≥ 3 h en uso típico | Registro de batería |
| Fallas mecánicas | Sin falla crítica en el periodo | Bitácora y fotografías |

**Pruebas de deseabilidad:**

| Métrica | Meta propuesta | Cómo se mide |
|---|---|---|
| Uso recurrente | ≥ 2 sesiones por semana en ≥ 3 de 4 semanas | Registro de sesiones |
| Comprensión de las métricas | ≥ 80 % de respuestas correctas sobre qué significa cada métrica | Cuestionario con ejemplos |
| Valor percibido de las recomendaciones | ≥ 4 de 5 en la mayoría de los usuarios | Escala Likert tras la sesión |

**Disposición de pago:** preguntas directas de rango de precio y compra de pods o preventa con depósito simbólico, separadas de la experiencia de uso. **No se infiere disposición de pago de la satisfacción.**

---

# PASO 9 — Matriz de riesgos y plan de mitigación

Probabilidad (P) e impacto (I): A = alto, M = medio, B = bajo.

| # | Riesgo | P | I | Prioridad | Semana | Detección | Acción preventiva | Plan alternativo |
|---|---|---|---|---|---|---|---|---|
| 1 | **Acelerómetro:** sin existencias, retraso o sobrecosto | A | A | **1** | 1–3 | Cotizaciones y confirmación de pedido en la semana 1 | Pedir 12 unidades el día 1 en dos proveedores | Módulo para 1–2 unidades; reducir a versión "reacción" |
| 2 | **Calibración:** el índice de fuerza no es repetible con el elastómero | A | M | **2** | 5–7 | CV de repetibilidad en banco | Fijar el material y el montaje temprano; calibrar cada unidad | Reportar solo aceleración e impulso |
| 3 | **Batería:** seguridad, calidad y autonomía | M | A | **3** | 4–7 | Pruebas de descarga y temperatura | Celda con protección y de proveedor confiable; límite de brillo | LiPo con protección en soporte rígido |
| 4 | **Carga por apilamiento:** contactos con cortos o desgaste | A | M | **4** | 5–6 | Prueba de corriente y temperatura | Sensor Hall que habilita la salida sin pod encima; límite de corriente; hombro mecánico; MCU alimentado por la batería | USB-C únicamente |
| 5 | **Conectividad** (gateway BLE + ESP-NOW; iOS/Android) | M | A | **5** | 3–7 | Registro de desconexiones, pérdidas y consumo del gateway | Rutina autónoma en el pod; reenvío por `seq`; rol de gateway intercambiable; prueba temprana en la semana 4 | Gateway alterna ventanas BLE/ESP-NOW; BLE entre pods (3–4 seguidores); Wi-Fi/UDP |
| 6 | **Software multiplataforma:** retrasos con el BLE nativo y compilación en iOS | M | A | **6** | 2–6 | Prueba de emparejamiento en un iPhone real en la semana 3 | *Development build* desde la semana 1; cuenta de Apple a tiempo **[Pendiente]** | Piloto solo Android y iOS en una segunda etapa |
| 7 | **PCB:** errores de diseño o plazos de fabricación | M | A | **7** | 4–6 | Revisión del diseño (DRC) y pruebas de v0 | Congelar el diseño en la semana 4; versión de módulos como respaldo | Montaje en perfboard para el piloto de 5 unidades |
| 8 | **Manufactura de carcasas:** tiempo de impresión y variación entre unidades | M | M | **8** | 6–8 | Tiempo medido en la semana 2 | Una pieza de prueba temprana; varias impresoras | Simplificar la geometría; menos piezas |
| 9 | **Presupuesto:** el lote supera el fondo disponible | A | M | **9** | 1–8 | Seguimiento semanal de gastos | Cotizar todo en la semana 1; priorizar versión "reacción" | Lote de 5 unidades |
| 10 | **Alcance y capacidad del equipo** (hardware, firmware, app, backend, sitio, piloto) | A | A | **10** | 1–8 | Entregables semanales vs. plan | Congelar el alcance de la semana 3; recorte por orden de prioridad | Retrasar la página de venta, el leaderboard y las recompensas |

---

# PASO 10 — Decisiones finales

## Escenario A — MVP de ocho semanas (1–2 unidades demostrativas utilizables)

- **Arquitectura:** ESP32 (DevKit o módulo) + módulo ADXL375 + piezo opcional + aro de LEDs + celda protegida con pestañas + TP4056 USB-C con protección + LDO AP2112K-3.3. Demo de la semana 3 con **un pod** y BLE directo. Desde la semana 4: **gateway BLE + ESP-NOW** con 2 pods. Apilamiento: prototipo con un par de pogo magnéticos y una base de maqueta, con decisión al cierre de la semana 5. App React Native con SQLite. Supabase para respaldo y autenticación. Recomendaciones por reglas y LLM opcional.
- **Incluye:** LEDs, impacto, RT, aceleración e impulso, BLE, historial y gráficas, comparación con sesiones anteriores, rutinas sencillas, operación sin conexión y sincronización con reintentos.
- **Excluye:** fuerza en newtons, HarmonyOS, leaderboard en línea, recompensas complejas, OTA, pagos y página de ventas elaborada (una página simple sí). El apilamiento y ESP-NOW multi-pod quedan sujetos a los hitos de las semanas 4–5.
- **Costo:** la electrónica cotizada suma ≈ $951 (incluye ≈ $150 de pogo magnéticos). Con PCB, carcasa y complementos se espera ≈ $1,220–1,510 (≈ $1,070–1,360 sin los pogo) **[Estimado]**. Al límite de los $1,500 MXN; el precio del AP2112K y los complementos están **[Pendientes]**.
- **Riesgos principales:** autenticidad y disponibilidad del acelerómetro, coexistencia BLE + ESP-NOW, plazo.
- **Criterios de aceptación:** 100 impactos consecutivos registrados sin pérdida; RT dentro de ±5 ms de la referencia en ≥ 90 % de las pruebas; 3 h de autonomía; una persona completa el primer entrenamiento sin ayuda en ≤ 10 min.

## Escenario B — Primera tirada de 5–10 unidades

- **Arquitectura:** PCB propia (2 capas, fabricación externa) con ESP32-WROOM-32E, módulo ADXL375 en las primeras 5 unidades (CI en PCB propia en una segunda tirada), TP4056 con protección, LDO AP2112K y conectores; ensamblaje manual; carcasa PETG con superficie de EPDM/EVA o TPU; calibración por unidad; Supabase Pro durante el piloto; gateway BLE + ESP-NOW y apilamiento según los hitos de las semanas 4–5.
- **Incluye:** todo lo del Escenario A, más prueba de fin de línea, hoja de control por unidad, etiquetas con clave de emparejamiento, empaque y guía de uso, y piloto con usuarios.
- **Excluye:** certificación para venta, fuerza en newtons, ML propio, comunidad.
- **Costo estimado:** ≈ $11,800 MXN de fabricación en efectivo para 10 unidades **[Estimado, ±25 %]**, más ≈ $460 MXN al mes de Supabase Pro y gastos únicos del banco de calibración.
- **Riesgos principales:** PCB y plazos de envío, ensamblaje de LGA, calidad de las celdas, tiempo de impresión.
- **Criterios de aceptación:** ≥ 90 % de las unidades pasan la prueba de fin de línea; variación entre unidades dentro de tolerancia definida; 0 eventos perdidos tras sincronización; ≥ 3 h de autonomía en todas las unidades.
- **Nota:** 5 unidades en la semana 8 son posibles con riesgo alto; **10 probablemente requieran las semanas 9–12.**

## Escenario C — Producto futuro

- **Arquitectura:** diseño para inyección de plástico, certificación, carga por apilamiento robusta, galgas extensométricas o celda de carga con ADC rápido para fuerza directa, OTA firmada, backend escalable.
- **Incluye:** IA avanzada (modelos entrenados con datos reales), análisis longitudinal, comunidad, leaderboard ampliado, HarmonyOS nativo, nuevas funciones de hardware.
- **Excluye:** nada, sujeto a validación.
- **Costo:** depende de volumen e inversión **[Pendiente]**.
- **Riesgos principales:** homologación y requisitos regulatorios **[Pendiente]**, financiamiento, soporte posventa.
- **Criterios de aceptación:** definidos tras el piloto, incluyendo disposición de pago y retención.

## Decisiones que el equipo debe tomar antes de comprar componentes o fabricar la PCB

1. ¿El PDS exige realmente la fuerza en newtons o basta con aceleración e impulso?
2. ¿Los $1,500 MXN son para 1 unidad o para varias? ¿Quién financia el lote de 10 (≈ $11,800)?
3. ¿Se acepta que el piloto inicial sea de 5 unidades en la semana 8 y 10 en las semanas 9–12?
4. ¿Módulo ADXL375 para el prototipo y las primeras 5 unidades, y CI para la siguiente tirada? ¿Qué proveedor tiene stock real (pedir cotización de 12 unidades)?
5. ¿Se conserva o se elimina el piezo (decidir con la prueba de la semana 2)?
6. ¿Se confirman las decisiones vigentes: gateway BLE + ESP-NOW y apilamiento con pogo magnéticos, con hitos en las semanas 4 y 5?
7. ¿Qué equipo y capacidades tiene el laboratorio para PCB (ancho de pista, vías, serigrafía)? ¿Se aprueba una PCB externa?
8. ¿Qué material de superficie se fija (TPU vs. EPDM sobre EVA) tras la prueba de la semana 2–3?
9. ¿Cuántas impresoras y horas hay para las 10 carcasas?
10. ¿Qué cuenta de Apple y distribución (TestFlight) se usará?
11. ¿Quién es el segmento objetivo y cuál es la competencia y su precio en México (cotizar)?
12. ¿Cómo se manejarán el consentimiento y los datos personales del piloto (revisar con la institución)?
13. ¿Qué clave de API del LLM y qué presupuesto mensual se asignan?
14. ¿Quién será responsable de la prueba de fin de línea y de la calibración por unidad?

---

## Fuentes consultadas (1 de octubre de 2026)

- **ADXL375, características:** Analog Devices (analog.com/ADXL375); módulo Adafruit (adafruit.com/product/5374) con USD 24.95 (1–9 u.), 22.46 (10–99 u.) y 19.96 (100+).
- **ADXL375BCCZ-RL en LCSC:** lcsc.com/product-image/C662206.html (USD 7.44, 6.38, 5.74 y 5.20 por volumen; 0 en inventario al consultar).
- **Mouser, sitios regionales (no el de México):** mouser.ec y mouser.hn, con existencias del ADXL375BCCZ; mouser.in con 5,000 unidades del ADXL375BCCZ-RL "esperadas" el 22-10-2026.
- **ESP32-WROOM-32E-N4:** lcsc.com/product-image/C701341.html y jlcpcb.com/partdetail/C701341 (parte "Extended"; precios y existencias varían por página).
- **Supabase:** guías de precios 2026 (makerkit.dev/blog/saas/supabase-pricing; focusreactive.com/blog/supabase-price/; cloudzero.com/blog/supabase-pricing/). Verificar siempre en supabase.com/pricing.
- **HarmonyOS NEXT:** en.wikipedia.org/wiki/HarmonyOS_5 y notas de prensa (huaweicentral.com).
- **No verificado:** precios y existencias en tiendas mexicanas, disponibilidad del ADXL375 en la biblioteca de JLCPCB PCBA, plazos de envío a México, soporte actual de React Native para BLE y mínimos de versión, normativa mexicana vigente y precio de la competencia.
