# Actividad práctica: comparación de algoritmos supervisados

Repositorio del equipo para comparar KNN, SVM y MLP en la clasificación binaria de tumores (benignos/malignos).

## Estructura

```text
Algoritmos_Ap_Sup/
├── data/
│   ├── wdbc.data
│   └── wdbc.names
├── docs/
│   ├── conclusiones.pdf
│   └── equipo.md
├── notebooks/
│   └── comparacion_knn_svm_mlp.ipynb
├── .gitignore
├── LICENSE
└── README.md
```

## Dataset

Wisconsin Diagnostic Breast Cancer (WDBC), proporcionado por el docente: 569 registros, 30 características numéricas y la variable objetivo `diagnosis` (357 benignos `B` y 212 malignos `M`). El archivo `wdbc.data` no tiene encabezados; los nombres de las columnas se asignan en el notebook según `wdbc.names`.

## Ejecución en Google Colab

1. Abre `notebooks/comparacion_knn_svm_mlp.ipynb` en Google Colab: [abrir en Colab](https://colab.research.google.com/github/AngelaRKE/Algoritmos_Ap_Sup/blob/main/notebooks/comparacion_knn_svm_mlp.ipynb).
2. Ejecuta todas las celdas en orden (Entorno de ejecución > Ejecutar todo).
3. El notebook busca `wdbc.data` en la carpeta `data/`. Si no lo encuentra, lo descarga del repositorio UCI y, si tampoco es posible, pide subir el archivo manualmente.
4. El notebook ya se entrega ejecutado, con todas las métricas, matrices de confusión, gráficas y conclusiones visibles.

## Metodología

- Una sola división estratificada entrenamiento/prueba (80/20, `random_state=42`) compartida por los tres modelos.
- Preprocesamiento dentro de pipelines: imputación por mediana y estandarización (`StandardScaler`) de las variables numéricas. El pipeline también contempla One-Hot Encoding para variables categóricas, aunque este dataset no tiene.
- Modelos: KNN (k=5), SVM con kernel RBF y MLP con dos capas ocultas (64, 32).
- Métricas: Accuracy, Precision, Recall, F1-score, matrices de confusión y cantidad de errores, con la clase maligna como clase positiva.
- Se presta especial atención al Recall de la clase maligna y a los falsos negativos.

## Resultados

| Algoritmo | Accuracy | Precision | Recall | F1-score | FP | FN | Errores |
|---|---|---|---|---|---|---|---|
| KNN | 0.9561 | 0.9744 | 0.9048 | 0.9383 | 1 | 4 | 5 |
| **SVM** | **0.9737** | **1.0000** | **0.9286** | **0.9630** | **0** | **3** | **3** |
| MLP | 0.9649 | 1.0000 | 0.9048 | 0.9500 | 0 | 4 | 4 |

El algoritmo seleccionado es **SVM**: tiene la mayor accuracy y, sobre todo, el mayor Recall para la clase maligna, que es el criterio más importante en este problema. La interpretación completa está en las fases 7 y 8 del notebook y en `docs/conclusiones.pdf`.

## Importante

La clasificación es un ejercicio académico y no una herramienta de diagnóstico médico.

## Equipo

Los integrantes y sus aportaciones están en `docs/equipo.md`.
