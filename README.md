
# Predicción de precios de acciones con redes LSTM

Proyecto final de la materia **Laboratorio de Datos** (FCEyN, UBA, 2025), realizado en conjunto con [Maximiliano Rodríguez Camps](https://github.com/).

## Objetivo

Explorar qué tan bien una red neuronal recurrente (LSTM) puede predecir el precio de cierre de una acción (MercadoLibre, MELI), y cómo cambia esa capacidad predictiva al agregar más información al modelo.

## Enfoque

Se entrenaron y compararon **tres versiones progresivas** de un modelo LSTM:

1. **Univariado** — el modelo solo ve el precio de cierre histórico.
2. **Multivariado** — se agrega el volumen de operaciones como variable adicional.
3. **Multivariado + acciones correlacionadas** — se identifican, mediante análisis de correlación, otras acciones relacionadas con MELI (Shopify, Amazon, Sea Ltd) y se incluyen como variables adicionales.

## Evaluación

Los modelos se evaluaron con varias métricas, no solo el error de predicción:

- **MAE / MSE / R²** — error de la predicción del valor exacto.
- **Sign accuracy** — si el modelo acierta la *dirección* del movimiento (sube/baja), que es más relevante que el valor exacto en un contexto financiero.
- **Predicción recursiva** — se probó alimentar al modelo con sus propias predicciones (en vez de datos reales) para varios pasos hacia adelante, y observar en qué punto se degrada la calidad de la predicción.

## Resultados y conclusiones

Agregar volumen y acciones correlacionadas mejoró el desempeño frente al modelo univariado, aunque predecir el precio de una acción sigue siendo, como es esperable, un problema difícil (los mercados financieros son notoriamente ruidosos e influidos por factores no capturados en el precio histórico). El valor del proyecto está en el proceso: diseño de un pipeline de series temporales de punta a punta, feature engineering basado en análisis de correlación, y una evaluación honesta y crítica de los resultados más allá de una sola métrica.

## Herramientas

Python · TensorFlow/Keras (LSTM) · pandas · yfinance (datos históricos) · scikit-learn (métricas) · matplotlib

## Datos

Datos históricos de precios descargados vía la API de Yahoo Finance (`yfinance`).
