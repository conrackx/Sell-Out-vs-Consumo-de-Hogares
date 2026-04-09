# 📘 **Informe Analítico – Ejercicio Práctico de Business Intelligence**

**Tema:** Análisis Integrado de Sell Out y Consumo de Hogares  
**Herramienta:** Microsoft Power BI  
**Autor:** _Miguel Urbina_  
**Fecha:** _31 de marzo de 2026_

---

## 1. Introducción

El presente informe describe el desarrollo y los resultados del **ejercicio práctico de Analista de Business Intelligence**, cuyo objetivo principal es **integrar información de Sell Out y Consumo de Hogares** para analizar el desempeño comercial, el cumplimiento de objetivos y el comportamiento del consumidor, con el fin de **identificar oportunidades de mejora y optimización del negocio**.

Para ello se diseñó un **modelo de datos optimizado**, se desarrollaron **medidas DAX estratégicas** y se construyó un **informe interactivo en Power BI**, enfocado en la correcta narrativa de los datos y la toma de decisiones.

---

## 2. Fuentes de Datos Utilizadas

El análisis integra las siguientes fuentes:

- **Sell Out**: ventas al consumidor final a nivel de tienda y producto.
- **Consumo de Hogares**: información de compra por hogar, canal y nivel socioeconómico.
- **Productos**: maestro de productos con jerarquías de categoría, segmento, marca y descripción.
- **Tiendas**: información geográfica y operativa de los puntos de venta.
- **Objetivos de Sell Out**: metas comerciales definidas por tienda y año.
- **Calendario**: dimensión temporal estándar, marcada como tabla de fechas.

Estas fuentes fueron integradas bajo un **esquema en estrella**, garantizando consistencia analítica, rendimiento y claridad del modelo.

---

## 3. Modelado de Datos y Enfoque Analítico

El modelo se diseñó considerando diferentes **granos de información**:

- **Sell Out**: semana – tienda – producto.
- **Consumo de Hogares**: periodo – hogar – producto.
- **Objetivos**: año – tienda.

Los objetivos comerciales no se relacionan físicamente con la tabla calendario, ya que el **cumplimiento mensual y acumulado se gestiona mediante DAX**, alineado con la naturaleza anual de la meta.  
La dimensión calendario centraliza toda la lógica temporal, permitiendo análisis YTD, MTD e interanual de forma consistente.

---

## 4. Descripción del Informe Power BI

El informe se estructura en varias páginas, cada una diseñada para responder una pregunta específica del negocio y conducir progresivamente al análisis estratégico.

---

### 4.1 Portada

La portada cumple una función introductoria y de navegación, incorporando **marcadores** que permiten acceder a las diferentes secciones del informe.

---

### 4.2 Resumen Ejecutivo

**Objetivo:** Proporcionar una visión general del desempeño del negocio.

Esta página presenta indicadores clave como:

- Ventas USD acumuladas (YTD)
- Meta YTD
- Variación frente a la meta
- Porcentaje de cumplimiento

Complementariamente, se muestra la evolución mensual de ventas frente al objetivo, así como la distribución territorial y por categoría, permitiendo al usuario comprender rápidamente **cómo va el negocio y dónde se concentra el resultado**.

---

### 4.3 Análisis de Sell Out

**Objetivo:** Identificar los principales motores del desempeño comercial.

En esta sección se analizan:

- Distribución de ventas por categoría y segmento.
- Productos líderes (Top 10) por ventas.
- Desempeño de marcas comparado con el año anterior.
- Contribución geográfica por estado.

Esta página permite entender **qué productos, marcas y regiones explican el resultado observado en el Resumen Ejecutivo**, y detectar crecimientos o caídas relevantes.

---

### 4.4 Performance vs Target

**Objetivo:** Evaluar el cumplimiento de objetivos comerciales a nivel operativo.

Aquí se analiza el desempeño **por tienda**, mostrando:

- Ventas reales vs meta definida.
- Cumplimiento porcentual.
- Brechas positivas y negativas.
- Número de tiendas que cumplen los objetivos.

Esta página facilita la **priorización de acciones comerciales**, identificando tiendas en riesgo o con sobrecumplimiento.

---

### 4.5 Alineación del Mercado

**Objetivo:** Evaluar la coherencia entre la oferta comercial y la demanda del consumidor.

Se comparan:

- **Share de Ventas** vs **Share de Gasto del consumidor** por categoría.
- Brecha de participación.
- Índice de oportunidad comercial.

