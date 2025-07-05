# Mantenimiento Predictivo de Máquinas

## Descripción del problema
¿Podemos predecir a tiempo si una máquina sufrirá una falla conociendo las lecturas de diferentes tipos de sensores como temperatura, velocidad de rotación, etc?

El objetivo con este proyecto es lograr predecir estas fallas a tiempo, para así realizar la debida mantención y evitar costos mayores.

## Dataset
- Fuente: [Kaggle – Machine Predictive Maintenance Dataset](https://www.kaggle.com/datasets/shivamb/machine-predictive-maintenance-classification)
- Este dataset contiene datos asociados a lecturas de sensores, los cuales dan información respecto a las condiciones operativas de máquinas en la industria. Este dataset tiene 10000 data points almacenados como filas con 14 features en columnas.
La variable objetivo es Machine failure, la cual es binaria, donde: 0 = no hay falla, 1 = hay falla.

#### 📄 Features disponibles

| Feature              | Tipo        | Descripción |
|------------------------|-------------|-------------|
| `UDI`                 | Numérica     | Identificador único del registro. |
| `Product ID`          | Categórica   | ID del producto. |
| `Type`                | Categórica   | Tipo de producto A, B o C. |
| `Air temperature [K]` | Numérica     | Temperatura del aire en Kelvin. |
| `Process temperature [K]` | Numérica | Temperatura del proceso interno. |
| `Rotational speed [rpm]` | Numérica  | Velocidad de rotación del eje de la máquina. |
| `Torque [Nm]`         | Numérica     | Fuerza de torsión aplicada. |
| `Tool wear [min]`     | Numérica     | Minutos acumulados de desgaste de herramienta. |
| `Target` (`Machine failure`) | Binaria | Variable objetivo: 0 = no hay falla, 1 = hay falla. |
| `Failure Type`        | Categórica   | Tipo específico de falla. |

Solo se utilizarán como **features** las variables numéricas relevantes (temperaturas, torque, velocidad, desgaste), junto con `Type` codificada. Se excluirán `UDI`, `Product ID` y `Failure Type`.

## Modelo seleccionado
- Random Forest

## Estrategia de evaluación
El modelo se evaluará utilizando una división de los datos en un 80% para entrenamiento y 20% para testeo, manteniendo el balance de clases. 


Las métricas utilizadas serán:
- Accuracy: para medir el desempeño general.
- Precision: para saber cuántas predicciones positivas son correctas.
- Recall: para medir cuántas fallas reales se logran detectar.
- F1-score: equilibrio entre precisión y recall.
- Matriz de confusión: para visualizar errores de clasificación.

Estas métricas permitirán evaluar el desempeño del modelo, logrando así verificar que tan bien identifica las fallas reales y si minimiza falsas alarmas, algo fundamental en un sistema de mantenimiento predictivo.


## Justificación del modelo
- Ventajas: Random Forest es un modelo robusto que maneja bien relaciones no lineales entre variables, puede trabajar con variables tanto numéricas como categóricas, y puede determinar la importancia de cada variable. Además, es menos sensible al overfitting que otros modelos como los árboles de decisión simples.
- Limitaciones: Al tratarse de un modelo de caja negra puede ser más difícil de interpretar que un árbol de decisión simple, y consume más recursos computacionales. No es muy apto para datasets extremadamente grandes o con muchos atributos irrelevantes.
- Pertinencia: El dataset contiene relaciones probablemente no lineales entre sensores y fallas, lo que hace que un modelo como Random Forest sea el más adecuado. Además, permite manejar diversos tipos de features y puede integrarse fácilmente en entornos industriales reales.

## Metodología aplicada

1. Carga y exploración inicial de los datos
   - Se revisará la estructura del dataset, los tipos de variables que presenta, y si tiene valores faltantes o inconsistentes.
2. Análisis exploratorio (EDA)
   - Se analizaran las distribuciones de las variables que son numéricas, el balance de clases en la variable objetivo y la correlación entre sensores.
3. Preprocesamiento y feature engineering
   - Se eliminarán columnas irrelevantes para la predicción, como `UDI` y `Product ID`.
   - Se codificará en binario la variable categórica `Type`.
   - Se normalizarán las variables numéricas de ser necesario.
4. Selección del modelo y entrenamiento
   - Se entrenará un modelo de Random Forest con el conjunto de entrenamiento.
   - Se realizará la división de los datos en 80/20.
5. Control de overfitting
   - Se ajustarán hiper parámetros como `max_depth`, `n_estimators` y `min_samples_split`.
   - Se usará validación cruzada (Cross-Validation) para evaluar la robustez del modelo.
6. Evaluación del modelo mediante métricas
   - Se calcularán métricas como accuracy, precision, recall, F1-score.
   - Se construirá una Matriz de Confusión y una Curva ROC.
7. Visualización de resultados
   - Se graficarán métricas y se presentará la importancia de cada variable (feature-importances) para la predicción.

## Autores
Diego Avendaño y Braulio Silva
