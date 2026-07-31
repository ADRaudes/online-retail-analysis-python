# Brief del proyecto

## Encargo

**Rol:** analista de datos junior.

**Solicitante:** responsable comercial de una empresa de comercio electrónico.

**Situación:** la empresa dispone de las transacciones del último año, pero no tiene una visión validada de sus ventas, cancelaciones, concentración de clientes ni desempeño por producto y país.

**Decisión que debe apoyar el análisis:** identificar dónde se genera el ingreso, qué riesgos afectan el desempeño y qué tres acciones comerciales conviene priorizar para el siguiente periodo.

## Fuente obligatoria

Usar **Online Retail** de UCI:

- Página: https://archive.ics.uci.edu/dataset/352/online-retail
- DOI: https://doi.org/10.24432/C5BW33
- Archivo: `Online Retail.xlsx`
- Tamaño aproximado: 22,6 MB
- Licencia: CC BY 4.0

No editar el archivo original. Guardarlo en `data/raw/`.

## Entregables obligatorios

1. `notebooks/01_online_retail_eda.ipynb`
2. `reports/executive_summary.md`
3. Gráficos finales en `reports/figures/`
4. `README.md` final con hallazgos y reproducción
5. `requirements.txt`
6. `docs/ai_usage.md` con uso de IA y validaciones

## Preguntas de negocio

1. ¿Qué periodo y volumen de datos cubre la fuente?
2. ¿Cuáles son las ventas brutas, el valor de cancelaciones y las ventas netas?
3. ¿Cuántos pedidos completados y clientes identificados existen?
4. ¿Cuál es el ticket promedio de los pedidos completados?
5. ¿Cómo evolucionan las ventas netas por mes?
6. ¿Qué productos concentran mayor ingreso y cantidad vendida?
7. ¿Qué países generan mayor ingreso dentro y fuera de Reino Unido?
8. ¿Qué clientes concentran mayor ingreso identificado?
9. ¿Qué meses, productos o países presentan señales anómalas?
10. ¿Qué tres acciones concretas recomienda el análisis?

## Definiciones iniciales

Estas reglas deben comprobarse contra los datos antes de usarse:

- **Valor de línea:** `Quantity * UnitPrice`.
- **Venta completada:** cantidad positiva, precio positivo e invoice que no represente cancelación.
- **Cancelación:** invoice marcado como cancelado o cantidad negativa. Verificar que ambas señales sean coherentes.
- **Ventas brutas:** suma del valor de líneas completadas.
- **Valor cancelado:** valor absoluto de las líneas clasificadas como cancelación.
- **Ventas netas:** ventas brutas menos valor cancelado.
- **Pedidos completados:** invoices únicos de ventas completadas.
- **Ticket promedio:** ventas brutas divididas entre pedidos completados.
- **Clientes identificados:** `CustomerID` únicos no vacíos en ventas completadas.

Si los datos contradicen estas definiciones, documentar el problema y ajustar la regla; no forzar el resultado.

## Fases de trabajo

### 1. Carga y reconocimiento

- Descargar el archivo desde UCI.
- Crear el notebook indicado.
- Cargar el Excel con pandas sin editarlo manualmente.
- Mostrar filas de ejemplo, dimensiones, columnas y tipos.
- Confirmar periodo mínimo y máximo.
- Explicar qué representa una fila.

### 2. Auditoría de calidad

- Contar valores faltantes por columna.
- Revisar duplicados exactos.
- Revisar cantidades y precios iguales, menores o mayores que cero.
- Revisar invoices de cancelación.
- Revisar descripciones y clientes faltantes.
- Registrar cantidades antes de limpiar.

### 3. Limpieza y reglas de negocio

- Convertir fechas al tipo correcto.
- Normalizar texto solo cuando sea necesario.
- Separar ventas completadas y cancelaciones.
- Justificar cada eliminación o reemplazo.
- No eliminar `CustomerID` vacío de las métricas generales de ventas.
- Crear las columnas derivadas necesarias.
- Guardar una salida procesada reproducible; nunca corregirla a mano.

### 4. Análisis

- Calcular los KPI definidos.
- Analizar evolución mensual.
- Calcular top de productos por ingreso y unidades.
- Analizar países con Reino Unido y sin Reino Unido.
- Analizar concentración de ingreso por cliente identificado.
- Investigar al menos una anomalía encontrada durante el EDA.

### 5. Visualización

Crear al menos cuatro gráficos:

1. Línea de ventas netas mensuales.
2. Barras de los diez productos con mayor ingreso.
3. Barras de los diez países con mayor ingreso fuera de Reino Unido.
4. Un gráfico elegido por el analista para explicar cancelaciones, clientes o una anomalía.

Todos deben tener título, ejes, unidades, orden lógico y una breve interpretación.

### 6. Comunicación

El resumen ejecutivo debe contener:

- objetivo;
- cinco hallazgos con cifras;
- tres recomendaciones accionables;
- limitaciones de los datos;
- explicación breve de la metodología.

## Validaciones obligatorias

- Registrar filas antes y después de cada limpieza.
- Reconciliar ventas brutas, cancelaciones y ventas netas.
- Confirmar que los subtotales mensuales sumen el total global.
- Confirmar que los rankings usen `sum`, `mean` o `count` de forma intencional.
- Verificar que un `merge`, si se usa, no multiplique filas.
- Ejecutar el notebook completo de arriba abajo sin depender de celdas anteriores ocultas.
- No publicar una conclusión que no aparezca en una tabla o gráfico ejecutado.

## Uso permitido de IA

La IA puede:

- proponer código;
- explicar errores;
- sugerir validaciones;
- refactorizar;
- revisar gráficos y redacción.

El analista debe:

- explicar la lógica del código usado;
- anticipar el resultado esperado;
- validar los resultados;
- decidir las métricas y reglas de negocio;
- registrar en `docs/ai_usage.md` los usos materiales de IA.

No se acepta código copiado sin comprensión ni conclusiones inventadas por la IA.

## Fuera de alcance

- Machine learning.
- Dashboard en Power BI.
- Segmentación RFM formal.
- Predicción de ventas.
- Aplicación web.

## Criterio de aceptación

El proyecto se aprueba si otro analista puede descargar la fuente, ejecutar el notebook de arriba abajo y obtener los mismos KPI, gráficos y conclusiones; además, cada recomendación debe estar respaldada por evidencia visible.
