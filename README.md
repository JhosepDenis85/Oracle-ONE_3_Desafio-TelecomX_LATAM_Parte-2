# 🎯 Desafío Telecom X - Parte 2: Predicción de Cancelación (Churn)

## 📋 Descripción del Proyecto

Este proyecto forma parte del **Oracle Next Education (ONE)** en colaboración con **Alura Latam**, enfocado en desarrollar un modelo predictivo robusto para anticipar qué clientes de TelecomX tienen mayor probabilidad de cancelar sus servicios (churn), permitiendo implementar estrategias de retención proactivas.

### 🎯 Objetivo Principal

Construir un sistema de Machine Learning que permita:
- Predecir con **alta precisión** (>90%) qué clientes cancelarán sus servicios
- Identificar los **factores críticos** que influyen en la cancelación
- Proponer **estrategias de retención** basadas en datos
- Generar un **ROI del 46%** en el primer año

---

## 📊 Metodología y Retos Implementados

El proyecto se estructura en **12 retos** que abarcan todo el pipeline de Machine Learning:

### 📥 A. PREPARACIÓN DE LOS DATOS (Retos 1-4)

#### **Reto 1: Extracción del Archivo Tratado**
- Carga de datos desde GitHub (CSV tratado)
- Dataset original: **7,043 clientes**
- Tasa de churn inicial: **26.58%**

#### **Reto 2: Eliminación de Columnas Irrelevantes**
- Eliminación de `customerID` (sin valor predictivo)
- Optimización del dataset para modelado

#### **Reto 3: Encoding de Variables Categóricas**
- Conversión de variable objetivo: `Churn` → binaria (0/1)
- **One-Hot Encoding** para variables categóricas
- Resultado: **40 features** para el modelo

#### **Reto 4: Verificación de Proporción de Churn**
- Análisis de desbalanceo de clases
- Ratio detectado: **2.76:1** (No Churn:Churn)
- Decisión: Aplicar técnica de balanceo SMOTE

---

### ⚙️ B. PREPROCESAMIENTO AVANZADO (Retos 5-8)

#### **Reto 5: Balanceo de Clases con SMOTE**
- Técnica: **Synthetic Minority Over-sampling Technique**
- Antes: 7,043 registros → Después: **10,796 registros**
- Balance perfecto: 50% Churn / 50% No Churn
- Inclusión de limpieza de valores NaN antes de SMOTE

#### **Reto 6: Normalización con StandardScaler**
- Estandarización de variables numéricas
- Media ≈ 0, Desviación estándar ≈ 1
- Esencial para modelos sensibles a escala (SVM, KNN, Regresión Logística)

#### **Reto 7: Análisis de Correlación**
- Matriz de correlación completa
- Identificación de Top 15 variables correlacionadas con Churn
- Visualización con heatmap

#### **Reto 8: Análisis Dirigido**
- Análisis exploratorio de variables clave:
  - **Tenure** (antigüedad): Boxplots, histogramas, KDE
  - **TotalCharges** (cargos totales): Violin plots, distribuciones
- Insights sobre patrones de comportamiento

---

### 🤖 C. MODELADO Y EVALUACIÓN (Retos 9-12)

#### **Reto 9: Separación de Datos (Train/Test)**
- Split estratificado: **70% entrenamiento** / **30% prueba**
- Train: 7,557 registros | Test: 3,239 registros
- Estratificación para mantener balance de clases

#### **Reto 10: Creación de 5 Modelos de Machine Learning**

| Modelo | Tipo | Normalizado | Tiempo Entrenamiento |
|--------|------|-------------|---------------------|
| **Logistic Regression** | Lineal | ✅ Sí | ~0.05s |
| **KNN** | Basado en instancias | ✅ Sí | ~0.01s |
| **Decision Tree** | Árbol | ❌ No | ~0.03s |
| **Random Forest** | Ensemble | ❌ No | ~0.8s |
| **SVM** | Kernel RBF | ✅ Sí | ~2.5s |

#### **Reto 11: Evaluación Exhaustiva de Modelos**

**Reto 11.a - Métricas de Rendimiento:**
- Accuracy, Precision, Recall, F1-Score
- Matrices de confusión para cada modelo
- Reportes de clasificación detallados
- Visualización comparativa de métricas

**Reto 11.b - Análisis Crítico:**
- Detección de overfitting/underfitting
- Comparación Train vs Test accuracy
- Recomendaciones de ajuste

**🏆 Resultados de Modelos:**

| Modelo | Accuracy | Precision | Recall | F1-Score |
|--------|----------|-----------|--------|----------|
| **Random Forest** 🥇 | **91.3%** | **90.8%** | **91.9%** | **91.3%** |
| Decision Tree 🥈 | 89.5% | 88.7% | 90.4% | 89.5% |
| Logistic Regression 🥉 | 81.2% | 79.8% | 83.1% | 81.4% |
| SVM | 80.9% | 79.5% | 82.7% | 81.1% |
| KNN | 78.3% | 76.2% | 81.5% | 78.8% |

#### **Reto 12: Importancia de Variables**

**Top 5 Variables Predictoras (Random Forest):**
1. **tenure** (Antigüedad del cliente) - Importancia: 0.1854
2. **TotalCharges** (Cargos totales) - Importancia: 0.1632
3. **MonthlyCharges** (Cargos mensuales) - Importancia: 0.1421
4. **Contract_Two year** (Contrato de 2 años) - Importancia: 0.0987
5. **PaymentMethod_Electronic check** - Importancia: 0.0765

**Análisis de Coeficientes (Regresión Logística):**
- Variables con coeficientes positivos (aumentan churn)
- Variables con coeficientes negativos (reducen churn)
- Visualización con gráficos de barras horizontales


---

## 🛠️ Tecnologías Utilizadas

### Lenguaje y Entorno
- **Python 3.8+**
- **Jupyter Notebook** / **Google Colab**

### Librerías de Análisis de Datos
```python
pandas==2.0+        # Manipulación de datos
numpy==1.24+        # Operaciones numéricas
```

### Librerías de Visualización
```python
matplotlib==3.7+    # Gráficos básicos
seaborn==0.12+      # Visualizaciones estadísticas
```

### Librerías de Machine Learning
```python
scikit-learn==1.3+  # Modelos, métricas, preprocesamiento
imbalanced-learn    # SMOTE (balanceo de clases)
```

### Modelos Implementados
- Logistic Regression
- K-Nearest Neighbors (KNN)
- Decision Tree Classifier
- **Random Forest Classifier** (Modelo final)
- Support Vector Machine (SVM)



