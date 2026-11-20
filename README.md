
# Pipeline de Preprocesamiento Robusto con Scikit-Learn

## Descripción del proyecto

Este proyecto tiene como objetivo construir un pipeline de preprocesamiento de datos utilizando Scikit-Learn, automatizando las tareas de limpieza y transformación de datos para preparar un conjunto de datos antes de aplicar un modelo de Machine Learning.

Se utiliza un dataset relacionado con vehículos para desarrollar un modelo de regresión capaz de predecir el valor de venta (`selling_value`) a partir de diferentes características.
El dataset se obtuvo de https://www.kaggle.com/datasets/yuremartins/car-rental-data


## Objetivos

- Automatizar el preprocesamiento de datos.
- Evitar la fuga de datos (Data Leakage).
- Diferenciar el tratamiento de variables numéricas y categóricas.
- Construir un Pipeline reutilizable.
- Entrenar y evaluar un modelo de Machine Learning.
- Guardar el pipeline entrenado utilizando Joblib.

## Dataset utilizado

El dataset contiene 2.000 registros y 7 columnas.

Las variables utilizadas son:

| Variable | Tipo |
|---|---|
| purchase_value | Numérica |
| desc_vehicle | Categórica |
| segment | Categórica |
| contract_duration | Numérica |
| selling_value | Variable objetivo |

La variable objetivo es `selling_value`, que representa el valor de venta que el modelo intenta predecir.

## Tecnologías y librerías

- Python
- Pandas
- NumPy
- Scikit-Learn
- Joblib
- Google Colab

## Desarrollo del proyecto

### 1. Carga y exploración de datos

Se realiza la carga del dataset y el análisis de sus características, tipos de datos y valores faltantes.

### 2. División de datos

Se utiliza `train_test_split` para dividir los datos:

- 80% para entrenamiento.
- 20% para prueba.

La división se realiza antes de ajustar los transformadores para evitar Data Leakage.

### 3. Preprocesamiento

Se implementa un `ColumnTransformer` con dos tratamientos:

**Variables numéricas:**
- Imputación de valores faltantes mediante la mediana.
- Estandarización con StandardScaler.

**Variables categóricas:**
- Imputación mediante el valor más frecuente.
- Codificación con OneHotEncoder.
- Tratamiento de categorías desconocidas mediante `handle_unknown='ignore'`.

### 4. Construcción del Pipeline

Se utiliza la clase `Pipeline` de Scikit-Learn para integrar el preprocesamiento y el modelo de Regresión Lineal (`LinearRegression`).

### 5. Evaluación del modelo

Se utilizan las siguientes métricas:

| Métrica | Resultado |
|---|---:|
| MAE | 6531.41 |
| MSE | 74155969.73 |
| RMSE | 8611.39 |
| R² | 0.9659 |

El modelo obtuvo un coeficiente de determinación R² de 0.9659 en el conjunto de prueba.

### 6. Predicción y persistencia

Se comprueba el funcionamiento del método `.predict()` utilizando nuevos datos.

Finalmente, se exporta el pipeline entrenado mediante la librería Joblib.

Archivo generado: `pipeline_vehiculos.pkl`.

## Estructura del repositorio

- `Pipeline_Preprocesamiento.ipynb`: notebook con la implementación completa.
- `datos_alquiler_autos.csv`: conjunto de datos utilizado.

## Instalación de dependencias

Instalar las siguientes librerías:

```bash
pip install pandas numpy scikit-learn joblib
```

## Ejecución

1. Descargar el repositorio.
2. Abrir Google Colab.
3. Cargar el notebook `Pipeline_Preprocesamiento.ipynb`.
4. Cargar el archivo CSV cuando el notebook lo solicite.
5. Ejecutar las celdas en orden.

## Conclusión

Se desarrolló un pipeline de preprocesamiento robusto y reutilizable con Scikit-Learn, integrando la imputación de valores faltantes, escalado de variables numéricas y codificación de variables categóricas.

La implementación permite mantener un tratamiento consistente de los datos durante el entrenamiento y las predicciones, evitando la fuga de información entre los conjuntos de entrenamiento y prueba.
