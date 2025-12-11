# 📊 Predicción de Cancelación de Clientes

Este proyecto desarrolla y compara distintos modelos de **clasificación** para predecir la **cancelación de clientes** (churn). El enfoque se centra en obtener el mejor rendimiento posible optimizando la métrica **AUC ROC**, utilizando técnicas avanzadas de preprocesamiento, balanceo, validación y tuning.

---

## 🚀 Objetivo del Proyecto
Predecir si un cliente cancelará su servicio (0/1) mediante modelos de machine learning que maximicen AUC ROC.  
Se implementó un flujo completo desde EDA hasta evaluación final, garantizando un proceso reproducible y libre de fugas de información.

---

## 🛠️ Pasos Realizados

### ✔️ Preparación y Análisis
- Carga y unión de datos por **CustomerID**.  
- Preprocesamiento y creación de la variable objetivo.  
- Exploratory Data Analysis (EDA).  
- División en **train / validación / test**.  

### ✔️ Modelado
- Creación de **pipelines** para evitar data leakage.  
- Entrenamiento de modelos:
  - Dummy  
  - Random Forest  
  - LightGBM  
- Aplicación de **SMOTE** para balanceo de clases.  
- Ajuste de hiperparámetros con **RandomizedSearchCV + validación cruzada estratificada**.  

### ✔️ Evaluación
- Métricas: **AUC ROC**, Accuracy.  
- Curvas ROC para comparar modelos.  

---

## ⚙️ Dificultades y Soluciones

### 🔹 Pipeline complejo  
Se organizaron etapas combinadas de preprocesamiento + SMOTE + modelo dentro de pipelines modulares para mantener el flujo limpio y reproducible.

### 🔹 Prevención de data leakage  
Todo escalado, codificación y balanceo se ajustó **solo con datos de entrenamiento** mediante pipelines correctamente estructurados.

### 🔹 Compatibilidad de funciones de evaluación  
Se creó una función estándar capaz de evaluar tanto modelos básicos como tunings, asegurando métricas consistentes.

---

## ⭐ Resultados de Modelos

| Modelo | Configuración | AUC (Validación) | Accuracy |
|-------|---------------|------------------|----------|
| Dummy | Base | 0.5000 | 0.7346 |
| RandomForest | Base | 0.9206 | 0.8772 |
| LightGBM | Base | 0.9580 | 0.9375 |
| RandomForest + SMOTE | Balanceado | 0.9161 | 0.8730 |
| LightGBM + SMOTE | Balanceado | 0.9617 | 0.9432 |
| RF + SMOTE + Tuning | Optimizado | 0.9168 | 0.8779 |
| LightGBM + SMOTE + Tuning | Optimizado | **0.9643** | **0.9454** |

---

## 🏆 Modelo Final Seleccionado
**LightGBM + SMOTE + Tuning**

### 📈 Rendimiento en Test:
- **AUC:** 0.9640  
- **Accuracy:** 0.9390  

---

## 📌 Conclusiones
- **LightGBM** fue el modelo con mejor desempeño general, combinando precisión y rapidez.  
- **SMOTE** mejoró ligeramente los resultados, confirmando un desbalance moderado en las clases.  
- El tuning con RandomizedSearchCV incrementó la estabilidad y rendimiento del modelo.  
- El uso de **pipelines modulares** garantiza reproducibilidad, escalabilidad y evita data leakage.

---
