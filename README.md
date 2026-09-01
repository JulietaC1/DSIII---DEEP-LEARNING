# Pre-Entrega 3: Clasificador Supervisado con TF-IDF

En esta etapa del proyecto se construyó un pipeline de clasificación supervisada para el dataset de noticias AG News, aplicando técnicas de NLP clásico y modelos machine learning tradicionales.

## Elección del Modelo
Se seleccionó Regresión Logística como modelo base porque funciona muy bien con matrices numéricas dispersas de alta dimensión (como las que genera TF-IDF). Además de ser un modelo muy rápido para entrenar, tiene un comportamiento lineal que ayuda a controlar el riesgo de sobreajuste.

## Configuración de TF-IDF
Para la vectorización del texto se utilizaron las siguientes opciones:
* **max_features = 5000:** Limité el vocabulario a las 5,000 palabras más representativas para no sobrecargar la memoria y evitar meter ruido en los datos.
* **ngram_range = (1, 2):** Incluí palabras individuales y pares de palabras (unigramas y bigramas) para no perder expresiones compuestas como *"new york"* o *"oil price"*.
* **Cero Data Leakage:** Ajusté el vocabulario (`fit_transform`) únicamente con los datos de entrenamiento (`X_train`) y sobre el conjunto de prueba (`X_test`) apliqué solamente `transform`.

## Resultados y Matriz de Confusión
* **Accuracy general:** El modelo alcanzó un 89% de precisión global en las 2,000 noticias de prueba.
* **Categoría de mejor desempeño:** *Sports* fue la mejor clasificada con un F1-Score de 0.96, gracias a que maneja un vocabulario deportivo bastante marcado.
* **Puntos de confusión:** El mayor cruce de errores se dio entre *Business* y *Sci_Tech* (40 y 46 errores en la matriz). Esto tiene lógica, ya que muchas noticias de tecnología hablan de empresas, acciones o lanzamientos de mercado.

## Requisitos e Instalación
Las librerías y versiones utilizadas en el desarrollo están detalladas en `requirements.txt`.