Adicionalmente, se analiza la relación entre:

- Ventas,
- Gasto,
- Cantidad de hogares compradores.

Esta sección constituye el **núcleo estratégico del informe**, ya que permite identificar categorías con potencial de crecimiento o desalineación entre lo que se vende y lo que el consumidor demanda.

---

### 4.6 Consumo de Hogares

**Objetivo:** Comprender el comportamiento del consumidor.

Se analizan indicadores como:

- Cantidad de hogares compradores.
- Gasto total y promedio.
- Frecuencia de compra.
- Distribución por nivel socioeconómico.
- Comportamiento por canal (tradicional y moderno).
- Evolución temporal del gasto por segmento.

Esta página explica **las causas de la demanda observada** y aporta contexto al análisis de alineación de mercado.

---

### 4.7 Páginas Finales – Drill Through

**Objetivo:** Facilitar la exploración del detalle transaccional que sustenta los agregados del informe, permitiendo validar hipótesis y trazar hallazgos ejecutivos hasta la transacción.

Se documentan y operan tres páginas de drill‑through que responden preguntas concretas:

- **Detalle anual por descripción y mes:** muestra, para la descripción seleccionada, la evolución mensual de ventas y el detalle de transacciones que componen cada total.
- **Análisis de Sell Out por marca y segmento:** descompone la contribución de marcas y segmentos dentro de la categoría seleccionada, permitiendo identificar los SKUs y segmentos que explican el desempeño.
- **Performance vs Target:** compara Meta Mensual y Ventas USD por año y por mes, mostrando variación absoluta y porcentual para identificar brechas operativas.

Estas páginas finales actúan como **nivel de exploración avanzada** del informe: concentra el detalle necesario para auditar resultados, validar hipótesis y soportar decisiones operativas sin perder la trazabilidad desde los KPIs ejecutivos.

---

## 5. Limitaciones

El desarrollo del informe presentó diversas limitaciones técnicas derivadas de la estructura original de las fuentes de datos y de la necesidad de garantizar un modelo analítico coherente. Las principales consideraciones fueron las siguientes:

**1. Relación entre los objetivos comerciales y la dimensión calendario**  
Los objetivos comerciales, al estar modelados como una hoja de hechos independiente, no podían relacionarse directamente con la dimensión estándar de tiempo. Esto impedía establecer una relación física tradicional en el modelo. Para resolverlo, se gestionó la lógica temporal despivotando dicha tabla y manejandola mediante medidas DAX, permitiendo calcular metas mensuales y anuales sin comprometer la integridad del modelo dimensional.

**2. Ausencia de una dimensión calendario estandarizada**  
El conjunto de datos original no incluía una dimensión calendario completa, indispensable para realizar análisis temporales robustos. Por ello, se importó una tabla de calendario estandarizada diseñada para soportar inteligencia de tiempo, garantizando la correcta ejecución de funciones YTD, MTD y comparaciones interanuales.

**3. Transformación de la tabla de objetivos comerciales**  
La tabla de objetivos presentaba un formato no analítico, con metas distribuidas en columnas por mes. Para habilitar su uso dentro del modelo, fue necesario despivotar la estructura, permitiendo que el año del objetivo funcionara como una marca temporal válida y que cada tienda tuviera un registro único por periodo. Dado que los objetivos comerciales se expresaban como un monto mensual único, se reutilizó dicho valor para calcular la meta anual, manteniendo coherencia con la lógica de negocio.

**4. Incompletitud de la dimensión de productos**  
La dimensión de productos no contenía la totalidad de los códigos de barras presentes en las fuentes de Sell Out y Consumo de Hogares. Esta inconsistencia generaba pérdidas de información y afectaba la correcta asignación de categorías, marcas y segmentos. Para mitigar este problema, se realizó una auditoría completa de códigos de barras y se reconstruyó la dimensión de productos, incorporando los códigos previamente ausentes, incluidos aquellos asociados a productos clasificados como “sin datos”.

---

## 6. Conclusiones

El informe desarrollado cumple con los objetivos del ejercicio al:

- Integrar de forma coherente múltiples fuentes de datos.
- Aplicar un modelo dimensional claro y eficiente.
- Utilizar medidas DAX robustas y reutilizables.
- Construir una narrativa que avanza desde el desempeño general hasta la identificación de oportunidades estratégicas.

El resultado es un reporte que no solo describe lo ocurrido, sino que **apoya la toma de decisiones**, al conectar ventas, objetivos y comportamiento del consumidor.
