# Proyecto Final: Segmentación No Supervisada de Alojamientos de Airbnb de la Ciudad de México

Este es el proyecto final de la primera materia de la **Maestría en Inteligencia Artificial** de la **Universidad Autónoma de Yucatán (UADY)**. Corresponde a la **Materia 1: "Introducción a la Inteligencia Artificial"**.

**Autor:** Aarón Eduardo Arceo Arjona

## Descripción

El proyecto aplica técnicas de aprendizaje no supervisado para agrupar los alojamientos de Airbnb de la Ciudad de México según sus características (ubicación, tipo de propiedad, precio, amenidades y calificaciones, entre otras). Se usa el conjunto de datos de [Inside Airbnb](https://insideairbnb.com/get-the-data/) (versión de septiembre de 2025).

El flujo de trabajo incluye:

- Limpieza y análisis exploratorio de datos (EDA).
- Reducción de dimensiones con PCA.
- Búsqueda del número óptimo de clústeres con K-Means, Gaussian Mixture Model (GMM), Clúster Jerárquico y DBSCAN.
- Visualización de los grupos en 2D.
- Perfilamiento y conclusiones por clúster.

## Contenido de la carpeta

| Archivo | Descripción |
|---|---|
| [proyecto_final_aaron_eduardo_arceo_arjona.ipynb](proyecto_final_aaron_eduardo_arceo_arjona.ipynb) | Notebook con todo el desarrollo del proyecto. **Se recomienda ejecutarla en Google Colab.** |
| [Introducción_IA_Proyecto_Aarón_Arceo_Arjona.pdf](Introducción_IA_Proyecto_Aarón_Arceo_Arjona.pdf) | Documento PDF que muestra los resultados obtenidos en la notebook. |
| [requirements.txt](requirements.txt) | Dependencias para ejecutar la notebook de forma local (Python 3.12). |

## Ejecución en Google Colab (recomendada)

1. Abrir [Google Colab](https://colab.research.google.com/) → **Archivo → Subir notebook** y seleccionar `proyecto_final_aaron_eduardo_arceo_arjona.ipynb`.
2. Ejecutar **Entorno de ejecución → Ejecutar todas**.

La primera celda de código instala las paqueterías que Colab no trae preinstaladas, y los datos (~800 MB) se descargan automáticamente desde Google Drive. Se requiere conexión a internet.

Las instrucciones para ejecutarla de forma local (Jupyter o VS Code) están al inicio de la notebook.
