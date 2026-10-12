# Semana 6 - Clasificación Supervisada: Árbol de Decisión vs. SVM

## 📌 Descripción del Proyecto
En esta entrega se aborda la predicción temprana del riesgo de abandono escolar universitario (*Dropout*) frente a la continuidad de los estudios utilizando técnicas de Machine Learning supervisado. 

El dataset seleccionado proviene del repositorio de la Universidad de California en Irvine (UCI ID: 697), registrando atributos sociodemográficos y de rendimiento académico de 4.424 estudiantes de educación superior politécnica de Portugal.

---

## 🎯 Pregunta Analítica y Objetivo
* **Pregunta:** ¿En qué medida las variables académicas del primer y segundo semestre (materias aprobadas y calificaciones), junto a factores socioeconómicos y demográficos clave (edad, género, becas, deudas de arancel y turno), permiten predecir de forma efectiva la probabilidad de deserción escolar frente a la continuidad de los estudios?
* **Objetivo:** Entrenar, evaluar y comparar dos modelos de clasificación supervisada (**Árbol de Decisión** con poda en profundidad y **SVM con Kernel RBF**), priorizando la sensibilidad métrica (**Recall**) y la **interpretabilidad institucional** orientada a la toma de decisiones pedagógicas y de retención estudiantil.

---

## 📂 Estructura de la Carpeta
```text
Semana_6/
├── Datos/
│   └── students_dropout.csv               # Dataset procesado y exportado
├── Notebooks/
│   └── Presentación_AA_Semana_6.ipynb     # Notebook completo con análisis, modelos y visualización
└── README.md                              # Documentación del proyecto
## 🔍 Variables Utilizadas en el Análisis

### Variables Predictoras ($X$):
* **Académicas / Numéricas:**
  * `Curricular units 1st sem (approved)`: Asignaturas aprobadas en el primer semestre.
  * `Curricular units 1st sem (grade)`: Promedio de calificaciones en el primer semestre.
  * `Curricular units 2nd sem (approved)`: Asignaturas aprobadas en el segundo semestre.
  * `Curricular units 2nd sem (grade)`: Promedio de calificaciones en el segundo semestre.
  * `Age at enrollment`: Edad del alumno al momento de la inscripción.
* **Sociodemográficas / Categóricas:**
  * `Scholarship holder`: Condición de estudiante becado (1: Sí, 0: No).
  * `Debtor`: Deuda registrada en cuotas o aranceles (1: Sí, 0: No).
  * `Gender`: Género del estudiante (1: Masculino, 0: Femenino).
  * `Daytime/evening attendance`: Turno de cursada (1: Diurno, 0: Vespertino).

### Variable Objetivo ($y$):
* `Target_binario`: Trayectoria del estudiante (1: Abandono / *Dropout*, 0: Continuidad / *Graduate* o *Enrolled*).
## 📊 Resultados y Evaluación Comparativa

Evaluación sobre el conjunto de test (25% estratificado, 1.106 muestras):

| Métrica | Árbol de Decisión (`max_depth=4`) | SVM (`kernel='rbf'`) |
| :--- | :---: | :---: |
| **Accuracy** | **0.854** | 0.847 |
| **Precision (Dropout)** | 0.812 | **0.850** |
| **Recall (Dropout)** | **0.707** | 0.637 |
| **F1-Score (Dropout)** | **0.756** | 0.728 |

> **Matriz de Confusión:** El Árbol de Decisión minimiza los falsos negativos a **104** (frente a **129** de SVM), identificando a 251 alumnos en riesgo.
## 🛠️ Tecnologías y Requisitos

* **Lenguaje:** Python 3.10+
* **Librerías principales:**
  * `pandas`, `numpy` (Manipulación de datos)
  * `matplotlib`, `seaborn` (Visualización de datos)
  * `scikit-learn` (Modelado, escalado y evaluación)
  * `ucimlrepo` (Extracción oficial del dataset)

### Ejecución:
1. Clonar el repositorio o descargar el notebook ubicado en `Semana_6/Notebooks/`.
2. Abrir en Google Colab o JupyterLab.
3. Ejecutar las celdas secuencialmente para replicar los entrenamientos y gráficos.
