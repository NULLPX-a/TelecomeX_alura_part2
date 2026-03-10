# 📊 Telecom X - Parte 2: Predicción de Churn con Machine Learning

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/)
[![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-1.0+-orange.svg)](https://scikit-learn.org/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

Este proyecto desarrolla un pipeline completo de Machine Learning para predecir la cancelación de clientes (**Churn**) en una empresa de telecomunicaciones. Basado en el desafío **Telecom X (Alura/LATAM)**, el objetivo es identificar proactivamente a los clientes en riesgo y proponer estrategias de retención basadas en datos.

## 🎯 Objetivos del Proyecto

1.  **Preprocesamiento Robusto**: Limpieza, encoding (One-Hot) y estandarización de datos.
2.  **Manejo de Desbalance**: Aplicación de técnica **SMOTE** para corregir la distribución desigual de clases (Ratio 2.77:1).
3.  **Modelado Comparativo**: Entrenamiento y evaluación de dos algoritmos contrastantes:
    *   **Regresión Logística** (Modelo lineal, sensible a escala).
    *   **Random Forest** (Modelo basado en árboles, no sensible a escala).
4.  **Interpretabilidad**: Análisis de coeficientes e importancia de variables para entender los "porqués" del churn.
5.  **Estrategia de Negocio**: Generación de recomendaciones accionables para reducir la tasa de cancelación.

---

## 🚀 Resultados Clave

### 🏆 Modelo Seleccionado: Regresión Logística
Aunque Random Forest obtuvo una mayor *Accuracy* general (77.1%), se seleccionó la **Regresión Logística** como modelo principal debido a su superior capacidad de detección de riesgos (**Recall = 79.5%**). En negocios de retención, es crítico minimizar los falsos negativos (clientes que se van y no detectamos).

| Métrica | Regresión Logística | Random Forest |
| :--- | :---: | :---: |
| **Accuracy** | 74.5% | **77.1%** |
| Precision | 51.3% | 55.5% |
| **Recall (Churn)** | **79.5%** ✅ | 70.4% |
| F1-Score | 62.3% | 62.1% |

### 🔍 Factores Críticos Identificados
El análisis de variables reveló patrones claros consensuados por ambos modelos:

*   🔴 **Mayores Riesgos**:
    *   Servicio de **Fibra Óptica** (posibles problemas de calidad/precio).
    *   Método de pago **Electronic Check**.
    *   Contratos **Month-to-Month**.
    *   Facturación total alta.
*   🟢 **Mayores Protectores**:
    *   **Antigüedad (Tenure)**: La variable más importante. Los primeros meses son críticos.
    *   Contratos a **2 Años**.
    *   Servicios agregados: **Tech Support** y **Online Security**.

---

## 🛠️ Tecnologías Utilizadas

*   **Lenguaje**: Python 3.8+
*   **Manipulación de Datos**: Pandas, NumPy
*   **Machine Learning**: Scikit-Learn, Imbalanced-Learn (SMOTE)
*   **Visualización**: Matplotlib, Seaborn
*   **Entorno**: Google Colab / Jupyter Notebook

---

## 📂 Estructura del Notebook

El proyecto está diseñado para ejecutarse **celda por celda** en orden secuencial:

1.  **Imports & Configuración**: Carga de librerías y supresión de warnings.
2.  **Carga de Datos**: Lectura del dataset tratado (CSV/JSON).
3.  **Limpieza**: Eliminación de IDs y columnas redundantes.
4.  **Preprocesamiento**: Detección de tipos y configuración de `ColumnTransformer` (Escalado + OneHot).
5.  **Análisis Exploratorio (EDA)**: Matrices de correlación y boxplots para identificar patrones iniciales.
6.  **División de Datos**: Split 70/30 estratificado.
7.  **Balanceo**: Integración de SMOTE dentro del Pipeline.
8.  **Entrenamiento**: Ejecución de Regresión Logística y Random Forest.
9.  **Evaluación**: Cálculo de métricas (Accuracy, Precision, Recall, F1) y Matrices de Confusión.
10. **Interpretabilidad**: Extracción de coeficientes (RegLog) e Importancia de Features (RF).
11. **Informe Ejecutivo**: Generación automática de conclusiones y estrategias de negocio.

---

## 💡 Estrategias de Retención Propuestas

Basado en los resultados del modelo, se recomiendan las siguientes acciones:

1.  **Onboarding Reforzado**: Contactar activamente a clientes nuevos (<6 meses) con Fibra Óptica para asegurar satisfacción temprana.
2.  **Migración de Contratos**: Incentivar el cambio de contratos mensuales a anuales con descuentos o upgrades, aprovechando el alto poder protector de los contratos largos.
3.  **Bundles de Seguridad**: Incluir *Tech Support* y *Online Security* gratuitamente en los paquetes de Fibra para aumentar la "pegajosidad" del servicio.
4.  **Cambio de Método de Pago**: Promover el débito automático sobre el cheque electrónico para reducir la fricción de cancelación.

---

## 📥 Cómo Usar

### Opción A: Google Colab (Recomendado)
1.  Abre el notebook `.ipynb` en Google Colab.
2.  Asegúrate de tener el archivo de datos (`tu_archivo_tratado.csv`) subido a tu Drive o en la sesión local.
3.  Ejecuta la celda de instalación si es necesario:
    ```bash
    !pip install imbalanced-learn
    ```
4.  Ejecuta las celdas secuencialmente (Shift+Enter).

### Opción B: Local (Jupyter Lab/VS Code)
1.  Clona este repositorio.
2.  Crea un entorno virtual e instala las dependencias:
    ```bash
    pip install pandas numpy scikit-learn imbalanced-learn matplotlib seaborn jupyter
    ```
3.  Coloca tu archivo CSV en la misma carpeta.
4.  Abre el notebook y ejecuta las celdas.

---

## Autor y Licencia
**NULLPX-a**  
[GitHub](https://github.com/NULLPX-a)

**Desafío:** Alura LatAm - TelecomX Challenge

Licencia: MIT

---
