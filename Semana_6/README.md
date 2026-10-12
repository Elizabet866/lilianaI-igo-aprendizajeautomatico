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
