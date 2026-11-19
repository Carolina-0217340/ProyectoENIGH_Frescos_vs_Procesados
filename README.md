# Frescos vs. procesados: ¿en qué gastan en comida los hogares mexicanos? (ENIGH 2024)

Análisis del gasto en alimentos frescos y procesados en hogares mexicanos con la Encuesta Nacional de Ingresos y Gastos de los Hogares (ENIGH) 2024 del INEGI. Incluye estadística descriptiva, contraste de hipótesis, reducción de dimensionalidad y modelos de clasificación en Python.

**Autora:** Carolina Hurtado
**Curso:** Visualización de Datos y Narración de Historias

## Pregunta

¿Qué proporción de su gasto en alimentos destinan los hogares mexicanos a productos frescos frente a procesados, y cómo cambia según el estrato socioeconómico, el tamaño de la localidad y el ingreso?

## Resultados principales

- Los hogares destinan alrededor de **69%** de su gasto en alimentos a frescos (razón de totales ponderados).
- La diferencia entre entidades es de unos 21 puntos: de 77.1% en Tlaxcala a 56.1% en Nuevo León.
- Los hogares de localidades más pequeñas gastan más en frescos. Los de estratos e ingresos más altos gastan menos; en ambos casos el efecto es pequeño.
- El mejor modelo para predecir qué hogares gastan más de la mitad en procesados (gradient boosting con pesos de clase) obtiene ROC-AUC de 0.699 en prueba.
- El resultado depende de la definición de "fresco": va de 64.6% a 84.9% según la clasificación.

## Datos

Se usan dos tablas de la ENIGH 2024, que deben descargarse del sitio de INEGI:

- `gastoshogar`: gasto de los hogares por producto.
- `concentradohogar`: ingresos y características de los hogares.

Descarga: https://www.inegi.org.mx/programas/enigh/nc/2024/

Las dos tablas se unen con las claves `folioviv` y `foliohog`. Los datos originales no se incluyen aquí por su tamaño. La tabla final de 90,122 hogares está en `hogares_procesados.csv`.

## Cómo reproducir

1. Abrir el notebook en Google Colab.
2. Subir a Colab los dos archivos descargados de INEGI.
3. Ejecutar las celdas de arriba hacia abajo, sin saltarse ninguna (Entorno de ejecución > Ejecutar todo).

Todos los procesos con azar usan la semilla 42. Las versiones de las bibliotecas están en `requirements.txt`.

## Contenido

| Archivo | Descripción |
| --- | --- |
| `Proyecto_ENIGH.ipynb` | Todo el análisis, con sus salidas |
| `hogares_procesados.csv` | Tabla final de hogares (una fila por hogar) |
| `requirements.txt` | Versiones de las bibliotecas |
| Catálogo de gastos de INEGI | Descripción de cada clave de producto |

## Fuentes

- INEGI. (2025). *Encuesta Nacional de Ingresos y Gastos de los Hogares (ENIGH) 2024*.
- INEGI. (2025). *ENIGH 2024. Catálogo para gastos del hogar*. https://www.inegi.org.mx/contenidos/programas/enigh/nc/2024/doc/enigh2024_ns_catalogo_gastos.pdf
- La clasificación de productos está inspirada en NOVA (Monteiro et al., 2019).

## Limitaciones

Los errores estándar no incorporan el diseño muestral de la encuesta, la clasificación de productos es una decisión de la autora, y es una sola encuesta (2024), por lo que los resultados son asociaciones y no tendencias en el tiempo.
