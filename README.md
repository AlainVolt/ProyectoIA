# Mantenimiento Predictivo de Máquinas

## Descripción del problema
¿Podemos predecir a tiempo si una máquina sufrirá una falla conociendo las lecturas de diferentes tipos de sensores como temperatura, velocidad de rotación, etc?

El objetivo con este proyecto es lograr predecir estas fallas a tiempo, para así realizar la debida mantención y evitar costos mayores.

## Dataset
- Fuente: [Kaggle – Machine Predictive Maintenance Dataset](https://www.kaggle.com/datasets/shivamb/machine-predictive-maintenance-classification)
- Este dataset contiene datos asociados a lecturas de sensores, los cuales dan información respecto a las condiciones operativas de máquinas en la industria.
La variable objetivo es Machine failure, la cual es binaria, donde: 0 = no hay falla, 1 = hay falla.

#### 📄 Variables disponibles

| Variable               | Tipo        | Descripción |
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

## Modelos seleccionados
Modelos a evaluar:
- Naive-Bayes
- Decision Tree
- Random Forest
- K-Nearest Neighbors (KNN)

## Estrategia de evaluación
Cada modelo se evaluará utilizando una división de los datos en un 80% para entrenamiento y 20% para testeo, manteniendo el balance de clases. 


Las métricas utilizadas serán:
- Accuracy: para medir el desempeño general.
- Precision: para saber cuántas predicciones positivas son correctas.
- Recall: para medir cuántas fallas reales se logran detectar.
- F1-score: equilibrio entre precisión y recall.
- Matriz de confusión: para visualizar errores de clasificación.

## Justificación del modelo
- Ventajas: 
- Limitaciones: 
- Pertinencia: 

## Metodología aplicada
1. EDA y preprocesamiento
2. Feature engineering y normalización
3. Entrenamiento de múltiples modelos
4. Control de Overfitting mediante Cross-Validation
5. Evaluación con métricas estándar
6. Visualización de resultados (Confusion Matrix, Curva ROC)

## Autores
Diego Avendaño y Braulio Silva
