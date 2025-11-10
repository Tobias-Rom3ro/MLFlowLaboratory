# 🧑‍💻 MLflow Laboratory - Tracking de Modelos ML y LLMs

[![MLflow](https://img.shields.io/badge/MLflow-0194E2?style=flat&logo=mlflow&logoColor=white)](https://mlflow.org/)
[![Python](https://img.shields.io/badge/Python-3.8+-3776AB?style=flat&logo=python&logoColor=white)](https://www.python.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=flat&logo=jupyter&logoColor=white)](https://jupyter.org/)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat&logo=scikit-learn&logoColor=white)](https://scikit-learn.org/)

> **Proyecto Educativo**: Introducción práctica a MLflow para tracking, registro y comparación de modelos de Machine Learning tradicionales y Modelos de Lenguaje (LLMs).

**Autores**: Tobías Romero (2021214011) y Jenifer Roa (2022214006)

---

## 🎯 Descripción del Proyecto

Este proyecto es un laboratorio educativo que demuestra el uso de **MLflow** para el ciclo de vida completo de modelos de machine learning, dividido en dos partes principales:

### Parte I: Modelos de ML Clásicos
Entrenamiento y registro de modelos de **Regresión Logística** para clasificación de cáncer de mama utilizando el dataset Wisconsin Breast Cancer. Incluye:
- Pipeline de preprocesamiento con StandardScaler
- Comparación de hiperparámetros
- Registro completo de métricas y artefactos
- Visualizaciones de matriz de confusión y curva ROC

### Parte II: Modelos de Lenguaje (LLMs)
Comparación sistemática entre **Gemini 2.0** y **DeepSeek** en múltiples tareas de NLP:
- Escritura creativa
- Generación de código
- Respuestas técnicas
- Resumen de información
- Traducción

---

## ✨ Características

- 🔬 **Experimentos Reproducibles**: Seeds fijas y configuración controlada
- 📊 **Tracking Completo**: Hiperparámetros, métricas y artefactos en MLflow
- 🎨 **Visualizaciones**: Matrices de confusión, curvas ROC y métricas comparativas
- 🤖 **Integración LLMs**: Llamadas a APIs de Google (Gemini) y OpenRouter (DeepSeek)
- 📝 **Documentación Detallada**: Notebooks con explicaciones paso a paso
- 🏷️ **Versionado de Modelos**: Registro automático en MLflow Model Registry
- 📦 **Dataset Tracking**: Uso de `mlflow.data` para versionar datos

---

## 📁 Estructura del Proyecto

```
MLFlowLaboratory/
│
├── notebooks/
│   ├── Registro de Modelos de ML.ipynb       # Parte I: ML Clásico
│   └── Registro de Modelos LLM.ipynb         # Parte II: LLMs
│
├── mlruns/                                     # Directorio de tracking MLflow
│
├── .env.example                                # Plantilla de variables de entorno
├── .gitignore                                  # Archivos ignorados por Git
├── requirements.txt                            # Dependencias del proyecto
└── README.md                                   # Este archivo
```

---

## 🔧 Requisitos Previos

- **Python**: 3.8 o superior
- **Jupyter Notebook** o **JupyterLab**
- **API Keys** (para la Parte II):
  - Google AI (Gemini)
  - OpenRouter (DeepSeek)

---

## 🚀 Instalación

### 1. Clonar el repositorio

```bash
git clone https://github.com/tu-usuario/MLFlowLaboratory.git
cd MLFlowLaboratory
```

### 2. Crear entorno virtual (recomendado)

```bash
# Con venv
python -m venv venv
source venv/bin/activate  # En Windows: venv\Scripts\activate

# O con conda
conda create -n mlflow-lab python=3.10
conda activate mlflow-lab
```

### 3. Instalar dependencias

```bash
pip install -r requirements.txt
```

---

## ⚙️ Configuración

### Para la Parte II (LLMs)

1. **Copiar el archivo de ejemplo**:
   ```bash
   cp .env.example .env
   ```

2. **Editar `.env` con tus API keys**:
   ```env
   GOOGLE_API_KEY=tu_api_key_de_google
   OPENROUTER_API_KEY=tu_api_key_de_openrouter
   OLLAMA_HOST=http://localhost:11434  # Opcional si usas Ollama
   ```

3. **Obtener API Keys**:
   - **Google AI**: [https://makersuite.google.com/app/apikey](https://makersuite.google.com/app/apikey)
   - **OpenRouter**: [https://openrouter.ai/keys](https://openrouter.ai/keys)

---

## 💻 Uso

### Iniciar Jupyter Notebook

```bash
jupyter notebook
```

### Ejecutar los Notebooks

1. **Parte I** - Modelos de ML:
   - Abrir `notebooks/Registro de Modelos de ML.ipynb`
   - Ejecutar las celdas secuencialmente
   - Los experimentos se registrarán en `mlruns/`

2. **Parte II** - LLMs:
   - Abrir `notebooks/Registro de Modelos LLM.ipynb`
   - Asegurarse de tener las API keys configuradas
   - Ejecutar las celdas secuencialmente

### Ver Resultados en MLflow UI

```bash
mlflow ui
```

Luego abrir [http://localhost:5000](http://localhost:5000) en tu navegador.

---

## 📓 Notebooks

### 1. Registro de Modelos de ML

**Objetivo**: Demostrar el tracking básico de MLflow con modelos scikit-learn

**Contenido**:
- Carga y exploración del dataset Wisconsin Breast Cancer
- División train/test estratificada
- Pipeline con StandardScaler + LogisticRegression
- Dos experimentos con diferentes hiperparámetros:
  - **Baseline** (C=1.0, solver='lbfgs')
  - **Optimizado** (C=0.1, solver='saga')
- Registro completo de métricas, parámetros y artefactos
- Visualizaciones guardadas como artefactos

### 2. Registro de Modelos LLM

**Objetivo**: Comparar modelos LLM en tareas diversas con tracking de costos y latencia

**Contenido**:
- Configuración de APIs (Gemini y DeepSeek)
- 5 tareas de evaluación:
  1. Escritura creativa (cuento de ciencia ficción)
  2. Generación de código (búsqueda binaria)
  3. Respuesta a preguntas técnicas (aprendizaje por refuerzo)
  4. Resumen (principios de POO)
  5. Traducción (ES → EN)
- Métricas tracked:
  - Latencia (segundos)
  - Tokens de entrada/salida
  - Palabras por segundo
  - Longitud de respuesta
- Artefactos guardados:
  - Prompts originales
  - Respuestas completas
  - Metadata del experimento (JSON)

---

## 🤖 Modelos Implementados

### Machine Learning Clásico

| Modelo | Dataset | Algoritmo | Accuracy | F1-Score | ROC-AUC |
|--------|---------|-----------|----------|----------|---------|
| Baseline | Breast Cancer | LogisticRegression (C=1.0) | 0.9825 | 0.9861 | 0.9954 |
| Optimizado | Breast Cancer | LogisticRegression (C=0.1) | 0.9737 | 0.9793 | 0.9957 |

### Modelos de Lenguaje

| Modelo | Provider | Versión | Tareas Evaluadas |
|--------|----------|---------|------------------|
| Gemini | Google AI | 2.0-flash-exp | 5 |
| DeepSeek | OpenRouter | v3.1:free | 5 |

---

## 📊 Métricas y Visualizaciones

### ML Clásico
- **Accuracy**: Porcentaje de predicciones correctas
- **Precision**: Tasa de verdaderos positivos
- **Recall**: Sensibilidad del modelo
- **F1-Score**: Media armónica de precision y recall
- **ROC-AUC**: Área bajo la curva ROC

**Visualizaciones**:
- Matriz de confusión (heatmap)
- Curva ROC con AUC
- Reporte de clasificación

### LLMs
- **Latencia**: Tiempo de respuesta en segundos
- **Tokens**: Input/output/total
- **Velocidad**: Palabras por segundo
- **Longitud**: Caracteres de respuesta
- **Success Rate**: Tasa de éxito de llamadas

---

## 📈 Resultados

### Parte I: Modelos de ML

El modelo **baseline** logró un desempeño ligeramente superior en accuracy (98.25%) comparado con el modelo optimizado (97.37%), aunque ambos mostraron excelente capacidad de generalización con ROC-AUC superior a 0.99.

**Hallazgos clave**:
- La regularización más fuerte (C=0.1) reduce mínimamente el overfitting
- El solver 'lbfgs' es más eficiente para este problema
- Ambos modelos son production-ready

### Parte II: LLMs

Comparación pendiente de análisis detallado de las respuestas por tarea. Los experimentos están registrados en MLflow con todas las métricas de latencia y consumo de tokens.

---

## 🛠️ Tecnologías Utilizadas

### Core
- **MLflow**: Tracking de experimentos y registro de modelos
- **Python**: Lenguaje de programación principal
- **Jupyter**: Entorno interactivo de desarrollo

### Machine Learning
- **scikit-learn**: Modelos de ML clásicos
- **NumPy**: Operaciones numéricas
- **Pandas**: Manipulación de datos

### Visualización
- **Matplotlib**: Gráficos estáticos
- **Seaborn**: Visualizaciones estadísticas

### LLMs
- **google-generativeai**: API de Gemini
- **openai**: Cliente para OpenRouter
- **python-dotenv**: Gestión de variables de entorno

---

## 🤝 Contribuciones

Este es un proyecto educativo. Si encuentras errores o tienes sugerencias:

1. Abre un **Issue** describiendo el problema/mejora
2. Si quieres contribuir código:
   - Haz un fork del repositorio
   - Crea una rama (`git checkout -b feature/mejora`)
   - Commit tus cambios (`git commit -m 'Añade nueva característica'`)
   - Push a la rama (`git push origin feature/mejora`)
   - Abre un Pull Request

---

## 📧 Contacto

**Tobías Romero** - 2021214011  
**Jenifer Roa** - 2022214006

**Proyecto**: [MLFlowLaboratory](https://github.com/Tobias-Rom3ro/MLFlowLaboratory)

---

## 📜 Créditos.

- Dataset Wisconsin Breast Cancer de [scikit-learn](https://scikit-learn.org/)
- Documentación oficial de [MLflow](https://mlflow.org/docs/latest/index.html)
- Comunidad de MLOps y Open Source

---
