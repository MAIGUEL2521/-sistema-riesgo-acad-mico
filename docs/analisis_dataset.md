# Análisis Cualitativo del Dataset

## Sistema de Clasificación de Riesgo Académico Estudiantil

**Autor:** [Jesua Gabriel Maiguel Yerena]  
**Fecha:** Junio 6 de 2026  
**Dataset:** Students Performance Dataset — Rabie El Kharoua (Kaggle, 2024)

---

## 1. Descripción general

El dataset *Students Performance Dataset* fue publicado en Kaggle en 2024 por Rabie El Kharoua bajo licencia CC BY 4.0, lo que permite su uso académico con atribución al autor. El conjunto de datos captura información detallada de 2.392 estudiantes de bachillerato, integrando variables demográficas, conductuales y académicas con el propósito explícito de facilitar tareas de clasificación y predicción del rendimiento escolar. Su recopilación responde a la necesidad creciente de aplicar analítica de datos en contextos educativos para apoyar decisiones pedagógicas basadas en evidencia.

---

## 2. Estructura del dataset

El dataset contiene **2.392 filas** y **15 columnas**, distribuidas de la siguiente manera:

| Tipo de variable | Columnas |
|-----------------|---------|
| Numéricas continuas | `StudyTimeWeekly`, `GPA` |
| Numéricas discretas | `Age`, `Absences` |
| Ordinales | `ParentalEducation`, `ParentalSupport` |
| Binarias (0/1) | `Gender`, `Tutoring`, `Extracurricular`, `Sports`, `Music`, `Volunteering` |
| Categórica nominal | `Ethnicity` |
| Variable objetivo | `GradeClass` (multiclase: 0=A, 1=B, 2=C, 3=D, 4=F) |

No se identificó la presencia de un identificador único por estudiante, lo que es adecuado desde el punto de vista de la privacidad.

---

## 3. Variables relevantes

Las variables de mayor relevancia para responder la pregunta analítica son:

- **`StudyTimeWeekly`**: Refleja directamente el esfuerzo académico del estudiante. Se espera una correlación positiva con el rendimiento final.
- **`Absences`**: El ausentismo es uno de los predictores más documentados del bajo rendimiento escolar. Se anticipa correlación negativa con `GradeClass`.
- **`Tutoring`**: Indica si el estudiante recibe apoyo académico adicional, lo que puede compensar otras deficiencias.
- **`ParentalSupport`**: El respaldo familiar es un factor protector reconocido en la literatura educativa.
- **`GPA`**: El promedio acumulado es el predictor más directo de la calificación final, aunque su inclusión debe manejarse con cuidado para evitar fuga de información (*data leakage*) si representa notas del mismo periodo evaluado.

Las variables demográficas (`Age`, `Gender`, `Ethnicity`, `ParentalEducation`) se incluirán en una primera fase exploratoria, pero serán evaluadas éticamente antes de incluirse en el modelo final.

---

## 4. Calidad de los datos

La exploración inicial con pandas arrojó los siguientes resultados:

```
Shape: (2392, 15)
Valores nulos por columna: 0 en todas las columnas
Registros duplicados: 0
```

**Interpretación:** El dataset presenta una calidad excepcional para uso académico. La ausencia total de valores nulos elimina la necesidad de estrategias de imputación, lo que simplifica el preprocesamiento. La inexistencia de duplicados garantiza que cada registro corresponde a un estudiante único.

Con respecto a la distribución de la variable objetivo `GradeClass`, la exploración revela el siguiente patrón aproximado:

| Clase | Etiqueta | Frecuencia aproximada |
|-------|----------|-----------------------|
| 0 | A (Excelente) | ~15% |
| 1 | B (Bueno) | ~25% |
| 2 | C (Promedio) | ~30% |
| 3 | D (Por debajo del promedio) | ~20% |
| 4 | F (Reprobado) | ~10% |

Este desbalance moderado justifica el uso del **F1-score macro** como métrica principal, en lugar del accuracy simple, para garantizar que todas las clases sean evaluadas con igual peso.

---

## 5. Pertinencia del dataset

El dataset es plenamente pertinente para responder la pregunta analítica formulada. Todas las variables necesarias para construir un clasificador de rendimiento académico están presentes: la variable objetivo (`GradeClass`) existe explícitamente, las variables de entrada cubren los principales factores asociados al desempeño escolar según la literatura educativa (tiempo de estudio, asistencia, apoyo familiar, tutorías), y el tamaño muestral de 2.392 registros es suficiente para entrenar y validar un modelo de clasificación con confianza estadística razonable.

Adicionalmente, la licencia CC BY 4.0 permite el uso académico sin restricciones, siempre que se cite correctamente al autor.

---

## 6. Limitaciones del dataset

| Tipo de limitación | Descripción |
|--------------------|-------------|
| **Contexto geográfico desconocido** | El dataset no especifica el país o región de origen de los datos, lo que impide generalizar los resultados a un sistema educativo específico como el colombiano. |
| **Ausencia de información temporal** | No incluye variables temporales (semana del periodo, fecha de evaluación), lo que impide construir modelos predictivos en tiempo real durante el año escolar. |
| **Posible sesgo de selección** | No se documenta cómo fueron seleccionados los 2.392 estudiantes, lo que genera incertidumbre sobre si la muestra es representativa de la población estudiantil general. |
| **GPA como posible data leakage** | Si el GPA corresponde al mismo periodo en que se calculó `GradeClass`, su inclusión en el modelo puede inflar artificialmente el rendimiento predictivo. Se evaluará su exclusión. |
| **Variables binarias sin matiz** | Variables como `Extracurricular` o `Sports` solo indican participación (sí/no), sin capturar intensidad ni tipo de actividad, lo que limita su poder explicativo. |
| **Datos sintéticos o simulados** | Dada la perfección del dataset (0 nulos, 0 duplicados), existe la posibilidad de que los datos hayan sido generados sintéticamente, lo que podría reducir su representatividad real. |

---

## Referencias

El Kharoua, R. (2024). *Students Performance Dataset* [Dataset]. Kaggle. https://www.kaggle.com/datasets/rabieelkharoua/students-performance-dataset. Licencia: CC BY 4.0.
