<img src="https://r2cdn.perplexity.ai/pplx-full-logo-primary-dark%402x.png" style="height:64px;margin-right:32px"/>

# Actúa como analista de mercado con especialización en

dimensionamiento para startups de hardware y software en
América Latina. Tu metodología es el enfoque top-down
con triangulación de fuentes verificables: INEGI, CEPAL,
BID, reportes de industria con autor y año identificables.
No inventes cifras — si no existe fuente verificable para
un número, lo señalas y explicas cómo estimarlo con
lógica de primer principio.

Somos emprendedores en México:

Concepto: [Lumetriq: Dispositivo IoT (hardware y app) para entrenamiento de agilidad y reflejos mediante paneles luminosos táctiles, similar a BlazePod. Funciona emitiendo estímulos visuales que el usuario debe desactivar físicamente, automatizando la dirección de los ejercicios y gamificando el esfuerzo. Combinado con una aplicación que ofrezca múltiples beneficios como rastreo de progreso, leaderboards, opciones de personalización de rutinas, etc. Se piensa que la App puede ser la mejor trayectoria para desarrollar un producto interesante.]

Segmento objetivo: \[Segmento objetivo: Estudios boutique, gimnasios HIIT, boxes de CrossFit y centros de entrenamiento funcional en México, especialmente los que ofrecen clases grupales de alta intensidad

CAPA 1 - Demográfica: Profesionales a cargo de atletas de combate o atletismo en gimnasios institucionales o locales.

CAPA 2 - Conductual: Ya ejecutan drills de reacción, pero usan métodos manuales y tediosos (aplausos, silbatos, cronómetros) o tests gratuitos.

CAPA 3 - Psicográfica: Valoran la motivación, la variedad y la competencia ("el primero que toca gana") muy por encima de la medición analítica profunda.

CAPA 4 - Económica: Rechazan las suscripciones SaaS B2B costosas; anclan el precio del software al de apps de consumo (~\$60-\$100 MXN) y su verdadera disposición de compra está en adquirir el hardware físico mediante un pago único.
Se tiene la hipótesis que los gimnasios podrían estar dispuestos a pagar una suscripción mayor por ofrecer el servicio de la app en sus instalaciones.\]

Precio estimado del producto/servicio: [500 - 600 MXN]

Modelo de ingresos: $$
venta única y suscripción mensual /
suscripción anual
$$

Mercado inicial: México
Expansión potencial: LATAM en año 3+

Construye TAM, SAM y SOM con este razonamiento explícito:

TAM: Universo total con el problema Y disposición de pago.
No solo "cuántos tienen el problema" — cuántos pagarían.
Mostrar la reducción paso a paso con fuente de cada número.

SAM: El subconjunto alcanzable con el modelo actual.
Especificar exactamente qué lo reduce: geografía, canal,
precio, idioma, tamaño mínimo de cliente.

SOM: La porción realista en los primeros 2 años.
Justificar el porcentaje con lógica de go-to-market concreta:
cuántos vendedores, qué canal, qué geografía piloto.
El número sin lógica no sirve.

FORMATO DE SALIDA:

════════════════════════════════════════════════════════
DIMENSIONAMIENTO DE MERCADO
Concepto: [nombre]
════════════════════════════════════════════════════════

TAM — Mercado Total Direccionable
Universo de partida: [n° y descripción]

↓ Filtro $$
descripción
$$: [n° resultante] · Fuente: [nombre]

↓ Filtro $$
descripción
$$: [n° resultante] · Fuente: [nombre]

Universo final TAM: [n° personas o negocios]

