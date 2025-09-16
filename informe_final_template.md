# Predicción de ingreso hospitalario en urgencias con variables clínicas y de triaje

**Autora:** Ignacia Pérez  
**Fecha:** [TODO]  
**Repositorio:** [URL de tu GitHub]

---

## 1. Resumen (Abstract)
[TODO: objetivo, datos, modelo, principales resultados (accuracy, recall en Ingreso), y conclusión clínica.]

---

## 2. Introducción y Objetivo
- **Contexto clínico:** [TODO: Describe el problema en urgencias y la decisión de ingreso.]
- **Pregunta de investigación:** [TODO: ¿Podemos predecir Ingreso (sí/no) al momento del triaje?]
- **Impacto esperado:** [TODO: Gestión de camas, priorización, seguridad del paciente.]
- **Elección de modelo:** [TODO: Regresión Logística por interpretabilidad y buen recall.]

---

## 3. Datos
- **Fuente:** dataset CSV provisto (latin-1, separador `;`).
- **Tamaño:** [TODO: n filas, m columnas].
- **Variables clave:**
  - Demográficas: `Age`, `Sex`
  - Signos vitales: `SBP`, `DBP`, `HR`, `RR`, `BT`, `MAP` (derivada)
  - Triage: `KTAS_RN`, `KTAS_expert`, `Mental`, `Arrival mode`, `Group`, `Injury`, `Pain`
  - Outcome: `Admitted` (binario: ingreso vs egreso)
- **Diccionario de categorías:**  
  - `Sex`: 1=Femenino, 2=Masculino  
  - `Injury`: 1=No, 2=Sí  
  - `Pain`: 0=No, 1=Sí  
  - `Mental`: 1=Alert, 2=Verbal, 3=Pain response, 4=Unresponsive  
  - `Arrival mode`: 1=Walking, 2=Public Ambulance, 3=Private Vehicle, 4=Private Ambulance, 5–7=Other  
  - `KTAS_*`: 1–5 (1–3 emergencia; 4–5 no emergencia)  
  - `Disposition`: 1=Discharge, 2=Ward, 3=ICU, 4=Discharge, 5=Transfer, 6=Death, 7=Surgery  

---

## 4. Definición del Outcome
- **Regla:** `Admitted = 0` (Disposition 1, 4, 6 = Egreso), `Admitted = 1` (Disposition 2, 3, 5, 7 = Ingreso).  
- **Justificación clínica:** [TODO: Explica por qué muerte (6) se consideró egreso en este objetivo.]  
- **Distribución:**  

---

## 5. Preprocesamiento e Ingeniería de Atributos
- Conversión de numéricas mal tipadas (`SBP`, `DBP`, `HR`, `RR`, `BT`).  
- Variables derivadas:
  - `MAP`
  - `Hypotension (SBP<90)`
  - `Tachycardia (HR>120)`
  - `Resp_abnormal (RR<12 o >24)`
  - `Fever_or_Hypothermia (BT>38 o <35)`
  - `Elderly (Age≥65)`
- Valores faltantes: imputación mediana (numéricas), moda (categóricas).  
- Outliers: mantenidos por plausibilidad clínica.

---

## 6. Estadística Descriptiva y EDA
- **Tabla descriptiva:** [TODO: pega resumen `df.describe()`].  
- **Figuras:**  
  - Figura 1. Histogramas y boxplots iniciales de `Age`, `SBP`, `DBP`, `HR`, `RR`, `BT`.  
  - Figura 2. Boxplots por outcome (`Admitted`): `Age`, `SBP`, `DBP`, `MAP`, `HR`, `RR`, `BT`.  
- **Hallazgos:** [TODO: describe diferencias (ej. SBP más bajo y edad más alta en ingresados)].

---

## 7. Metodología
- Partición 80/20, estratificada por `Admitted`.  
- Preprocesamiento: imputación + StandardScaler (numéricas), OneHotEncoder (categóricas).  
- Modelo: Regresión Logística (`class_weight="balanced"`).  
- Métrica prioritaria: Recall en clase Ingreso.

---

## 8. Resultados
- **Reporte de clasificación:**
- **Matriz de confusión:**  
  Figura 3. [TODO: inserta la imagen]  
- **Interpretabilidad (OR):**  
  Figura 4. Forest plot — top variables.  
- **Hallazgos principales:**  
  - [TODO: ej. Llegada en ambulancia y triage severo duplican la chance de ingreso.]  
  - [TODO: SBP alta reduce la probabilidad de ingreso.]  
  - [TODO: Edad y fiebre aumentan la probabilidad de ingreso.]

---

## 9. Discusión
- Validez clínica: [TODO]  
- Uso potencial: [TODO]  
- Comparación con RandomForest: [TODO breve]  
- Limitaciones: [TODO]

---

## 10. Conclusiones
- [TODO: 2–4 bullets con mensajes clave]  
- [TODO: líneas futuras, p.ej. incluir laboratorios, NLP para chief complaint]

---

## 11. Reproducibilidad
- Cómo ejecutar:


Versiones:
  - Python: [TODO]
  - pandas: [TODO]
  - scikit-learn: [TODO]

---

## 12. Referencias
- [TODO: Guías de triaje, papers, fuentes]
