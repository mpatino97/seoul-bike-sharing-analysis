# Predicción y Análisis Multimodelo de la Demanda de Bicicletas en Seúl

Este proyecto desarrolla un flujo de trabajo analítico y predictivo para estimar el volumen de alquiler del sistema público de bicicletas en Seúl (*Rented Bike Count*). Se implementa un enfoque holístico que combina ciencia de datos clásica, modelado temporal, inferencia probabilística y computación blanda (lógica difusa y clustering difuso) para optimizar la toma de decisiones en la movilidad urbana.

---

## Resumen de Metodología y Hallazgos

### 1. Variables Clave y Patrones Temporales
* **Factores determinantes:** La **Hora del día** y la **Temperatura** son los mayores impulsores de la demanda. Las **Precipitaciones** y **Nevadas** actúan como penalizadores severos del uso del sistema.
* **Comportamiento bimodal diario:** Picos marcados en horas de alto tráfico (08:00 y 18:00 hrs), impulsados por desplazamientos laborales y académicos.
* **Estacionalidad:** Alta concentración de uso en verano y otoño, sufriendo un declive drástico durante el invierno.

### 2. Comparativa de Modelado Predictivo
* **Regresión Regularizada (Ridge vs. Lasso):** 
  * **Ridge (L2):** Maneja eficazmente la multicolinealidad de las variables meteorológicas (como la correlación entre temperatura y punto de rocío) distribuyendo los pesos entre ellas sin eliminarlas.
  * **Lasso (L1):** Forzó coeficientes a cero, actuando como selector automático de características para eliminar variables ruidosas y ofrecer un modelo más interpretable.
* **Series Temporales & Inferencia Probabilística:** Incorporación de lags temporales e inferencia bayesiana para capturar la inercia del uso en horas previas y estimar escenarios bajo incertidumbre.

### 3. Clustering Clásico vs. Difuso
* A diferencia de la segmentación rígida de K-Means, el **Clustering Difuso (Fuzzy C-Means)** asigna grados de pertenencia fraccionales a múltiples grupos. Esto permite modelar las "horas de transición" meteorológicas o de demanda, donde las condiciones operativas coinciden parcialmente con más de un perfil.
* **Lógica Difusa:** Traduce la percepción humana del clima (ej. "frío", "agradable", "bochornoso") en reglas de negocio continuas para explicar variaciones en el comportamiento de uso.

---

## Estructura del Proceso

1. **Comprensión y Calidad de Datos:** Limpieza de datos (8.760 registros), corrección de atípicos (como valores de humedad al 0%) e imputación lógica.
2. **Análisis Exploratorio (EDA):** Identificación de correlaciones, varianza de demanda y distribuciones estacionales.
3. **Ingeniería de Características:** Extracción de componentes temporales (hora, mes, día de la semana) y variables categóricas.
4. **Implementación de Modelos:** Evaluación comparativa entre regresión, series temporales, modelos bayesianos, lógica difusa y clustering.

---

## Limitaciones del Estudio

* **Granularidad espacial:** Datos agregados a nivel ciudad sin nivel de detalle por estación individual, imposibilitando el análisis de saturación local o balanceo de flota.
* **Variables omitidas:** No se incluyen indicadores de calidad del aire (PM2.5), estado del tráfico en tiempo real o interrupciones en la red de transporte público.

---

## Líneas de Trabajo Futuro

* Incorporar geolocalización por estación para desarrollar modelos de redistribución logística.
* Incluir índices de contaminación y eventos especiales en la ciudad.
* Implementar modelos de ensamble no lineales (XGBoost, Random Forest) y redes neuronales recurrentes (LSTM) para la predicción de secuencias complejas.

---