Valor anual: $$
$ MXN] · Supuesto de precio: [$ por usuario/año
$$

SAM — Mercado Alcanzable
Filtros aplicados al TAM:

· $$
filtro
$$: reduce a [n°]

· $$
filtro
$$: reduce a [n°]

Universo SAM: [n°]
Valor anual: [\$ MXN]

SOM — Mercado Obtenible (años 1–2)
Meta: [n° clientes]
Porcentaje del SAM: [%]
Lógica de go-to-market:
· [canal específico]
· [geografía piloto]
· [capacidad del equipo]
Valor anual: [\$ MXN]

────────────────────────────────────────────────────────
SEÑAL DE VIABILIDAD:
SOM × precio anual = [\$ MXN]
¿Cubre costos operativos básicos de una startup de 4 personas?
Sí / No / Marginal — [1 oración de justificación]

FUENTES UTILIZADAS:
· [fuente 1 con año]
· [fuente 2 con año]
════════════════════════════════════════════════════════

════════════════════════════════════════════════════════

# DIMENSIONAMIENTO DE MERCADO

**Concepto:** Lumetriq\
════════════════════════════════════════════════════════

## Nota metodológica

El dato público verificable más cercano al segmento es la clase SCIAN **713943: “Centros de acondicionamiento físico del sector privado”**. Sin embargo, el comunicado público del DENUE 05/2026 no desglosa en su texto el número de establecimientos de esa clase. Por ello, no presentaré como cifra oficial el dato de 30,242 que aparece en una fuente secundaria no institucional. Para un modelo defendible ante inversionistas, esa cifra debe validarse descargando el microdato del DENUE y filtrando la clase 713943. El DENUE sí confirma que registra ubicación, actividad económica y tamaño de los establecimientos, y que es apropiado para identificar clientes potenciales.[^1_1][^1_2]

En consecuencia, el dimensionamiento siguiente usa un **escenario de trabajo explícito**, no una afirmación de mercado observado: **30,242 establecimientos privados** como base provisional, sujeto a validación directa en el archivo DENUE.

También hay una inconsistencia crítica en el precio: MXN 500–600 parece ser el precio de venta de hardware, no el valor anual de una suscripción B2B. Para evitar inflar el mercado, separo:

- **Hardware:** MXN 550 por kit.
- **Software B2B:** MXN 1,200 anuales por establecimiento, equivalente a MXN 100 mensuales.
- El valor anual combina venta inicial del kit y software del primer año: **MXN 1,750 por cliente**.

La disposición de pago no está medida públicamente para este producto. Por tanto, los filtros de adopción son supuestos de primer principio que deben validarse mediante entrevistas, preventas y pilotos.

______________________________________________________________________

# TAM — Mercado Total Direccionable

**Universo de partida:** 30,242 establecimientos privados de acondicionamiento físico en México, escenario provisional basado en la clase SCIAN 713943 del DENUE 05/2026.\
**Fuente que debe utilizarse para validación:** INEGI, DENUE 05/2026 y descarga filtrada por SCIAN 713943. El DENUE 05/2026 reporta 6,138,075 establecimientos totales en México.[^1_1]

```text
30,242 establecimientos
        ↓
Filtro: ofrecen entrenamiento presencial y pueden utilizar
paneles táctiles en clases, drills o circuitos funcionales
        ↓ 60%
18,145 establecimientos
        ↓
Filtro: tienen suficiente afinidad con HIIT, funcional,
CrossFit, combate, atletismo o entrenamiento de reflejos
        ↓ 45%
8,165 establecimientos
        ↓
Filtro: reconocen el problema y actualmente lo resuelven
con métodos manuales, cronómetros, silbatos o tests gratuitos
        ↓ 60%
4,899 establecimientos
        ↓
Filtro: tienen disposición de pagar por hardware y software
en el primer año
        ↓ 35%
1,715 establecimientos
```


### Universo final TAM

**TAM estimado:** **1,715 establecimientos compradores potenciales**.

Los porcentajes no son cifras publicadas por INEGI; son supuestos de primer principio:

- El 60% elimina establecimientos centrados principalmente en máquinas, rehabilitación, yoga, pilates u otras actividades con menor ajuste.
- El 45% elimina instalaciones sin clases grupales intensivas o sin uso frecuente de ejercicios de reacción.
- El 60% supone que una parte importante del segmento ya percibe el problema operativo.
- El 35% representa la disposición de pago inicial para un producto nuevo de hardware más software, no la mera existencia del problema.


### Valor anual del TAM

| Componente | Cálculo | Valor |
| :-- | --: | --: |
| Hardware inicial | 1,715 × MXN 550 | MXN 943,250 |
| Software año 1 | 1,715 × MXN 1,200 | MXN 2,058,000 |
| **Valor del primer año** | 1,715 × MXN 1,750 | **MXN 3,001,250** |
| **ARR recurrente posterior** | 1,715 × MXN 1,200 | **MXN 2,058,000** |

**Supuesto de precio:** MXN 550 por kit y MXN 100 mensuales por establecimiento.\
Si Lumetriq solo cobra MXN 500–600 una vez y no monetiza software, el TAM sería únicamente **MXN 943,250** de ventas iniciales, sin ingresos recurrentes.

______________________________________________________________________

# SAM — Mercado Alcanzable

El SAM debe reflejar lo que Lumetriq puede vender con el modelo actual: producto en español, fabricación o importación manejable, venta directa o digital, soporte remoto y clientes urbanos con clases grupales.

## Filtros aplicados al TAM

```text
TAM: 1,715 compradores potenciales
        ↓
Filtro geográfico: Ciudad de México,
Estado de México, Guadalajara, Monterrey y Puebla
        ↓ 55%
943 establecimientos
        ↓
Filtro de tamaño y operación: al menos una clase grupal
recurrente y capacidad de probar equipo nuevo
        ↓ 50%
472 establecimientos
        ↓
Filtro de canal: accesibles mediante venta directa,
Instagram, WhatsApp, distribuidores de equipo funcional
o alianzas con coaches
        ↓ 70%
330 establecimientos
        ↓
Filtro económico: aceptan hardware de MXN 550 y
software de MXN 1,200 anuales
        ↓ 60%
198 establecimientos
```


### Universo SAM

**SAM estimado:** **198 establecimientos**.

### Valor anual del SAM

| Componente | Cálculo | Valor |
| :-- | --: | --: |
| Hardware inicial | 198 × MXN 550 | MXN 108,900 |
| Software año 1 | 198 × MXN 1,200 | MXN 237,600 |
| **Valor del primer año** | 198 × MXN 1,750 | **MXN 346,500** |
| **ARR recurrente posterior** | 198 × MXN 1,200 | **MXN 237,600** |

### Qué excluye el SAM

El SAM no incluye:

- Gimnasios públicos o instituciones deportivas con procesos de compra largos.
- Cadenas nacionales que requieran certificaciones, integraciones o contratos corporativos.
- Instalaciones rurales o ciudades sin densidad suficiente para soporte y demostraciones.
- Usuarios domésticos, atletas individuales y consumidores finales.
- Clientes que solo quieren una app gratuita.
- Gimnasios que no realizan clases grupales de alta intensidad.
- Clientes que no pueden dedicar espacio, carga eléctrica o supervisión al dispositivo.

El porcentaje de actividad física de la población no debe utilizarse para multiplicar directamente el número de gimnasios: MOPRADEF mide personas, no establecimientos compradores. En 2024, INEGI reportó que 41.1% de las personas adultas en 32 ciudades de 100,000 habitantes o más realizó actividad física en su tiempo libre, y 64.2% de la población físicamente activa lo hizo en un nivel suficiente. Es una señal de demanda contextual, no una medición de disposición de pago de gimnasios.[^1_3]

______________________________________________________________________

# SOM — Mercado Obtenible, años 1–2

## Meta

**Meta base:** 45 clientes pagadores al cierre del segundo año.

**Porcentaje del SAM:** $45 / 198 = 22.7\%$.

Ese porcentaje no significa capturar 22.7% de todo el mercado nacional; significa capturar 45 cuentas dentro de un SAM deliberadamente reducido a cinco zonas urbanas y clientes accesibles por venta directa.

## Lógica de go-to-market

- **Geografía piloto:** Ciudad de México y área metropolitana durante los primeros 9–12 meses; Guadalajara y Monterrey en el segundo año.
- **Canal inicial:** demostraciones presenciales en clases de funcional, HIIT y CrossFit.
- **Canal digital:** anuncios geolocalizados, Instagram, TikTok, WhatsApp y videos de ejercicios competitivos.
- **Canal de confianza:** coaches, preparadores físicos, box owners y distribuidores de equipo funcional.
- **Oferta inicial:** kit con descuento por piloto, una rutina demostrativa y periodo de prueba de la aplicación.
- **Venta:** el dueño compra el hardware; el entrenador usa la app para crear sesiones, competencias y rankings.
- **Capacidad comercial:** dos fundadores dedicados a ventas y demostraciones, uno a producto y uno a operaciones/soporte.
- **Productividad asumida:** cada vendedor puede realizar 8–10 demostraciones calificadas por semana; con una conversión final de 5–8%, la meta de 45 clientes en dos años es exigente pero plausible.
- **Expansión:** alianzas con 3–5 coaches o distribuidores regionales, cada uno aportando aproximadamente 5–8 clientes durante el segundo año.

Una trayectoria posible sería:


| Periodo | Clientes nuevos | Clientes acumulados |
| :-- | --: | --: |
| Año 1 | 12–18 | 12–18 |
| Año 2 | 27–33 | 39–51 |
| **Meta base** | — | **45** |

## Valor anual del SOM

| Componente | Cálculo | Valor |
| :-- | --: | --: |
| Hardware inicial | 45 × MXN 550 | MXN 24,750 |
| Software año 1 | 45 × MXN 1,200 | MXN 54,000 |
| **Ingresos del primer año por la base** | 45 × MXN 1,750 | **MXN 78,750** |
| **ARR recurrente al cierre del año 2** | 45 × MXN 1,200 | **MXN 54,000** |

El SOM es pequeño en ingresos porque el precio supuesto también es pequeño. Incluso con 198 clientes —todo el SAM— el ingreso recurrente anual sería solo MXN 237,600 si se cobra MXN 100 mensuales por establecimiento.

______________________________________________________________________

# SEÑAL DE VIABILIDAD

**SOM × precio anual = MXN 78,750 de ingresos del primer año.**

**¿Cubre costos operativos básicos de una startup de cuatro personas? No.** Con MXN 78,750 de ingresos brutos anuales no se cubren salarios, manufactura, inventario, adquisición de clientes, soporte, desarrollo de app y cumplimiento; la hipótesis solo sería viable como piloto subsidiado o proyecto paralelo.

## Implicación comercial

El problema no parece ser únicamente el tamaño del mercado, sino el **ARPU insuficiente**. Para sostener una startup de cuatro personas, Lumetriq probablemente necesita una de estas estructuras:


| Modelo | Ejemplo de precio | Ingreso anual con 45 clientes |
| :-- | --: | --: |
| Hardware barato + app básica | MXN 550 + MXN 100/mes | MXN 78,750 primer año |
| Kit profesional + software | MXN 4,000 + MXN 500/mes | MXN 450,000 primer año |
| Licencia por instalación | MXN 8,000 + MXN 1,000/mes | MXN 900,000 primer año |
| Venta a cadenas o academias | Contrato anual de MXN 25,000 | MXN 1,125,000 |

La hipótesis más prometedora es cobrar por **instalación o sede**, no por usuario individual. La app puede seguir siendo simple y competitiva, pero el valor económico debe vincularse a:

- Mayor variedad de clases.
- Menor tiempo de preparación del coach.
- Retención y engagement de alumnos.
- Rankings y competencias internas.
- Uso simultáneo por grupos.
- Reportes básicos para el dueño.
- Contenido y rutinas exclusivas.

Con el precio actual de MXN 500–600 como ticket total, el producto puede funcionar como experimento de validación, pero no como negocio de hardware-software con equipo completo.

______________________________________________________________________

# FUENTES UTILIZADAS

- **INEGI, DENUE 05/2026.** Reporta 6,138,075 establecimientos en México y describe el directorio como fuente de ubicación, actividad económica y tamaño para estudios de mercado.[^1_1]
- **INEGI, MOPRADEF 2024, publicado en 2025.** Reporta 41.1% de población adulta físicamente activa en 32 ciudades y 64.2% de actividad en nivel suficiente.[^1_3]
- **INEGI, documentación del DENUE.** Confirma que el directorio permite identificar establecimientos por actividad, ubicación y tamaño, y que puede utilizarse para localizar clientes potenciales.[^1_2]
- **SCIAN 713943.** Clase económica utilizada como definición operativa del universo de centros privados de acondicionamiento físico. La cifra exacta de establecimientos debe extraerse y verificarse directamente en el archivo DENUE, no tomarse de una fuente secundaria.[^1_4]

**Conclusión:** el escenario provisional arroja un TAM de **1,715 establecimientos**, un SAM de **198** y un SOM de **45 clientes en dos años**. La oportunidad inicial es validable, pero con MXN 500–600 por producto y una suscripción de MXN 100 mensuales no alcanza para sostener una startup de cuatro personas; antes de escalar conviene probar un precio por sede considerablemente mayor.

<span style="display:none">[^1_10][^1_11][^1_12][^1_13][^1_14][^1_15][^1_16][^1_17][^1_18][^1_19][^1_20][^1_21][^1_22][^1_23][^1_24][^1_25][^1_26][^1_27][^1_28][^1_29][^1_30][^1_31][^1_32][^1_33][^1_34][^1_35][^1_36][^1_37][^1_38][^1_39][^1_5][^1_6][^1_7][^1_8][^1_9]</span>

<div align="center">⁂</div>

[^1_1]: https://www.inegi.org.mx/contenidos/saladeprensa/boletines/2026/denue/DENUE2026_05.pdf

[^1_2]: https://www.inegi.org.mx/rnm/index.php/catalog/1103/data-dictionary/F10

[^1_3]: https://www.inegi.org.mx/contenidos/saladeprensa/boletines/2025/mopradef/mopradef2024.pdf

[^1_4]: https://www.ssaver.gob.mx/proteccioncontrariesgossanitarios/wp-content/uploads/sites/10/2026/03/CATALOGO-DE-GIROS-ESTATAL-SALUBRIDAD-LOCAL-marzo-2026.pdf

[^1_5]: https://www.inegi.org.mx/contenidos/programas/mopradef/2024/doc/resultados_mopradef_2024.pdf

[^1_6]: https://en.www.inegi.org.mx/contenidos/programas/mopradef/2024/doc/889463922810.pdf

[^1_7]: https://www.inegi.org.mx/programas/mopradef/

[^1_8]: https://www.inegi.org.mx/rnm/index.php/catalog/1067

[^1_9]: https://www.inegi.org.mx/contenidos/programas/mopradef/2024/doc/889463922803.pdf

[^1_10]: https://www.inegi.org.mx/contenidos/saladeprensa/boletines/2025/mopradef/mopradef2024_RR.pdf

[^1_11]: https://www.inegi.org.mx/contenidos/programas/mopradef/doc/resultados_mopradef_2025.pdf

[^1_12]: https://www.inegi.org.mx/contenidos/programas/mopradef/doc/889463922797.pdf

[^1_13]: https://en.www.inegi.org.mx/contenidos/saladeprensa/boletines/2025/mopradef/mopradef2024_RR.docx

[^1_14]: https://en.www.inegi.org.mx/programas/mopradef/

[^1_15]: https://en.www.inegi.org.mx/contenidos/saladeprensa/boletines/2024/denue/denue2024_05.pdf

[^1_16]: https://www.inegi.org.mx/app/mapa/denue/Default.aspx?idee=19992

[^1_17]: https://www.inegi.org.mx/contenidos/saladeprensa/boletines/2024/denue/denue2024_11.pdf

[^1_18]: https://www.gslb.inegi.org.mx/contenidos/programas/mopradef/2024/doc/889463922803.pdf

[^1_19]: https://en.www.inegi.org.mx/app/mapa/denue/default.aspx

[^1_20]: https://en.www.inegi.org.mx/app/mapa/Denue/

[^1_21]: https://www.inegi.org.mx/app/mapa/denue/

[^1_22]: https://www.inegi.org.mx/temas/directorio/

[^1_23]: https://www.inegi.org.mx/servicios/api_denue.html

[^1_24]: https://www.inegi.org.mx/rnm/index.php/catalog/1103

[^1_25]: https://www.inegi.org.mx/contenidos/temas/MapaDigital/Doc/consulta_denue.pdf

[^1_26]: https://scian-mexico.com/scian/clase/713943-centros-de-acondicionamiento-fisico-del-sector-privado/

[^1_27]: https://mrgimnasios.com/blog/cuantos-gimnasios-hay-cerca-denue-inegi

[^1_28]: https://mrgimnasios.com/blog/como-es-el-gimnasio-promedio-en-mexico

[^1_29]: https://scian-mexico.com/scian/subrama/71394-clubes-deportivos-y-centros-de-acondicionamiento-fisico/

[^1_30]: https://mexicoo.mx/strong-gym-2261303

[^1_31]: https://mexicoo.mx/gimnasio-dancor-sport-gym-8889376

[^1_32]: https://mexicoo.mx/gimnasio-calmecac-fitness-8325430

[^1_33]: https://www.inegi.org.mx/rnm/index.php/catalog/979

[^1_34]: https://www.inegi.org.mx/rnm/index.php/catalog/924

[^1_35]: https://www.inegi.org.mx/contenidos/temas/directorio/doc/metodologia.pdf

[^1_36]: https://en.www.inegi.org.mx/app/mapa/denue/nota.pdf

[^1_37]: https://www.inegi.org.mx/app/descarga/default.html

[^1_38]: https://www.inegi.org.mx/rnm/index.php/catalog/668

[^1_39]: https://www.inegi.org.mx/rnm/index.php/catalog/587


---

# Considera que los 500 - 600 son el precio de producción por unidad y que ese tipo de productos como Blazepod, ROX y FitLight se venden en paquetes de 3 y 6 dispositivos. Haz una investigación de cuál sería un precio pertinente de ventas para estos dispisitvos e investiga el precio de suscripción de la app para un usuario humano y un gimnasio y con base en eso asignale un precio hipotético al producto y servicio e incorporalo al análisis previo

════════════════════════════════════════════════════════

# DIMENSIONAMIENTO DE MERCADO

**Concepto:** Lumetriq\
**Actualización:** precio de hardware y suscripciones\
════════════════════════════════════════════════════════

## 1. Referencias de precio

Los competidores muestran que el hardware no se vende cerca del costo de fabricación. BlazePod publica kits y bundles entre **USD 329 y USD 1,352**, dependiendo del número de pods, accesorios y nivel de uso profesional.[^2_1][^2_2]

FITLIGHT publica un sistema de **USD 749** y un paquete deportivo de seis luces por **USD 1,869**. Su aplicación se incluye sin suscripción adicional.[^2_3][^2_4]

ROX Pro aparece publicado alrededor de **GBP 229 para tres unidades** y **GBP 629 para seis unidades con estuche de carga**, aunque se trata de precio de distribuidor, no necesariamente de precio oficial para México.[^2_5]

BlazePod ofrece una aplicación gratuita limitada y un plan profesional de aproximadamente **USD 9.99 mensuales el primer año o USD 99.99 anuales**, que sube posteriormente a aproximadamente **USD 14.99 mensuales o USD 149.99 anuales**.[^2_6][^2_7]

Como referencia de software de entrenamiento, TrainHeroic parte de **USD 9.99 mensuales para un atleta** y escala hasta **USD 99.99 mensuales para 100 atletas**; sus planes para equipos mayores llegan a varios cientos de dólares mensuales.[^2_8][^2_9]

Para convertir referencias internacionales utilicé aproximadamente **MXN 17.50 por USD**, cercano al tipo de cambio publicado por Banxico el 24 de septiembre de 2026.[^2_10]

### Benchmark convertido a México

| Producto | Paquete | Precio publicado aproximado | Equivalente aproximado |
| :-- | --: | --: | --: |
| BlazePod | Kit inicial | USD 329 | MXN 5,760 |
| BlazePod | Bundle profesional | USD 539–766 | MXN 9,440–13,400 |
| ROX Pro | 3 unidades | GBP 229 | Aproximadamente MXN 5,200–5,500 |
| ROX Pro | 6 unidades | GBP 629 | Aproximadamente MXN 14,000–15,000 |
| FITLIGHT | Sistema | USD 749 | MXN 13,100 |
| FITLIGHT | Paquete de 6 luces | USD 1,869 | MXN 32,700 |

Estos precios no son directamente comparables: incluyen accesorios, software, garantía, estuche de carga, importación o posicionamiento profesional. Aun así, confirman que el mercado acepta precios muy superiores a MXN 500–600 por unidad cuando el producto se vende como sistema.

______________________________________________________________________

## 2. Precio hipotético de Lumetriq

### Costo base

- **Costo de producción estimado por dispositivo:** MXN 550.
- No incluye necesariamente empaque, control de calidad, mermas, certificaciones, garantía, logística, impuestos, soporte ni desarrollo de software.
- Para los cálculos se supone un costo total directo de fabricación y preparación de **MXN 700 por dispositivo**. Este monto es un supuesto operativo y debe validarse con cotizaciones.


### Precio recomendado de hardware

Sugiero lanzar dos paquetes:


| Paquete | Contenido | Precio sugerido al cliente |
| :-- | --: | --: |
| Lumetriq Starter | 3 dispositivos, cargador y accesorios básicos | **MXN 4,490** |
| Lumetriq Studio | 6 dispositivos, estación de carga, accesorios y estuche | **MXN 7,990** |

El paquete de seis tiene un precio promedio de **MXN 1,332 por dispositivo**, equivalente a un margen bruto preliminar de aproximadamente 47% antes de costos indirectos si el costo total unitario fuese MXN 700.

El precio de MXN 7,990 es sustancialmente inferior a BlazePod, ROX Pro y FITLIGHT, pero suficientemente superior al costo para financiar garantía, inventario y venta. También permite posicionar Lumetriq como una herramienta profesional accesible, no como un juguete electrónico.

### Precio recomendado de la aplicación

#### Usuario individual

| Plan | Precio sugerido |
| :-- | --: |
| Gratis | MXN 0 |
| Lumetriq Pro mensual | **MXN 149/mes** |
| Lumetriq Pro anual | **MXN 1,290/año** |

El precio anual equivale a MXN 107.50 mensuales y queda por debajo del equivalente en México de muchas aplicaciones internacionales de entrenamiento profesional. También está cerca de la referencia local de Strava, cuyo precio listado en la App Store mexicana incluye una suscripción de MXN 119.[^2_11]

El usuario individual debería recibir:

- Rutinas básicas.
- Temporizador y control de luces.
- Historial de sesiones.
- Algunos rankings.
- Compatibilidad con un paquete de tres o seis dispositivos.

La versión Pro puede incluir:

- Biblioteca completa de ejercicios.
- Personalización avanzada.
- Historial ampliado.
- Progresión y métricas.
- Retos y rankings privados.
- Exportación de resultados.


#### Gimnasio o estudio

| Plan | Precio sugerido | Uso |
| :-- | --: | :-- |
| Studio Basic | **MXN 499/mes** o MXN 4,990/año | Una sede, hasta 3 coaches, hasta 25 atletas activos |
| Studio Pro | **MXN 899/mes** o MXN 8,990/año | Una sede, coaches ilimitados, clases grupales, rankings y reportes |
| Multi-sede | Desde **MXN 1,499/mes** | Varias sedes y administración centralizada |

Para el dimensionamiento utilizaré como precio base **MXN 899 mensuales**, es decir:

$$
MXN\ 899 \times 12 = MXN\ 10,788\ \text{anuales}
$$

Este precio es mucho más defendible que MXN 100 mensuales porque la compra no corresponde a una aplicación de consumo: el gimnasio utiliza el software para múltiples atletas, clases y coaches, y el sistema genera una experiencia comercializable dentro de sus instalaciones.

______________________________________________________________________

# TAM — Mercado Total Direccionable

**Universo de partida:** 30,242 establecimientos privados de acondicionamiento físico en México, escenario provisional que debe validarse con una extracción directa del DENUE para la clase SCIAN 713943. El DENUE 05/2026 reporta 6,138,075 establecimientos totales y permite filtrarlos por actividad, ubicación y tamaño.[^2_12][^2_13]

```text
30,242 establecimientos privados
        ↓
Filtro: tienen actividades de entrenamiento presencial
        ↓ 60%
18,145 establecimientos
        ↓
Filtro: ofrecen HIIT, funcional, CrossFit, combate,
atletismo o clases de alta intensidad
        ↓ 45%
8,165 establecimientos
        ↓
Filtro: pueden utilizar un sistema de reacción visual
en sesiones individuales o grupales
        ↓ 60%
4,899 establecimientos
        ↓
Filtro: tienen disposición de invertir en un sistema
de hardware de MXN 4,490–7,990
        ↓ 35%
1,715 establecimientos
```


### Universo final TAM

**TAM:** **1,715 establecimientos compradores potenciales**.

El número de 1,715 sigue siendo un escenario estimado, no una cifra observada de disposición de pago. La variable más incierta es el último filtro: no existe, en las fuentes consultadas, una encuesta pública que mida cuántos gimnasios mexicanos pagarían por sistemas de luces reactivas.

### Valor anual del TAM

Para el cálculo se utiliza el paquete promedio esperado:

- 70% de clientes: paquete Studio de 6 dispositivos a MXN 7,990.
- 30% de clientes: paquete Starter de 3 dispositivos a MXN 4,490.
- Ticket hardware promedio ponderado:

$$
(70\% \times 7,990) + (30\% \times 4,490)
= MXN\ 6,940
$$

- Suscripción Studio Pro: MXN 10,788 anuales.

| Componente | Cálculo | Valor |
| :-- | --: | --: |
| Hardware inicial | 1,715 × MXN 6,940 | **MXN 11,902,100** |
| Suscripción año 1 | 1,715 × MXN 10,788 | **MXN 18,505,420** |
| **Valor total año 1** | Hardware + software | **MXN 30,407,520** |
| **ARR posterior** | 1,715 × MXN 10,788 | **MXN 18,505,420** |

El TAM de ingresos recurrentes es, por tanto, aproximadamente **MXN 18.5 millones anuales**, mientras que el mercado de primera compra hardware más software sería aproximadamente **MXN 30.4 millones**.

______________________________________________________________________

# SAM — Mercado Alcanzable

El modelo actual de Lumetriq puede atender clientes en español, con hardware vendido directamente, soporte remoto y demostraciones presenciales. No supone todavía una red nacional de distribuidores, certificaciones para instituciones públicas ni integraciones con cadenas.

```text
TAM: 1,715 establecimientos
        ↓
Filtro geográfico: CDMX, Estado de México,
Guadalajara, Monterrey y Puebla
        ↓ 55%
943 establecimientos
        ↓
Filtro: al menos una clase grupal recurrente
y capacidad de comprar equipo profesional
        ↓ 50%
472 establecimientos
        ↓
Filtro: accesibles mediante venta directa,
redes sociales, coaches o distribuidores
        ↓ 70%
330 establecimientos
        ↓
Filtro: aceptan ticket inicial aproximado
de MXN 6,940 más suscripción anual
de MXN 10,788
        ↓ 60%
198 establecimientos
```


### Universo SAM

**SAM:** **198 establecimientos**.

### Valor anual del SAM

| Componente | Cálculo | Valor |
| :-- | --: | --: |
| Hardware inicial | 198 × MXN 6,940 | **MXN 1,374,120** |
| Suscripción año 1 | 198 × MXN 10,788 | **MXN 2,136,024** |
| **Valor total año 1** | Hardware + software | **MXN 3,510,144** |
| **ARR posterior** | 198 × MXN 10,788 | **MXN 2,136,024** |

Este SAM es considerablemente más atractivo que el cálculo anterior porque el software se cobra como herramienta B2B por sede y el hardware se vende en paquetes de tres y seis unidades.

______________________________________________________________________

# SOM — Mercado Obtenible, años 1–2

## Meta

**Meta base:** 45 gimnasios o estudios pagadores al cierre del segundo año.

**Porcentaje del SAM:**

$$
45 / 198 = 22.7\%
$$

La proporción es alta en relación con el SAM, pero el SAM ya está restringido a cinco ciudades, clientes accesibles y establecimientos con capacidad de compra.

## Lógica de go-to-market

- **Año 1:** CDMX y Estado de México.
- **Año 2:** Guadalajara y Monterrey; Puebla como mercado de prospección digital.
- **Equipo comercial:** dos personas dedicadas a demostraciones y ventas.
- **Demostraciones:** 8–10 por vendedor por semana.
- **Conversión objetivo:** 5–8% de demostración calificada a cliente pagador.
- **Canal primario:** demostraciones en clases de funcional, HIIT, CrossFit y preparación física.
- **Canal secundario:** coaches reconocidos, distribuidores de equipo funcional y alianzas con boxes.
- **Oferta de entrada:** paquete Studio de 6 unidades a MXN 7,990, con primer mes de software incluido.
- **Retención:** el cliente debe realizar al menos cuatro sesiones mensuales con Lumetriq y usar rankings o retos internos.

Una trayectoria razonable sería:


| Periodo | Clientes nuevos | Clientes acumulados |
| :-- | --: | --: |
| Año 1 | 15 | 15 |
| Año 2 | 30 | 45 |
| **Total** | **45** | **45** |

## Valor anual del SOM

| Componente | Cálculo | Valor |
| :-- | --: | --: |
| Hardware inicial | 45 × MXN 6,940 | **MXN 312,300** |
| Suscripción año 1 | 45 × MXN 10,788 | **MXN 485,460** |
| **Ingresos de primera compra** | Hardware + software | **MXN 797,760** |
| **ARR posterior** | 45 × MXN 10,788 | **MXN 485,460** |

Estos valores suponen que los 45 clientes pagan el plan Studio Pro durante un año completo. En la práctica, los ingresos de los años 1 y 2 serán menores si los clientes se incorporan gradualmente.

Una estimación más realista del flujo del segundo año sería:

- 15 clientes captados en el año 1, con renovación: MXN 161,820 de software.
- 30 clientes nuevos en el año 2: MXN 323,640 de software.
- Hardware de 30 clientes nuevos: MXN 208,200.
- Ingresos aproximados del año 2: **MXN 693,660**, antes de impuestos, devoluciones, comisiones y costos de soporte.

______________________________________________________________________

# SEÑAL DE VIABILIDAD

**SOM × precio anual = MXN 797,760 de ingresos de primera compra para 45 clientes.**

**¿Cubre costos operativos básicos de una startup de cuatro personas? Marginal, pero todavía no con suficiente seguridad.**

La situación mejora sustancialmente frente al precio anterior, pero MXN 797,760 de ingresos brutos acumulados de primera compra no equivale a utilidad. Si los costos de hardware, ventas, soporte y desarrollo consumen una parte relevante del ingreso, probablemente no financia cuatro salarios durante dos años.

La oportunidad se vuelve más viable bajo una de estas condiciones:

- Llegar a **75–100 gimnasios**.
- Aumentar la suscripción Studio Pro a **MXN 1,199–1,499 mensuales**.
- Vender paquetes premium con 12 unidades.
- Cobrar instalación, capacitación o contenido premium.
- Conseguir clientes corporativos, academias deportivas o cadenas.
- Mantener una tasa de renovación superior a 80%.
- Utilizar la suscripción como ingreso principal y no como accesorio del hardware.


### Precio recomendado para validar

El paquete inicial que probaría en entrevistas y preventa sería:

- **Lumetriq Starter, 3 unidades:** MXN 4,490.
- **Lumetriq Studio, 6 unidades:** MXN 7,990.
- **App individual Pro:** MXN 149 mensuales o MXN 1,290 anuales.
- **App gimnasio Studio Pro:** MXN 899 mensuales o MXN 8,990 anuales.
- **Primer año del gimnasio:** hardware más suscripción anual, aproximadamente **MXN 16,980** para el paquete de seis unidades.

El precio de MXN 16,980 por el primer año está muy por debajo de paquetes profesionales de FITLIGHT y BlazePod, pero permite probar si el cliente valora la solución como herramienta de clases y no solo como dispositivo barato.

## Riesgo principal

El mercado comparable demuestra que existe espacio para cobrar miles de pesos por un sistema de reacción, pero no demuestra que un gimnasio mexicano pagará automáticamente ese precio por Lumetriq. La validación debe medir:

1. Si el cliente compra tres o seis unidades.
2. Si acepta MXN 7,990 antes de probar el producto.
3. Si sigue pagando MXN 899 después del primer mes.
4. Si usa la app en suficientes clases para justificar el gasto.
5. Si el dueño percibe aumento en retención, diferenciación o ingresos por clase.

El primer experimento comercial debería ofrecer una preventa de **10 paquetes Studio a MXN 6,990**, con 90 días de acceso a la aplicación y renovación posterior a MXN 899 mensuales. Si menos de tres de diez prospectos calificados aceptan, el problema probablemente será de valor percibido o segmento, no de tamaño de mercado.

<span style="display:none">[^2_14][^2_15][^2_16][^2_17][^2_18][^2_19][^2_20][^2_21][^2_22][^2_23][^2_24][^2_25][^2_26][^2_27][^2_28][^2_29][^2_30][^2_31][^2_32][^2_33][^2_34][^2_35][^2_36][^2_37][^2_38][^2_39][^2_40][^2_41][^2_42][^2_43][^2_44][^2_45][^2_46][^2_47][^2_48][^2_49][^2_50][^2_51][^2_52][^2_53][^2_54][^2_55][^2_56][^2_57][^2_58][^2_59][^2_60][^2_61]</span>

<div align="center">⁂</div>

[^2_1]: https://www.blazepod.com/products/single-product

[^2_2]: https://www.blazepod.com/collections/bundles

[^2_3]: https://www.fitlighttraining.com/products/fitlight-system

[^2_4]: https://www.fitlighttraining.com/products/fitlight®-soccer-pack

[^2_5]: https://www.football4football.com/football-equipment/rox-pro-review-equipment-research

[^2_6]: https://perform-better.de/en/BlazePod-Trainer-Kit/A07268

[^2_7]: https://blazepod.eu/pages/membership

[^2_8]: https://us.fitgap.com/products/022817/trainheroic

[^2_9]: https://www.trainheroic.com/coach/

[^2_10]: https://www.banxico.org.mx/tipcamb/tipCamMIAction.do?idioma=sp

[^2_11]: https://apps.apple.com/mx/app/strava-run-bike-hike/id426826309?l=en-GB

[^2_12]: https://www.inegi.org.mx/contenidos/saladeprensa/boletines/2026/denue/DENUE2026_05.pdf

[^2_13]: https://www.inegi.org.mx/rnm/index.php/catalog/1103/data-dictionary/F10

[^2_14]: https://apps.apple.com/om/app/blazepod/id1382204042

[^2_15]: https://apps.apple.com/ca/app/blazepod/id1382204042

[^2_16]: https://apps.apple.com/nz/app/blazepod/id1382204042

[^2_17]: https://apps.apple.com/py/app/blazepod/id1382204042

[^2_18]: https://apps.apple.com/co/app/rox-pro-trainer/id6757195734?l=en-GB

[^2_19]: https://play.google.com/store/apps/details?id=co.blazepod.blazepod\&hl=en_US

[^2_20]: https://perform-better.de/en/Shop/Top-brands/BlazePod/

[^2_21]: https://squashchamps.com/article/alternatives-to-blazepod-for-squash-training

[^2_22]: https://www.blazepod.com/collections

[^2_23]: https://perform-better.de/en/Shop/Functional/Athletic-Equipment/

[^2_24]: https://www.fitlighttraining.com/pages/the-fitlight-app

[^2_25]: https://truesportsvibes.com/best-blazepod-alternatives-for-athletes-in-2026/

[^2_26]: https://www.fitlighttraining.com/products/fitlight®-sports-vision-package

[^2_27]: https://www.fitlighttraining.com/products/fitlight®-basketball-pack

[^2_28]: https://www.fitlighttraining.com/

[^2_29]: https://www.blazepod.com/collections/all

[^2_30]: https://www.blazepod.com/

[^2_31]: https://www.fitlighttraining.com/products/fitlight

[^2_32]: https://www.blazepod.com/en-intl/collections/shop-page

[^2_33]: https://www.fitlighttraining.com/collections

[^2_34]: https://www.blazepod.com/collections/product

[^2_35]: https://get.blazepod.com/build-your-own

[^2_36]: https://www.banxico.org.mx/tipcamb/llenarTiposCambioAction.do?idioma=sp

[^2_37]: https://www.wsj.com/market-data/quotes/fx/USDMXN/historical-prices

[^2_38]: https://finance.yahoo.com/quote/USDMXN=X/history/

[^2_39]: https://finance.yahoo.com/quote/MXN=X/history/

[^2_40]: https://www.milenio.com/negocios/precio-del-dolar-hoy-9-septiembre-2026-a-cuanto-cotiza-en-vivo-atm

[^2_41]: https://www.milenio.com/negocios/precio-del-dolar-hoy-21-septiembre-2026-a-cuanto-cotiza-en-vivo-atm

[^2_42]: https://www.investing.com/currencies/usd-mxn-historical-data

[^2_43]: https://www.razon.com.mx/negocios/2026/09/21/este-es-el-precio-del-dolar-hoy-lunes-21-de-septiembre-de-2026/

[^2_44]: https://www.milenio.com/negocios/precio-del-dolar-hoy-22-septiembre-2026-a-cuanto-cotiza-en-vivo-atm

[^2_45]: https://tradingeconomics.com/mexico/currency

[^2_46]: https://www.milenio.com/negocios/precio-del-dolar-hoy-14-septiembre-2026-a-cuanto-cotiza-en-vivo-atm

[^2_47]: https://www.mibolsillo.com/noticias/peso-mexicano-mantiene-su-valor-asi-esta-el-precio-del-dolar-hoy-10-de-septiembre-de-2026-20260910-0004.html

[^2_48]: https://www.razon.com.mx/negocios/2026/09/17/este-es-el-precio-del-dolar-hoy-jueves-17-de-septiembre-de-2026/

[^2_49]: https://www.pesomxn.com/dolar-a-peso/banco-de-mexico-fix

[^2_50]: https://apps.apple.com/mx/app/strava-run-bike-walk/id426826309?l=en-GB

[^2_51]: https://www.guideflow.com/blog/personal-trainer-app

[^2_52]: https://wellhub.com/es-mx/plans-pricing/

[^2_53]: https://www.fitbudd.com/post/how-much-does-trainheroic-costs

[^2_54]: https://support.trainheroic.com/hc/en-us/articles/18156702444301-What-s-the-difference-between-a-Coach-Plan-and-selling-through-the-Marketplace

[^2_55]: https://support.trainheroic.com/hc/en-us/articles/18156776017677-FAQs-General-Questions-for-Prospective-Coaches

[^2_56]: https://marketplace.trainheroic.com/

[^2_57]: https://support.trainheroic.com/hc/en-us/articles/18156821768845-How-can-I-upgrade-downgrade-or-change-my-Coach-Plan

[^2_58]: https://www.ptpioneer.com/personal-training/tools/train-heroic-review/

[^2_59]: https://www.teambuildr.com/trainheroic-vs-teambuildr

[^2_60]: https://coachbox.app/en/compare/trainheroic-pricing/

[^2_61]: https://www.trainerstudio.com/en/comparison/truecoach-vs-trainheroic


---

# Estructura la respuesta como te lo solicité en el primer prompt

════════════════════════════════════════════════════════

# DIMENSIONAMIENTO DE MERCADO

**Concepto:** Lumetriq\
**Mercado inicial:** México\
**Horizonte SOM:** años 1–2\
════════════════════════════════════════════════════════

## Supuestos de precio

El costo de producción informado es **MXN 500–600 por dispositivo**. Para el cálculo uso un costo medio de **MXN 550**, sin asumir que incluya empaque, garantía, control de calidad, logística, impuestos o soporte.

Los comparables confirman que estos productos se venden como sistemas, no como unidades aisladas. BlazePod ofrece un kit inicial de cuatro pods con base de carga y estuche; sus bundles publicados van aproximadamente de USD 576 a USD 1,352. FITLIGHT publica un sistema en USD 749 con aplicación sin suscripción y capacidad de ampliar hasta 32 luces.[^3_1][^3_2][^3_3]

La aplicación de BlazePod tiene una versión gratuita y una versión Pro de aproximadamente USD 9.99 mensuales o USD 99.99 anuales durante el primer año; posteriormente, el precio publicado sube a aproximadamente USD 14.99 mensuales o USD 149.99 anuales. FITLIGHT, en contraste, comunica una aplicación sin cuotas de suscripción.[^3_3][^3_4]

### Precio hipotético de Lumetriq

| Producto | Contenido | Precio propuesto |
| :-- | --: | --: |
| Lumetriq Starter | 3 dispositivos, carga y accesorios básicos | **MXN 4,490** |
| Lumetriq Studio | 6 dispositivos, estación de carga, estuche y accesorios | **MXN 7,990** |
| App individual Free | Funciones básicas | **MXN 0** |
| App individual Pro | Rutinas, historial, personalización y rankings | **MXN 149/mes** o **MXN 1,290/año** |
| App gimnasio Studio Basic | Una sede, hasta 3 coaches, funciones operativas | **MXN 499/mes** o **MXN 4,990/año** |
| App gimnasio Studio Pro | Clases grupales, rankings, reportes y coaches ilimitados | **MXN 899/mes** o **MXN 8,990/año** |

Para el dimensionamiento se utiliza el siguiente caso base:

- **70% de los clientes compra Lumetriq Studio de 6 dispositivos:** MXN 7,990.
- **30% compra Lumetriq Starter de 3 dispositivos:** MXN 4,490.
- **Precio promedio ponderado de hardware:** MXN 6,940.
- **Suscripción B2B utilizada:** MXN 899 mensuales, o MXN 10,788 anuales.
- **Valor del primer año por cliente promedio:** MXN 17,728.

El precio de MXN 899 mensuales se justifica porque la licencia es por sede y puede utilizarse en clases grupales con varios atletas, no por un solo usuario. Debe validarse comercialmente: no existe una fuente pública que mida la disposición de pago de gimnasios mexicanos por este producto específico.

______________________________________________________________________

# TAM — Mercado Total Direccionable

**Universo de partida:** 30,242 establecimientos privados de acondicionamiento físico en México. Esta cifra se mantiene como escenario provisional y debe validarse mediante una extracción del DENUE filtrada por la clase SCIAN 713943. El DENUE 05/2026 reporta 6,138,075 establecimientos totales y permite filtrar por actividad económica, ubicación y tamaño.[^3_5][^3_6]

```text
30,242 establecimientos privados
        ↓ Filtro: realizan entrenamiento presencial
18,145 · 60% del universo
        Fuente: supuesto de primer principio; no existe un porcentaje
        público específico para este filtro
        ↓ Filtro: ofrecen HIIT, funcional, CrossFit,
        combate, atletismo o clases de alta intensidad
8,165 · 45% de los anteriores
        Fuente: supuesto de primer principio
        ↓ Filtro: el sistema de luces tiene aplicación
        práctica en su operación
4,899 · 60% de los anteriores
        Fuente: supuesto de primer principio
        ↓ Filtro: aceptarían invertir en hardware de
        MXN 4,490–7,990 y software de MXN 8,990–10,788 anuales
1,715 · 35% de los anteriores
        Fuente: hipótesis de disposición de pago;
        requiere validación con entrevistas y preventas
```


## Universo final TAM

**TAM:** **1,715 establecimientos compradores potenciales**.

El TAM no representa todos los gimnasios con atletas o clientes activos. Representa los establecimientos que, bajo los filtros anteriores, podrían comprar tanto el sistema físico como la aplicación B2B.

### Valor anual del TAM

| Componente | Cálculo | Valor |
| :-- | --: | --: |
| Venta inicial de hardware | 1,715 × MXN 6,940 | **MXN 11,902,100** |
| Suscripción del primer año | 1,715 × MXN 10,788 | **MXN 18,505,420** |
| **Valor del primer año** | Hardware + suscripción | **MXN 30,407,520** |
| **Ingreso recurrente anual posterior** | 1,715 × MXN 10,788 | **MXN 18,505,420** |

**Valor anual TAM:** **MXN 18,505,420 de ingresos recurrentes**, más aproximadamente **MXN 11,902,100 de hardware en el año de adquisición**.

______________________________________________________________________

# SAM — Mercado Alcanzable

El SAM se reduce al subconjunto que Lumetriq puede atender con el modelo actual: venta directa, soporte en español, demostraciones presenciales, distribución inicial limitada y operación en ciudades con suficiente concentración de gimnasios.

## Filtros aplicados al TAM

```text
TAM: 1,715 establecimientos
        ↓ Filtro geográfico: CDMX, Estado de México,
        Guadalajara, Monterrey y Puebla
943 · 55% del TAM
        ↓ Filtro: tienen clases grupales recurrentes
        y capacidad de comprar equipo profesional
472 · 50% de los anteriores
        ↓ Filtro: son accesibles por venta directa,
        coaches, redes sociales o distribuidores
330 · 70% de los anteriores
        ↓ Filtro: aceptan un ticket inicial promedio
        de MXN 6,940 y suscripción anual de MXN 10,788
198 · 60% de los anteriores
```


## Universo SAM

**SAM:** **198 establecimientos**.

### Reducciones específicas del SAM

- **Geografía:** solo cinco mercados urbanos mexicanos.
- **Canal:** venta directa, demostraciones, Instagram, WhatsApp, coaches y distribuidores especializados.
- **Precio:** se excluyen negocios que no puedan pagar aproximadamente MXN 7,000 de hardware y MXN 899 mensuales.
- **Idioma:** producto, soporte y contenido inicialmente en español.
- **Tamaño mínimo:** se requieren clases grupales o múltiples atletas para que el gimnasio capture valor suficiente.
- **Operación:** se excluyen instalaciones con uso ocasional, sin entrenador responsable o sin espacio para montar los dispositivos.
- **Modelo:** se excluyen usuarios domésticos y atletas individuales del SAM B2B.


### Valor anual del SAM

| Componente | Cálculo | Valor |
| :-- | --: | --: |
| Venta inicial de hardware | 198 × MXN 6,940 | **MXN 1,374,120** |
| Suscripción del primer año | 198 × MXN 10,788 | **MXN 2,136,024** |
| **Valor del primer año** | Hardware + suscripción | **MXN 3,510,144** |
| **Ingreso recurrente anual posterior** | 198 × MXN 10,788 | **MXN 2,136,024** |

**Valor anual SAM:** **MXN 2,136,024 recurrentes**, más **MXN 1,374,120 de hardware** en el año de adquisición.

______________________________________________________________________

# SOM — Mercado Obtenible (años 1–2)

## Meta

**Meta:** **45 gimnasios o estudios pagadores** al cierre del segundo año.

**Porcentaje del SAM:**

$$
45 \div 198 = 22.7\%
$$

La meta equivale al 22.7% del SAM definido, no al 22.7% de todos los gimnasios de México.

## Lógica de go-to-market

- **Año 1:** Ciudad de México y Estado de México.
- **Año 2:** Guadalajara y Monterrey; Puebla mediante prospección digital y alianzas.
- **Equipo comercial:** dos personas dedicadas a prospección, demostraciones y cierre.
- **Capacidad:** 8–10 demostraciones calificadas por vendedor por semana.
- **Conversión objetivo:** 5–8% de demostraciones calificadas a clientes pagadores.
- **Canal principal:** demostraciones dentro de clases de funcional, HIIT, CrossFit y preparación física.
- **Canal de confianza:** coaches, dueños de boxes y distribuidores de equipo funcional.
- **Oferta de entrada:** Lumetriq Studio de 6 dispositivos a MXN 7,990, con acceso de prueba a la app.
- **Adopción:** el cliente debe utilizar Lumetriq en al menos cuatro sesiones mensuales.
- **Expansión:** cada distribuidor o coach asociado debe aportar aproximadamente 5–8 clientes en el segundo año.


### Trayectoria propuesta

| Periodo | Clientes nuevos | Clientes acumulados |
| :-- | --: | --: |
| Año 1 | 15 | 15 |
| Año 2 | 30 | 45 |
| **Total años 1–2** | **45** | **45** |

## Valor anual del SOM

| Componente | Cálculo | Valor |
| :-- | --: | --: |
| Venta inicial de hardware | 45 × MXN 6,940 | **MXN 312,300** |
| Suscripción del primer año | 45 × MXN 10,788 | **MXN 485,460** |
| **Valor del primer año** | Hardware + suscripción | **MXN 797,760** |
| **Ingreso recurrente anual al llegar a 45 clientes** | 45 × MXN 10,788 | **MXN 485,460** |

Si los 45 clientes se adquieren gradualmente, el ingreso efectivo del año 2 será menor que MXN 797,760 porque no todos pagarán doce meses completos. Bajo una trayectoria de 15 clientes en el año 1 y 30 clientes nuevos en el año 2, el ingreso aproximado del año 2 sería:

- Renovación de 15 clientes: MXN 161,820.
- Suscripción de 30 clientes nuevos: MXN 323,640.
- Hardware de 30 clientes nuevos: MXN 208,200.
- **Ingresos estimados del año 2:** aproximadamente **MXN 693,660**, antes de impuestos, comisiones, devoluciones y costos operativos.

______________________________________________________________________

# SEÑAL DE VIABILIDAD

**SOM × precio anual = MXN 797,760 de ingresos de primera compra para 45 clientes.**

**¿Cubre costos operativos básicos de una startup de 4 personas? Marginal.**

El precio revisado mejora de forma importante el modelo: el negocio ya no depende de vender unidades a MXN 500–600, sino paquetes de tres y seis dispositivos y una licencia B2B por sede. Sin embargo, MXN 797,760 de ingresos brutos del primer año para 45 clientes todavía probablemente no cubre cuatro salarios, inventario, desarrollo de app, ventas, soporte, garantía y logística.

La señal sería más sólida con cualquiera de estas metas:

- 75–100 sedes activas.
- Suscripción Pro de MXN 1,199–1,499 mensuales.
- Paquete premium de 12 dispositivos.
- Venta de capacitación, instalación y contenido.
- Contratos con cadenas, academias o centros de alto rendimiento.
- Renovación anual superior a 80%.
- Margen bruto de hardware superior a 45%.

El precio inicial recomendado para validación comercial es:

- **Starter de 3 dispositivos:** MXN 4,490.
- **Studio de 6 dispositivos:** MXN 7,990.
- **App individual Pro:** MXN 149 mensuales o MXN 1,290 anuales.
- **App gimnasio Studio Pro:** MXN 899 mensuales o MXN 8,990 anuales.
- **Ticket promedio del primer año:** aproximadamente **MXN 17,728 por establecimiento**, incluyendo hardware y software.

════════════════════════════════════════════════════════

# FUENTES UTILIZADAS

- **INEGI, DENUE 05/2026.** Reporta 6,138,075 establecimientos en México y permite analizar ubicación, actividad económica y tamaño.[^3_5]
- **INEGI, documentación del DENUE.** Describe el directorio como fuente para identificar unidades económicas activas por actividad y localización.[^3_6]
- **BlazePod, Starter Kit y Bundles, 2024–2026.** Confirma la venta en paquetes con pods, base de carga y estuche; sus bundles publicados se encuentran aproximadamente entre USD 576 y USD 1,352.[^3_2][^3_1]
- **BlazePod / Perform Better, información de membresía.** Reporta acceso gratuito y planes Pro de aproximadamente EUR 9.99 mensuales o EUR 99.99 anuales el primer año, con incremento posterior a EUR 14.99 mensuales o EUR 149.99 anuales.[^3_4]
- **FITLIGHT, FITLIGHT System, 2025–2026.** Publica un sistema de USD 749 con aplicación sin suscripción y expansión hasta 32 luces.[^3_3]
- **Apple App Store, BlazePod.** Muestra referencias de suscripción de USD 12.99 mensuales, USD 99.99 anuales, USD 14.99 mensuales y USD 149.99 anuales, según el plan y mercado.[^3_7]
- **Banco de México, tipo de cambio FIX.** Referencia de aproximadamente MXN 17.64 por USD para septiembre de 2026.[^3_8]

<span style="display:none">[^3_10][^3_11][^3_12][^3_13][^3_14][^3_15][^3_16][^3_17][^3_18][^3_9]</span>

<div align="center">⁂</div>

[^3_1]: https://www.blazepod.com/products/starter-kit

[^3_2]: https://www.blazepod.com/collections/bundles

[^3_3]: https://www.fitlighttraining.com/products/fitlight-system

[^3_4]: https://perform-better.de/en/Product-categories/Measuring-devices/

[^3_5]: https://www.inegi.org.mx/contenidos/saladeprensa/boletines/2026/denue/DENUE2026_05.pdf

[^3_6]: https://www.inegi.org.mx/rnm/index.php/catalog/1103/data-dictionary/F10

[^3_7]: https://apps.apple.com/us/app/blazepod/id1382204042

[^3_8]: https://www.banxico.org.mx/tipcamb/tipCamMIAction.do?idioma=sp

[^3_9]: https://www.rox.com/pricing

[^3_10]: https://www.blazepod.com/products/certified-refurbished-starter-kit

[^3_11]: https://fitlight.odoo.com/en

[^3_12]: https://www.smeincusa.com/BlazePod-Starter-Kit

[^3_13]: https://www.shuttlesystems.com/products/blazepod-trainer-kit-copy

[^3_14]: https://get.blazepod.com/build-your-own

[^3_15]: https://www.fitlighttraining.com/

[^3_16]: https://www.blazepod.com/products/single-product

[^3_17]: https://www.fitlighttraining.com/products/fitlight®-basketball-pack

[^3_18]: https://www.fitlighttraining.com/pages/the-fitlight-app


---

# FORMATO DE SALIDA:

════════════════════════════════════════════════════════
DIMENSIONAMIENTO DE MERCADO
Concepto: [nombre]
════════════════════════════════════════════════════════
TAM — Mercado Total Direccionable
Universo de partida: [n° y descripción]

↓ Filtro $$
descripción
$$: [n° resultante] · Fuente: [nombre]

↓ Filtro $$
descripción
$$: [n° resultante] · Fuente: [nombre]

Universo final TAM: [n° personas o negocios]

Valor anual: $$
$ MXN] · Supuesto de precio: [$ por usuario/año
$$

SAM — Mercado Alcanzable
Filtros aplicados al TAM:

· $$
filtro
$$: reduce a [n°]

· $$
filtro
$$: reduce a [n°]

Universo SAM: [n°]

Valor anual: $$
$ MXN]
SOM — Mercado Obtenible (años 1–2)
Meta: [n° clientes]
Porcentaje del SAM: [%]
Lógica de go-to-market:
· [canal específico]
· [geografía piloto]
· [capacidad del equipo]
Valor anual: [$ MXN
$$

────────────────────────────────────────────────────────
SEÑAL DE VIABILIDAD:
SOM × precio anual = [\$ MXN]
¿Cubre costos operativos básicos de una startup de 4 personas?
Sí / No / Marginal — [1 oración de justificación]
FUENTES UTILIZADAS:
· [fuente 1 con año]
· [fuente 2 con año]
════════════════════════════════════════════════════════

════════════════════════════════════════════════════════

# DIMENSIONAMIENTO DE MERCADO

**Concepto:** Lumetriq\
════════════════════════════════════════════════════════

# TAM — Mercado Total Direccionable

**Universo de partida:** 30,242 establecimientos privados de acondicionamiento físico en México. Es un escenario provisional que debe validarse extrayendo del DENUE los establecimientos de la clase SCIAN 713943. El DENUE 05/2026 reporta 6,138,075 establecimientos totales y permite filtrarlos por actividad, ubicación y tamaño.[^4_1][^4_2]

↓ **Filtro entrenamiento presencial:** 18,145 establecimientos · **Fuente:** supuesto de primer principio; no existe un porcentaje público específico para este filtro.

↓ **Filtro afinidad con HIIT, funcional, CrossFit, combate, atletismo o clases de alta intensidad:** 8,165 establecimientos · **Fuente:** supuesto de primer principio.

↓ **Filtro utilidad del sistema de luces en clases grupales o sesiones de entrenamiento:** 4,899 establecimientos · **Fuente:** supuesto de primer principio.

↓ **Filtro disposición de pago por un paquete de hardware de MXN 4,490–7,990 y software B2B:** 1,715 establecimientos · **Fuente:** hipótesis de disposición de pago; requiere validación mediante entrevistas, pilotos y preventas.

**Universo final TAM:** **1,715 establecimientos compradores potenciales**

**Supuesto de producto:**

- 70% compra Lumetriq Studio: 6 dispositivos por MXN 7,990.
- 30% compra Lumetriq Starter: 3 dispositivos por MXN 4,490.
- Precio promedio ponderado de hardware: **MXN 6,940**.
- Suscripción para gimnasio Studio Pro: **MXN 899 mensuales o MXN 10,788 anuales**.
- Ticket promedio del primer año: **MXN 17,728 por establecimiento**.

**Valor anual:** **MXN 30,407,520 durante el primer año**\
**Supuesto de precio:** **MXN 10,788 por establecimiento/año de software + MXN 6,940 de hardware inicial**

Desglose:

- Hardware inicial: 1,715 × MXN 6,940 = **MXN 11,902,100**.
- Suscripción anual: 1,715 × MXN 10,788 = **MXN 18,505,420**.
- Ingreso recurrente anual posterior: **MXN 18,505,420**.

______________________________________________________________________

# SAM — Mercado Alcanzable

**Filtros aplicados al TAM:**

- **Geografía inicial:** CDMX, Estado de México, Guadalajara, Monterrey y Puebla; reduce a **943 establecimientos**.
- **Operación grupal:** al menos una clase grupal recurrente y capacidad de comprar equipo profesional; reduce a **472**.
- **Accesibilidad comercial:** contacto mediante venta directa, redes sociales, coaches o distribuidores; reduce a **330**.
- **Capacidad de pago:** aceptación de un paquete promedio de MXN 6,940 y suscripción anual de MXN 10,788; reduce a **198**.

**Universo SAM:** **198 establecimientos**

**Valor anual:** **MXN 3,510,144 durante el primer año**

Desglose:

- Hardware inicial: 198 × MXN 6,940 = **MXN 1,374,120**.
- Suscripción anual: 198 × MXN 10,788 = **MXN 2,136,024**.
- Ingreso recurrente anual posterior: **MXN 2,136,024**.

El SAM excluye gimnasios públicos, cadenas con procesos de compra corporativos, centros sin clases grupales, usuarios domésticos, atletas individuales y establecimientos que solo aceptarían una aplicación gratuita.

______________________________________________________________________

# SOM — Mercado Obtenible (años 1–2)

**Meta:** **45 gimnasios o estudios pagadores**

**Porcentaje del SAM:** **22.7%**

**Lógica de go-to-market:**

- **Canal específico:** demostraciones presenciales en clases de funcional, HIIT, CrossFit y preparación física; prospección por Instagram, WhatsApp y alianzas con coaches y distribuidores de equipo funcional.
- **Geografía piloto:** CDMX y Estado de México durante el primer año; Guadalajara y Monterrey en el segundo año; Puebla mediante prospección digital.
- **Capacidad del equipo:** dos personas en ventas y demostraciones, con 8–10 demostraciones calificadas por vendedor por semana y una conversión objetivo de 5–8%.
- **Oferta comercial:** Lumetriq Studio de 6 dispositivos a MXN 7,990, con acceso de prueba a la aplicación y renovación posterior a MXN 899 mensuales.
- **Trayectoria:** 15 clientes durante el año 1 y 30 clientes nuevos durante el año 2, para llegar a 45 clientes acumulados.

**Valor anual:** **MXN 797,760 de ingresos del primer año para 45 clientes**

Desglose:

- Hardware inicial: 45 × MXN 6,940 = **MXN 312,300**.
- Suscripción anual: 45 × MXN 10,788 = **MXN 485,460**.
- Ingreso recurrente anual al alcanzar 45 clientes: **MXN 485,460**.

Si los clientes se adquieren gradualmente, el ingreso real del año 2 sería aproximadamente **MXN 693,660**, considerando renovaciones, nuevas suscripciones y hardware de los clientes nuevos.

────────────────────────────────────────────────────────

# SEÑAL DE VIABILIDAD:

**SOM × precio anual = MXN 797,760 de ingresos brutos de primera compra**

**¿Cubre costos operativos básicos de una startup de 4 personas?**

**Marginal** — El precio revisado mejora el modelo, pero 45 clientes todavía probablemente no cubren cuatro salarios, desarrollo de app, inventario, ventas, soporte, garantía y logística.

Para una operación más sólida, Lumetriq debería alcanzar aproximadamente 75–100 sedes, aumentar el plan B2B a MXN 1,199–1,499 mensuales, vender paquetes de 12 dispositivos o agregar instalación, capacitación y contenido premium.

El precio hipotético recomendado es:

- **Lumetriq Starter, 3 dispositivos:** MXN 4,490.
- **Lumetriq Studio, 6 dispositivos:** MXN 7,990.
- **App individual Pro:** MXN 149 mensuales o MXN 1,290 anuales.
- **App gimnasio Studio Pro:** MXN 899 mensuales o MXN 8,990 anuales.
- **Ticket promedio del primer año por gimnasio:** aproximadamente MXN 17,728.


# FUENTES UTILIZADAS:

- **INEGI, DENUE 05/2026.** Reporta 6,138,075 establecimientos y permite analizarlos por actividad, ubicación y tamaño.[^4_1]
- **INEGI, documentación del DENUE, 2025–2026.** Define el directorio como fuente para identificar unidades económicas activas.[^4_2]
- **BlazePod, Starter Kit y Bundles, 2024–2026.** Referencia de paquetes de dispositivos, accesorios y precios internacionales.[^4_3][^4_4]
- **BlazePod / Perform Better, membresía de la aplicación, 2026.** Referencia de planes gratuitos y Pro.[^4_5]
- **FITLIGHT, FITLIGHT System, 2025–2026.** Referencia de sistema profesional y aplicación sin suscripción.[^4_6]
- **Banco de México, tipo de cambio FIX, 24 de septiembre de 2026.** Utilizado para convertir referencias internacionales a pesos mexicanos.[^4_7]

════════════════════════════════════════════════════════

<div align="center">⁂</div>

[^4_1]: https://www.inegi.org.mx/contenidos/saladeprensa/boletines/2026/denue/DENUE2026_05.pdf

[^4_2]: https://www.inegi.org.mx/rnm/index.php/catalog/1103/data-dictionary/F10

[^4_3]: https://www.blazepod.com/products/starter-kit

[^4_4]: https://www.blazepod.com/collections/bundles

[^4_5]: https://perform-better.de/en/Product-categories/Measuring-devices/

[^4_6]: https://www.fitlighttraining.com/products/fitlight-system

[^4_7]: https://www.banxico.org.mx/tipcamb/tipCamMIAction.do?idioma=sp


---

# Reduce el precio de los dispositivos, es muy caro 7,990.

════════════════════════════════════════════════════════

# DIMENSIONAMIENTO DE MERCADO

**Concepto:** Lumetriq\
════════════════════════════════════════════════════════

## Ajuste de precio del hardware

El precio de **MXN 7,990 por seis dispositivos** puede ser demasiado alto para gimnasios boutique, boxes pequeños y estudios HIIT. Aunque los competidores internacionales venden sistemas profesionales a precios superiores, Lumetriq puede competir con una estrategia de entrada más accesible y todavía mantener margen sobre el costo de producción estimado de MXN 500–600 por unidad. BlazePod, por ejemplo, comercializa kits de seis pods para entrenadores y clientes profesionales, pero su precio internacional incorpora marca, accesorios, distribución y posicionamiento premium.[^5_1]

### Precio propuesto

| Paquete | Contenido | Costo de producción estimado | Precio anterior | Precio revisado |
| :-- | --: | --: | --: | --: |
| Lumetriq Starter | 3 dispositivos | MXN 1,650 | MXN 4,490 | **MXN 2,990** |
| Lumetriq Studio | 6 dispositivos | MXN 3,300 | MXN 7,990 | **MXN 4,990** |

El precio de **MXN 4,990 por seis dispositivos** equivale a aproximadamente **MXN 832 por dispositivo**, dejando un margen bruto preliminar de alrededor de 34% frente al costo de producción de MXN 550 por unidad.

Este margen es más limitado que el de la propuesta anterior, pero puede facilitar la adopción inicial. No incluye todavía empaque, garantía, logística, comisiones ni costos de adquisición de clientes.

### Suscripciones

| Plan | Precio propuesto |
| :-- | --: |
| App individual Free | MXN 0 |
| App individual Pro | MXN 99/mes o MXN 990/año |
| App gimnasio Basic | MXN 299/mes o MXN 2,990/año |
| App gimnasio Pro | MXN 499/mes o MXN 4,990/año |

Para el dimensionamiento usaré:

- **Hardware promedio ponderado:** MXN 4,390.
- **Suscripción gimnasio Pro:** MXN 499 mensuales.
- **Suscripción anual:** MXN 5,988.
- **Ticket promedio del primer año:** MXN 10,378.

El hardware promedio se calcula suponiendo:

- 70% de los clientes compra el paquete Studio de MXN 4,990.
- 30% compra el paquete Starter de MXN 2,990.

$$
(70\% \times 4,990) + (30\% \times 2,990)
= MXN\ 4,390
$$

______________________________________________________________________

# TAM — Mercado Total Direccionable

**Universo de partida:** 30,242 establecimientos privados de acondicionamiento físico en México. Es un escenario provisional que debe validarse mediante una extracción del DENUE filtrada por la clase SCIAN 713943. El DENUE 05/2026 reporta 6,138,075 establecimientos totales y permite filtrarlos por actividad, ubicación y tamaño.[^5_2][^5_3]

↓ **Filtro entrenamiento presencial:** 18,145 establecimientos · **Fuente:** supuesto de primer principio; no existe un porcentaje público específico para este filtro.

↓ **Filtro afinidad con HIIT, funcional, CrossFit, combate, atletismo o clases de alta intensidad:** 8,165 establecimientos · **Fuente:** supuesto de primer principio.

↓ **Filtro utilidad del sistema de luces en clases grupales o sesiones de entrenamiento:** 4,899 establecimientos · **Fuente:** supuesto de primer principio.

↓ **Filtro disposición de pago por hardware de MXN 2,990–4,990 y software de MXN 4,990–5,988 anuales:** 1,715 establecimientos · **Fuente:** hipótesis de disposición de pago; requiere validación comercial.

**Universo final TAM:** **1,715 establecimientos compradores potenciales**

**Valor anual:** **MXN 17,797,070 durante el primer año**\
**Supuesto de precio:** **MXN 5,988 por establecimiento/año de software + MXN 4,390 de hardware inicial**

Desglose:

- Hardware inicial: 1,715 × MXN 4,390 = **MXN 7,528,850**.
- Suscripción anual: 1,715 × MXN 5,988 = **MXN 10,268,420**.
- Ingreso recurrente anual posterior: **MXN 10,268,420**.

______________________________________________________________________

# SAM — Mercado Alcanzable

**Filtros aplicados al TAM:**

- **Geografía inicial:** CDMX, Estado de México, Guadalajara, Monterrey y Puebla; reduce a **943 establecimientos**.
- **Operación grupal:** al menos una clase grupal recurrente y capacidad de comprar equipo; reduce a **472**.
- **Accesibilidad comercial:** venta directa, redes sociales, coaches o distribuidores; reduce a **330**.
- **Capacidad de pago:** aceptación de hardware promedio de MXN 4,390 y software anual de MXN 5,988; reduce a **198**.

**Universo SAM:** **198 establecimientos**

**Valor anual:** **MXN 2,054,844 durante el primer año**

Desglose:

- Hardware inicial: 198 × MXN 4,390 = **MXN 869,220**.
- Suscripción anual: 198 × MXN 5,988 = **MXN 1,185,624**.
- Ingreso recurrente anual posterior: **MXN 1,185,624**.

El SAM excluye gimnasios públicos, cadenas con compras corporativas, centros sin clases grupales, usuarios domésticos, atletas individuales y negocios que solo aceptarían una app gratuita.

______________________________________________________________________

# SOM — Mercado Obtenible (años 1–2)

**Meta:** **45 gimnasios o estudios pagadores**

**Porcentaje del SAM:** **22.7%**

**Lógica de go-to-market:**

- **Canal específico:** demostraciones presenciales en clases de funcional, HIIT, CrossFit y preparación física; prospección por Instagram, WhatsApp y alianzas con coaches.
- **Geografía piloto:** CDMX y Estado de México durante el año 1; Guadalajara y Monterrey durante el año 2.
- **Capacidad del equipo:** dos personas en ventas y demostraciones, con 8–10 demostraciones calificadas por vendedor por semana.
- **Oferta comercial:** paquete Studio de 6 dispositivos a MXN 4,990, con primer mes de aplicación incluido.
- **Conversión objetivo:** 5–8% de demostraciones calificadas a clientes pagadores.
- **Trayectoria:** 15 clientes nuevos en el año 1 y 30 clientes nuevos en el año 2.

**Valor anual:** **MXN 466,?** Wait calculate. 45*4,390=197,550; 45*5,988=269,460 total 467,010. Need avoid typo. Let's state.

Desglose:

- Hardware inicial: 45 × MXN 4,390 = **MXN 197,550**.
- Suscripción anual: 45 × MXN 5,988 = **MXN 269,460**.
- **Valor del primer año:** **MXN 467,010**.
- **Ingreso recurrente anual al alcanzar 45 clientes:** **MXN 269,460**.

────────────────────────────────────────────────────────

# SEÑAL DE VIABILIDAD:

**SOM × precio anual = MXN 467,010 de ingresos brutos de primera compra**

**¿Cubre costos operativos básicos de una startup de 4 personas?**

**No** — El menor precio facilita la adopción, pero con 45 clientes no alcanza para financiar cuatro salarios, producción, soporte, desarrollo de app y ventas.

El precio revisado es más adecuado para validar el producto porque reduce la barrera inicial:

- Paquete Starter de 3 dispositivos: **MXN 2,990**.
- Paquete Studio de 6 dispositivos: **MXN 4,990**.
- App individual Pro: **MXN 99 mensuales o MXN 990 anuales**.
- App gimnasio Pro: **MXN 499 mensuales o MXN 4,990 anuales**.

El riesgo es el margen. Si el costo real por dispositivo aumenta de MXN 550 a MXN 700–800 después de empaque, garantía y logística, el paquete de seis a MXN 4,990 dejaría poco margen para cubrir ventas y soporte. Por ello, el precio debe probarse junto con una meta de al menos **75–100 gimnasios activos** o una suscripción B2B superior posteriormente.

# FUENTES UTILIZADAS:

- **INEGI, DENUE 05/2026.** Reporta 6,138,075 establecimientos y permite analizarlos por actividad, ubicación y tamaño.[^5_2]
- **INEGI, documentación del DENUE, 2025–2026.** Fuente para identificar unidades económicas activas por actividad y localización.[^5_3]
- **BlazePod, Trainer Kit, 2024–2026.** Referencia de paquetes de seis pods destinados a entrenadores y clientes.[^5_1]
- **FITLIGHT, FITLIGHT System, 2025–2026.** Referencia internacional de sistemas profesionales de luces reactivas.[^5_4]
- **BlazePod / Perform Better, membresía de la aplicación, 2026.** Referencia de aplicación gratuita y plan Pro.[^5_5]

════════════════════════════════════════════════════════

<span style="display:none">[^5_10][^5_11][^5_12][^5_13][^5_14][^5_15][^5_16][^5_17][^5_18][^5_19][^5_6][^5_7][^5_8][^5_9]</span>

<div align="center">⁂</div>

[^5_1]: https://www.blazepod.com/blogs/all/finding-the-perfect-gifts-for-personal-trainers

[^5_2]: https://www.inegi.org.mx/contenidos/saladeprensa/boletines/2026/denue/DENUE2026_05.pdf

[^5_3]: https://www.inegi.org.mx/rnm/index.php/catalog/1103/data-dictionary/F10

[^5_4]: https://www.fitlighttraining.com/products/fitlight-system

[^5_5]: https://perform-better.de/en/Product-categories/Measuring-devices/

[^5_6]: https://www.blazepod.com/pages/training-hub/th-creator-9f4ogc2m

[^5_7]: https://www.amazon.com.mx/Kerbl-Pet-Light-Reflex-Luminoso/dp/B09HKD49QX

[^5_8]: https://www.blazepod.com/en-ca/pages/training-hub/innovault-basketball

[^5_9]: https://www.crunchbase.com/organization/roex

[^5_10]: https://directory.startupluxembourg.com/companies/roex_1

[^5_11]: https://www.blazepod.com/en-il/pages/training-hub/pegasus-project

[^5_12]: https://www.fancypets.mx/producto?prod_articulo=FL8556\&

[^5_13]: https://www.amazon.com.mx/s?rh=n:50603096011,p_n_g-1003197325111:24092605011

[^5_14]: https://www.amazon.com.mx/Iluminación-de-Emergencia/s?rh=n:12500364011,p_n_g-1003387276111:24221248011

[^5_15]: https://www.amazon.com.mx/Iluminación-de-Emergencia-2/s?rh=n:12500364011,p_n_feature_five_browse-bin:122265047011

[^5_16]: https://vaping360.com/reviews/new-product-releases-january-2026/

[^5_17]: https://www.amazon.com.mx/Barras-Luminosas-Emergencia/b?ie=UTF8\&node=211782565011

[^5_18]: https://www.roxmotor.com/

[^5_19]: https://www.amazon.com.mx/Pro-Track-Melson-transición-decoración/dp/B08RP66C5N


---

# qué puede hacer este equipo que es difícil de replicar:

conocimiento del sector, tecnología dominada, acceso a
distribución, experiencia directa con el usuario objetivo

La ventaja difícil de replicar no es únicamente fabricar los paneles luminosos: es combinar **conocimiento del entrenamiento**, **tecnología confiable**, **acceso recurrente a gimnasios** y **aprendizaje directo de los usuarios**. Cada elemento aislado puede copiarse; la combinación acumulada crea una barrera más defendible.

## Capacidades difíciles de replicar

### 1. Conocimiento específico del sector

El equipo puede diseñar ejercicios que realmente encajen en clases de HIIT, funcional, CrossFit, combate y atletismo, en lugar de construir solo un dispositivo que enciende luces.

Esto incluye:

- Entender cómo trabaja un coach durante una clase grupal.
- Saber cuánto tiempo puede dedicar a configurar una rutina.
- Diseñar ejercicios que no interrumpan el flujo de la sesión.
- Adaptar las dinámicas a calentamiento, activación, competencia y acondicionamiento.
- Identificar qué métricas interesan al entrenador y cuáles son irrelevantes.
- Comprender que el cliente puede valorar más la motivación y la variedad que un análisis biométrico profundo.

**Por qué es difícil de replicar:** un competidor puede copiar la apariencia del hardware, pero necesitaría tiempo dentro de gimnasios para comprender cómo convertir la tecnología en sesiones útiles y repetibles.

**Cómo convertirlo en activo:**

- Biblioteca propia de ejercicios y protocolos.
- Programas específicos para boxeo, fútbol, HIIT, CrossFit y rehabilitación.
- Manuales de uso para coaches.
- Certificación o capacitación Lumetriq para entrenadores.
- Registro de qué rutinas generan mayor frecuencia de uso.


### 2. Tecnología dominada por el equipo

La capacidad técnica debe abarcar tanto el hardware como la experiencia completa:

- Electrónica y sensores táctiles.
- Comunicación inalámbrica entre dispositivos y aplicación.
- Sincronización de varios dispositivos.
- Diseño de carcasas resistentes a golpes, sudor y uso intensivo.
- Gestión de batería y carga.
- Aplicación móvil y conexión con el dispositivo.
- Actualizaciones de firmware.
- Diseño de rutinas, rankings y seguimiento de progreso.
- Diagnóstico remoto de fallas.

La ventaja no es simplemente “saber construir un circuito”; es dominar la integración entre:

$$
\text{hardware} + \text{firmware} + \text{app} + \text{contenido} + \text{operación del gimnasio}
$$

**Por qué es difícil de replicar:** muchos competidores pueden producir una luz que se enciende, pero fallan en confiabilidad, sincronización, batería, facilidad de uso o mantenimiento. En un gimnasio, una falla durante una clase afecta directamente la percepción del producto.

**Cómo demostrarlo:**

- Tiempo de configuración menor a un minuto.
- Funcionamiento simultáneo de tres y seis unidades.
- Baja tasa de desconexiones.
- Autonomía suficiente para varias clases.
- Actualizaciones remotas.
- Reemplazo modular de componentes.
- Historial de pruebas de golpes, humedad y uso repetitivo.

No conviene afirmar que la tecnología es una ventaja difícil de copiar sin evidencia. La defensa aumenta cuando el equipo documenta prototipos, pruebas, iteraciones, firmware propio y decisiones técnicas.

### 3. Acceso a distribución

El acceso a distribución puede convertirse en una barrera relevante si el equipo ya tiene o desarrolla relaciones con:

- Gimnasios boutique.
- Boxes de CrossFit.
- Entrenadores personales.
- Academias de combate.
- Preparadores físicos.
- Distribuidores de equipo funcional.
- Universidades con programas deportivos.
- Clínicas de fisioterapia y centros de rendimiento.

**Por qué es difícil de replicar:** fabricar un producto es distinto a conseguir que llegue a las manos del coach correcto. Las relaciones comerciales, la confianza y la capacidad de demostrarlo en una clase reducen el costo de adquisición.

El canal más valioso no sería únicamente una tienda en línea. Sería una red de entrenadores que:

1. Prueban Lumetriq.
2. Lo incorporan a sus sesiones.
3. Recomiendan el sistema a otros gimnasios.
4. Generan contenido de uso.
5. Aportan retroalimentación al producto.

**Cómo convertirlo en activo:**

- Programa de entrenadores embajadores.
- Comisión por referencia o venta.
- Distribuidores especializados por ciudad.
- Días de demostración en gimnasios.
- Paquetes para coaches certificados.
- Casos de éxito medibles.
- Inventario local y tiempos de entrega cortos.

La distribución todavía debe considerarse una **capacidad por construir**, salvo que el equipo ya cuente con relaciones verificables. No debe presentarse como ventaja competitiva consolidada sin nombrar canales, aliados o clientes piloto concretos.

### 4. Experiencia directa con el usuario objetivo

La interacción directa con coaches y dueños de gimnasios permite aprender cosas que una investigación secundaria no revela:

- Qué parte de la configuración resulta frustrante.
- Qué ejercicios se repiten realmente.
- Cuántos dispositivos necesita una clase.
- Quién paga: el dueño, el coach o el atleta.
- Qué precio se percibe como razonable.
- Qué funciones de la app se utilizan después de la primera semana.
- Qué hace que el gimnasio renueve la suscripción.
- Qué ocurre cuando la batería está baja o un dispositivo falla.

**Por qué es difícil de replicar:** cada sesión de uso produce conocimiento acumulado. Un competidor puede entrevistar usuarios, pero no puede comprar instantáneamente la experiencia de cientos de pruebas, errores y ajustes.

Este conocimiento puede transformarse en un ciclo de aprendizaje:

$$
\text{uso real} \rightarrow \text{datos y entrevistas} \rightarrow \text{mejor producto}
\rightarrow \text{mayor adopción} \rightarrow \text{más uso real}
$$

La experiencia debe registrarse sistemáticamente, no quedarse como conocimiento informal del equipo.

### 5. Datos de uso y contenido propio

La aplicación puede convertirse en la principal barrera de Lumetriq si acumula:

- Rutinas más utilizadas.
- Duración promedio de las sesiones.
- Número de participantes.
- Ejercicios con mayor repetición.
- Tasa de finalización.
- Frecuencia de uso por gimnasio.
- Diferencias entre deportes y niveles.
- Resultados antes y después de una rutina.
- Razones de abandono o cancelación.

Estos datos no deben venderse como evidencia científica si no existe un protocolo de validación, pero sí pueden utilizarse para mejorar el producto.

Con el tiempo, Lumetriq podría saber:

- Qué rutinas funcionan mejor para clases grupales.
- Qué número de dispositivos produce mayor participación.
- Qué ejercicios son más atractivos para principiantes.
- Qué funciones predicen la renovación de un gimnasio.

Un competidor que copie el hardware no tendría automáticamente esa base de conocimiento.

## Qué sí puede copiar un competidor

No conviene sobreestimar la barrera. Relativamente fáciles de replicar serían:

- La forma exterior del dispositivo.
- Luces LED y botones táctiles.
- Un temporizador básico.
- Una aplicación con rankings simples.
- El paquete de tres o seis unidades.
- Un precio inicial bajo.
- Mensajes de marketing sobre reflejos y agilidad.

Por eso, la ventaja no debe basarse en “tenemos luces”, sino en:

- Mejor adaptación a clases grupales.
- Menor tiempo de configuración.
- Mayor confiabilidad.
- Contenido localizado para entrenadores mexicanos.
- Distribución cercana.
- Servicio posventa.
- Datos de uso acumulados.
- Comunidad de coaches.
- Iteración constante con usuarios reales.


## Formulación recomendada para presentar al equipo

> Lumetriq combina conocimiento directo de la operación de gimnasios y entrenamiento funcional con capacidades propias de diseño mecatrónico, desarrollo de software y validación de producto. Esta combinación permite crear rutinas y herramientas diseñadas para clases grupales reales, mientras el acceso continuo a coaches y gimnasios genera un ciclo de aprendizaje difícil de replicar. La ventaja inicial no está en una patente o en el hardware aislado, sino en la integración entre dispositivo, aplicación, contenido y distribución especializada.

## Evidencia que deberían construir

| Capacidad | Evidencia necesaria |
| :-- | :-- |
| Conocimiento del sector | Entrevistas documentadas, protocolos de entrenamiento y coaches asesores |
| Tecnología dominada | Prototipo funcional, pruebas de batería, conectividad y resistencia |
| Distribución | Cartas de intención, gimnasios piloto, distribuidores o embajadores |
| Experiencia de usuario | Sesiones observadas, métricas de uso y reportes de iteración |
| App y contenido | Biblioteca propia de rutinas, retención y frecuencia de uso |
| Aprendizaje acumulado | Registro de problemas, mejoras y decisiones basadas en pilotos |

La ventaja más defendible para Lumetriq sería, por tanto, **la integración de tecnología propia con conocimiento operativo del gimnasio y una red creciente de usuarios de entrenamiento**, no el dispositivo físico por sí solo.

<span style="display:none">[^6_1][^6_2][^6_3][^6_4]</span>

<div align="center">⁂</div>

[^6_1]: https://www.perplexity.ai/search/03daf254-b9f3-42a2-ba2b-33d1a6242d66

[^6_2]: https://www.perplexity.ai/search/0b03bfab-76fa-472b-9921-7556e5e212a7

[^6_3]: https://www.perplexity.ai/search/461a3155-306b-4218-9d37-909a9904f0c3

[^6_4]: https://www.perplexity.ai/search/fd869efb-d169-4007-87b5-4991b50ef7a1


---

## ¿Qué puede hacer Lumetriq difícil de replicar?

Lumetriq puede diferenciarse por integrar en un solo sistema:

- **Tecnología multimodal:** sensores de contacto, fuerza, acelerómetro y proximidad para detectar no solo si el usuario tocó el dispositivo, sino cómo, con qué intensidad y con qué movimiento.
- **Experiencia audiovisual sincronizada:** LEDs en los dispositivos y sonidos sincronizados desde la app para crear estímulos visuales y auditivos coordinados.
- **Ecosistema hardware–software:** dispositivos conectados con rutinas, métricas, gráficas y leaderboards dentro de una misma aplicación.
- **Diseño para uso intensivo:** estructura compacta y resistente, adecuada para golpes, sudor y sesiones repetitivas en gimnasios.
- **Conocimiento del usuario objetivo:** la experiencia directa con coaches y gimnasios permite diseñar rutinas útiles para clases grupales de HIIT, funcional, CrossFit y entrenamiento de reacción.
- **Datos y aprendizaje acumulado:** cada sesión puede generar información sobre tiempos de reacción, fuerza, precisión, movimiento y desempeño competitivo, permitiendo mejorar continuamente las rutinas y la experiencia.

La ventaja difícil de copiar no es un LED o un sensor aislado, sino la **integración compacta y resistente de sensores, estímulos audiovisuales, aplicación y contenido de entrenamiento**, adaptada específicamente a las necesidades de gimnasios y coaches.

---

# Del TAM/SAM/SOM tomé el que costaba 7990, me puedes decir cuál es el precio por unidad

El precio unitario del paquete **Lumetriq Studio de MXN 7,990** depende de cuántos dispositivos incluya:

- **Paquete de 6 dispositivos:**\
**MXN 7,990 ÷ 6 = MXN 1,331.67 por dispositivo**
- **Paquete de 3 dispositivos de MXN 4,490:**\
**MXN 4,490 ÷ 3 = MXN 1,496.67 por dispositivo**

Por lo tanto, para el TAM/SAM/SOM que utilizó el paquete de seis dispositivos:

> **Precio de venta unitario: aproximadamente MXN 1,332 por dispositivo.**

Con un costo de producción de **MXN 550 por dispositivo**:

- Margen bruto unitario: **MXN 781.67**
- Margen bruto porcentual sobre precio de venta: **58.7%**
- Multiplicador sobre costo: **2.42×**

Este margen es **antes** de considerar empaque, cargador, accesorios, garantía, logística, impuestos, comisiones y soporte.

