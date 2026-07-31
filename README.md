# Análisis de ventas y cancelaciones con Python

Proyecto de portafolio en desarrollo sobre transacciones reales de comercio electrónico.

## Objetivo

Entregar al responsable comercial un diagnóstico reproducible de ventas, cancelaciones, productos, clientes, países y evolución mensual, acompañado de recomendaciones verificables.

## Fuente

Online Retail, UCI Machine Learning Repository:

- 541.909 líneas transaccionales.
- Periodo: diciembre de 2010 a diciembre de 2011.
- Archivo original: `Online Retail.xlsx`.
- Licencia del dataset: CC BY 4.0.
- Fuente: https://archive.ics.uci.edu/dataset/352/online-retail
- DOI: https://doi.org/10.24432/C5BW33

## Estado

En desarrollo. El alcance y los criterios de aceptación están en [`docs/project_brief.md`](docs/project_brief.md).

## Estructura

```text
online-retail-analysis-python/
├── data/
│   ├── raw/                  # Fuente original; no se modifica
│   └── processed/            # Salidas reproducibles; no se editan a mano
├── docs/
│   ├── ai_usage.md           # Registro del uso de IA y validaciones
│   ├── data_dictionary.md     # Significado y granularidad de los campos
│   ├── project_brief.md      # Encargo y criterios de aceptación
│   └── project_status.md     # Seguimiento de entregas
├── notebooks/
│   └── 01_online_retail_eda.ipynb
├── reports/
│   ├── figures/              # Gráficos finales
│   └── executive_summary.md  # Resumen para el responsable comercial
├── .gitignore
├── README.md
└── requirements.txt
```

## Cómo reproducir

1. Descargar `Online Retail.xlsx` desde la fuente indicada.
2. Guardarlo en `data/raw/`.
3. Crear el entorno con las dependencias de `requirements.txt`.
4. Ejecutar el notebook completo de arriba abajo.

Los pasos y resultados finales se completarán cuando el análisis esté validado.
