# Actividad práctica: comparación de algoritmos supervisados

Repositorio del equipo para comparar KNN, SVM y MLP en la clasificación binaria de tumores (benignos/malignos).

## Estructura

```text
comparacion-algoritmos-supervisados/
├── data/
│   └── wdbc.data
│   └── wdbc.names
├── docs/
│   ├── conclusiones.md
│   └── equipo.md
├── notebooks/
│   └── comparacion_knn_svm_mlp.ipynb
├── .gitignore
├── LICENSE
└── README.md
```

## Ejecución en Google Colab

1. Abre `notebooks/comparacion_knn_svm_mlp.ipynb` en Google Colab.
2. Ejecuta las celdas en orden.
3. Cuando se solicite, carga el CSV o Excel del dataset entregado por el docente.
4. En la sección **Configuración de la variable objetivo**, cambia `TARGET_COLUMN` por el nombre exacto de la columna que contiene benigno/maligno.
5. Si hay identificadores (por ejemplo, `id`), agrégalos a `DROP_COLUMNS` para excluirlos de las características.
6. Comprueba que la clase positiva impresa sea la clase maligna. Si no, ajusta `positive_label`.
7. Ejecuta todo el notebook y revisa métricas, matrices, gráficas e interpretación.
8. Guarda el notebook con las salidas para que el docente pueda revisar el desarrollo y los resultados.

## Metodología

- Una sola división estratificada entrenamiento/prueba (80/20, `random_state=42`) compartida por los tres modelos.
- Preprocesamiento dentro de pipelines: imputación, One-Hot Encoding para categóricas y estandarización de numéricas.
- Modelos: KNN, SVM con kernel RBF y MLP.
- Métricas: Accuracy, Precision, Recall, F1-score, matrices de confusión y cantidad de errores.
- Se presta especial atención al Recall de la clase maligna y a los falsos negativos.

## Importante

Los resultados no están precargados porque dependen del dataset adjunto y de la columna objetivo real. No inventar métricas ni conclusiones. La clasificación es un ejercicio académico y no una herramienta de diagnóstico médico.

## Equipo

Completar `docs/equipo.md` con los nombres y aportaciones de los integrantes.
