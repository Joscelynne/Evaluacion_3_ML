Objetivo del Proyecto
Construir un modelo de clasificación binaria para predecir la probabilidad de incumplimiento de crédito (TARGET = 1) en solicitantes de préstamos.
El proyecto aborda la integración de múltiples fuentes de datos (tablas relacionales) y el manejo del desbalance de clases para obtener una solución escalable y desplegable.

Estructura del Repositorio (Basado en CRISP-DM)

project_root

data/

application_train.csv

otros archivos .csv del dataset Home Credit

notebooks/

01_EDA_Exploracion_Inicial.ipynb

02_Clustering_KMeans_Feature_Analysis.ipynb

src/

risk_prediction_model.py (script principal con preprocesamiento y modelado)

feature_engineering.py (funciones para unir y agregar tablas)

preprocessing_pipeline.py (definición del ColumnTransformer)

assets/

diagrama_datos.png (relaciones entre tablas)

README.md

requirements.txt

Tecnologías y Librerías

Este proyecto está desarrollado en Python utilizando las siguientes herramientas:

Data: Pandas, NumPy
Modelado: Scikit-Learn, LightGBM
Visualización: Matplotlib, Seaborn
Despliegue: FastAPI o Flask

Instalación de dependencias:
pip install -r requirements.txt

Desafíos Clave y Soluciones Implementadas

Integración de múltiples tablas

Uso de funciones de agregación (groupby().agg()) para consolidar datos de bureau, previous_application, etc.

Ubicación: src/risk_prediction_model.py (feature_engineering)

Alta dimensionalidad

Uso de LightGBM, modelo eficiente para muchas columnas y datos heterogéneos.

Técnica: LGBMClassifier

Desbalance de clases

Ajuste del parámetro scale_pos_weight en LightGBM para penalizar errores en la clase minoritaria.

Preprocesamiento robusto

ColumnTransformer con imputación automática, escalado y OneHotEncoder sin riesgo de data leakage.

Análisis complementario

Clustering con K-Means para segmentar clientes y usar el ID del cluster como característica adicional.

notebooks/02_Clustering_KMeans_Feature_Analysis.ipynb

Cómo Ejecutar el Proyecto

Clonar el repositorio:
git clone https://docs.github.com/es/repositories/creating-and-managing-repositories/quickstart-for-repositories

cd nombre_del_repositorio

Descargar los datos:
Colocar los archivos del dataset Home Credit (application_train.csv, bureau.csv, etc.) en la carpeta data/.

Ejecutar el flujo principal:
python src/risk_prediction_model.py

Resultados Esperados

El script mostrará:

Reportes de clasificación de los modelos (Regresión Logística y LightGBM)

Métrica AUC-ROC para comparar modelos

Gráfico de importancia de características del modelo final (LightGBM)