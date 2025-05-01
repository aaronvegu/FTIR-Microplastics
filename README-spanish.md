# Clasificación de Plásticos mediante FTIR y Aprendizaje Automático

Este repositorio documenta el proceso completo para clasificar tipos de plásticos utilizando datos de espectroscopía FTIR (Transformada de Fourier en el infrarrojo) y técnicas de aprendizaje automático. Incluye preprocesamiento de datos, reducción de dimensionalidad, entrenamiento de modelos y evaluación.

## 📌 Objetivo del Proyecto

Construir y validar modelos base de aprendizaje automático para clasificar tres tipos de plásticos:
- Polietileno (PE)
- Polipropileno (PP)
- Poliestireno (PS)

utilizando datos de huellas espectroscópicas extraídos de archivos `.dpt`.

## � Visión General de la Metodología

### 1. **Preparación de Datos**
- Archivos `.dpt` crudos se convierten en DataFrames estructurados.
- Se eliminan muestras con valores de absorbancia atípicos (>1.1 o <0.8).
- Los conjuntos de datos filtrados se visualizan y opcionalmente se guardan como archivos `.csv`.

### 2. **Reducción de Dimensionalidad (PCA)**
- Los espectros FTIR se escalan y reducen a 5 componentes principales.
- Los modelos PCA y StandardScaler se guardan como `.pkl` para reutilización.

### 3. **Entrenamiento de Modelos**
- Modelos entrenados: Bosque Aleatorio, SVM y Regresión Logística.
- Hiperparámetros optimizados mediante Búsqueda en Cuadrícula con validación cruzada de 5 particiones.
- Precisión evaluada en un conjunto de prueba reservado.

### 4. **Validación**
- Rendimiento validado en un conjunto etiquetado separado de muestras conocidas.
- Métricas de evaluación incluyen precisión y matriz de confusión.

### 5. **Clasificación de Muestras Desconocidas**
- Los modelos entrenados predicen sobre nuevos datos sin etiquetar.
- Se aplica un umbral de confianza; predicciones por debajo se etiquetan como "desconocido".
- Las predicciones se visualizan y exportan como `.csv`.

## 📂 Estructura de Carpetas
```
.
├── data/
│   ├── raw/                # Archivos .dpt crudos
│   ├── processed/          # CSVs limpios y reducidos con PCA
│   └── models/             # Modelos entrenados (.joblib)
├── notebooks/
│   └── FTIR_Classification.ipynb
├── pca/
│   ├── std_scaler.pkl
│   └── pca.pkl
├── predictions/
│   └── *.csv
└── README.md
```

## 📊 Resumen de Resultados

| Modelo              | Precisión CV | Precisión en Prueba | Precisión (Validación) |
|-------------------|-------------|---------------|-------------------------|
| Bosque Aleatorio      | 88.00%      | 78.95%        | Alta para PE             |
| SVM                | 41.33%      | 57.89%        | Confusión PP/PS         |
| Regresión Logística| 41.33%      | 57.89%        | Confusión PP/PS         |

- El Polietileno se clasificó con alta precisión.
- Se observó confusión entre Polipropileno y Poliestireno.

## 📈 Salidas Visuales
- Gráficos de espectros FTIR antes y después de la limpieza
- Matrices de confusión
- Gráficos de predicción basados en confianza

## 🛠️ Requisitos
```bash
pip install pandas numpy scikit-learn matplotlib joblib
```

## 📚 Referencias
- Documentación de Scikit-learn: https://scikit-learn.org/
- Microsoft AutoML: https://learn.microsoft.com/en-us/azure/machine-learning/concept-automated-ml
- Fundamentos de FTIR de Thermo Fisher: https://www.thermofisher.com

## 🔬 Contexto de Investigación
Este trabajo forma parte de un proyecto de investigación académica más amplio que investiga métodos para la clasificación de plásticos utilizando datos espectroscópicos. Para antecedentes teóricos y discusión de resultados, consulte los informes de investigación adjuntos.

## 📥 Licencia
Este repositorio se proporciona únicamente con fines académicos y de investigación. Por favor, cite adecuadamente si utiliza este material.

---

Para preguntas, contacte: `aaronvegu@gmail.com`