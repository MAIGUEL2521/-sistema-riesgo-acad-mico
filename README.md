# 🎓 Sistema de Clasificación de Riesgo Académico Estudiantil

## Descripción general

Este proyecto busca clasificar el nivel de rendimiento académico de estudiantes de bachillerato usando técnicas de machine learning, a partir de variables como hábitos de estudio, asistencia, participación de padres y actividades extracurriculares.

## Problema

En muchas instituciones educativas, los docentes y coordinadores no cuentan con herramientas que les permitan identificar a tiempo a los estudiantes con riesgo de bajo rendimiento. Este proyecto propone un clasificador que, a partir de datos académicos y socioeducativos, prediga la categoría de rendimiento final del estudiante (A, B, C, D o F), con el fin de apoyar decisiones de intervención temprana.

## Pregunta analítica

¿Es posible clasificar el nivel de rendimiento académico (A/B/C/D/F) de un estudiante de bachillerato a partir de variables como tiempo de estudio, asistencia, tutorías, participación de padres y actividades extracurriculares, con el fin de apoyar decisiones de intervención pedagógica temprana?

## Dataset

- **Nombre:** Students Performance Dataset
- **Fuente:** [Kaggle — Rabie El Kharoua (2024)](https://www.kaggle.com/datasets/rabieelkharoua/students-performance-dataset)
- **Licencia:** CC BY 4.0
- **Registros:** 2.392 estudiantes
- **Variables:** 15 columnas (14 de entrada + 1 objetivo)
- **Variable objetivo:** `GradeClass` (0=A, 1=B, 2=C, 3=D, 4=F)

## Estructura del repositorio

```
├── README.md
├── .gitignore
├── requirements.txt
├── data/
│   └── raw/
│       └── students_performance.csv
├── notebooks/
│   └── 01_exploracion.ipynb
└── docs/
    ├── ficha_proyecto.md
    ├── analisis_dataset.md
    └── wireframe_dashboard.png
```

## Tipo de tarea

- **Tarea:** Clasificación multiclase
- **Métrica principal:** F1-score macro
- **Justificación:** Las clases presentan desbalance leve; el F1-score macro garantiza que todas las categorías sean evaluadas con igual peso, evitando que las clases mayoritarias dominen la evaluación.

## Usuario final

Coordinadores académicos y docentes de bachillerato que necesitan identificar estudiantes en riesgo antes de que finalice el periodo académico.

## Tecnologías

- Python 3.11
- pandas, numpy, scikit-learn, matplotlib, seaborn
- Jupyter Notebook
- Streamlit (dashboard — entregas posteriores)

## Instalación

```bash
pip install -r requirements.txt
```

## Autor

Estudiante — Diplomado en Desarrollo Web para Analítica de Datos  
Programa: Tecnología en Desarrollo de Software  
Fecha: Junio 2026
