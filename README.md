# Urgencias-ml-proyecto

Proyecto: Modelo de Clasificación para Urgencias Hospitalarias
Descripción General

Este proyecto desarrolla un modelo predictivo para analizar datos de pacientes atendidos en servicios de urgencia, con el objetivo de predecir ingresos hospitalarios (admisión a sala o UCI) basándose en variables clínicas registradas al ingreso.
Se utiliza un enfoque de Machine Learning supervisado, con un modelo de regresión logística entrenado sobre datos anonimizados de un dataset público disponible en Kaggle.

Objetivo del Proyecto

Evaluar la capacidad de un modelo de aprendizaje automático para apoyar la toma de decisiones clínicas en urgencias, identificando qué variables influyen en la probabilidad de hospitalización desde un punto de vista clínico y operativo.

Metodología

Carga y exploración de datos: limpieza, revisión de valores nulos y tipos de variable.

Ingeniería de características: creación de variables derivadas clínicas como presión arterial media (MAP), hipotensión, taquicardia, entre otras.

Estandarización y codificación: escalado de variables numéricas y codificación one-hot para variables categóricas.

Entrenamiento del modelo: regresión logística con evaluación mediante métricas de precision, recall, f1-score y accuracy.

Validación: conjunto adicional de 60 pacientes simulados con estructura real para comprobar la generalización del modelo.

Resultados Principales

Exactitud (accuracy): ~74%

Sensibilidad (recall): mayor en pacientes admitidos que en egresados.

Variables más influyentes: modo de llegada, clasificación KTAS, grupo de hospital y signos vitales (BT, MAP, HR).

Se exploró también un modelo Random Forest, con rendimiento inferior (70%), descartado para su aplicación.

Interpretación Clínica

El modelo demuestra potencial como herramienta de apoyo para priorizar pacientes con mayor probabilidad de ingreso, fortaleciendo la eficiencia en la gestión de camas y el flujo de atención general en servicios de urgencia.

### Documento final
El informe completo en formato PDF se encuentra disponible en este repositorio:  
👉 [informe_final.pdf](./informe_final.pdf)
