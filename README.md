# 📊 Customer Churn Prediction — Machine Learning Project

Este proyecto implementa un modelo de **Machine Learning** para predecir el abandono de clientes (*churn*) en una empresa de telecomunicaciones. Se desarrolla un pipeline completo, desde el análisis exploratorio hasta la evaluación final del modelo, incorporando buenas prácticas profesionales como validación cruzada, pruebas de cordura y optimización del threshold. Proyecto educativo personal.

El objetivo principal del proyecto fue superar un **AUC-ROC ≥ 0.88** en el conjunto de prueba.  
El modelo final alcanzó un **AUC-ROC de 0.903**.

---

## 🚀 1. Objetivo del Proyecto

Interconnect, un operador de telecomunicaciones, busca identificar clientes en riesgo de abandonar el servicio para ofrecerles planes de retención personalizados. El objetivo del proyecto es:

- Construir un modelo predictivo de churn estable y explicable.
- Evaluar distintos algoritmos de ML.
- Optimizar su capacidad para detectar clientes en riesgo (Recall).
- Cumplir con la métrica objetivo: **AUC-ROC ≥ 0.88**.

---

## 📁 2. Contenido del Repositorio

- `customer_churn_prediction.ipynb` → Notebook completo con el pipeline end-to-end.  
- `datasets` → Datasets utilizados.  
- `README.md` → Documentación del proyecto.  

---

## 🧠 3. Dataset

El proyecto utiliza cuatro fuentes:

- `contract.csv` → Información contractual  
- `personal.csv` → Datos demográficos  
- `internet.csv` → Servicios de internet  
- `phone.csv` → Servicios telefónicos  

Cada archivo contiene la columna **customerID**, usada como clave para unir los datasets.

---

## 🔍 4. Metodología

El pipeline completo incluye:

### ✔️ Exploración de Datos (EDA)
- Análisis univariado y bivariado.
- Relación entre churn y variables demográficas, contractuales y de servicios.
- Identificación de características con mayor correlación con abandono.

### ✔️ Preparación de Datos
- Limpieza de valores nulos (`TotalCharges` conversion).
- Conversión de tipos de datos.
- Unificación de tablas.
- Codificación categórica:
  - OHE para modelos lineales
  - Manejo nativo para CatBoost / LightGBM
- División en **Train / Validation / Test**.

### ✔️ Modelado
Modelos evaluados:

| Modelo | AUC Validation |
|--------|----------------|
| **CatBoost** | **0.922** |
| LightGBM | 0.912 |
| Random Forest | 0.878 |
| Logistic Regression | 0.873 |
| Decision Tree | 0.869 |

CatBoost fue seleccionado como modelo final.

### ✔️ Pruebas de Cordura
- **DummyClassifier** → AUC ≈ 0.50  
- **Etiquetas aleatorias** → AUC ≈ 0.51  

Ambas pruebas confirman ausencia de *data leakage*.

### ✔️ Validación Cruzada
- CV AUC: **0.9078**

### ✔️ Optimización de Hiperparámetros
Se utilizó **RandomizedSearchCV** para optimizar:
- `depth`  
- `learning_rate`  
- `iterations`  
- `l2_leaf_reg`  
- `border_count`  

### ✔️ Optimización del Threshold
Se evaluaron 50 thresholds entre 0.1 y 0.9 para maximizar Recall y F1.

---

## 📈 5. Resultados del Modelo Final

Tras entrenar con el conjunto Train+Validation y evaluar en Test:

| Métrica | Valor |
|--------|--------|
| **AUC-ROC** | **0.903** |
| Accuracy | 0.8578 |
| Recall (t = 0.5) | 0.609 |
| F1-Score | 0.698 |
| Recall optimizado | **0.70** |

### 🔥 Mejora tras optimizar threshold

- Churners detectados: **173 → 200**  
- Falsos negativos reducidos: **111 → 84**  
- Solo aumentaron **21** falsos positivos

Esto representa un beneficio directo para estrategias de retención.

---

## 🏆 6. Conclusiones

- El modelo final **supera ampliamente la métrica objetivo** (AUC ≥ 0.88).  
- CatBoost demostró ser el algoritmo más estable y eficiente para este tipo de datos heterogéneos.  
- El proyecto implementa prácticas avanzadas como validación cruzada, pruebas de cordura y tuning inteligente.  
- La optimización del threshold permite adaptar el modelo a las necesidades del negocio (priorizar recall).  
- El pipeline es sólido, modular y adecuado para despliegue en producción.

---

## 📌 7. Tecnologías Utilizadas

- **Python**
- Pandas, NumPy  
- Scikit-Learn  
- CatBoost  
- LightGBM  
- Matplotlib, Seaborn  
- Jupyter Notebook  

---

## 👨‍💻 8. Autor

**Javier Andrés Díaz Charry**  
Data Science & Machine Learning  
📍 Huesca, España  
🔗 LinkedIn: *[www.linkedin.com/in/javier-andres-diaz-data-scientist]*

---

## ⭐ Notebook Completo

El notebook con todo el análisis y visualizaciones se encuentra en el archivo principal del repositorio.

