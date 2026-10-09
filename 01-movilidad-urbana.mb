# Movilidad urbana y productividad económica

**Herramientas:** Python (pandas, numpy, seaborn, matplotlib), Jupyter Notebook

## Contexto

Como analista de datos, se me asignó un caso simulado para un banco de desarrollo: identificar en qué ciudades del mundo conviene invertir en infraestructura de transporte para impulsar la productividad económica. Combiné dos fuentes de datos reales — **TomTom Traffic Index** (tráfico en tiempo real) y **OECD Cities** (PIB per cápita, desempleo, contaminación y población) — para 16 ciudades de América Latina en 2024.

## Proceso

- Limpieza y estandarización de nombres de ciudades/países y tipos de datos entre ambas fuentes.
- Filtrado al año 2024 y agregación de los datos de tráfico por ciudad.
- Unión de ambos datasets en una tabla única lista para análisis.
- Cálculo de correlaciones y visualización de relaciones entre variables de movilidad y económicas.

## Hallazgos clave

- La correlación entre retraso por congestión y PIB per cápita fue **débil y positiva** (r ≈ 0.28) — contrario a la hipótesis de que más tráfico implica menor productividad. Las megaciudades con economías más grandes (CDMX, São Paulo) también concentran más autos y actividad.
- La relación más fuerte del dataset fue **desempleo vs. PIB per cápita** (r ≈ -0.51): el desempleo explica mejor las diferencias de productividad que la congestión vial.
- **Ciudad de México** es un outlier claro en congestión: su retraso por tráfico (~2,833) más que duplica al de São Paulo (~1,729), la siguiente ciudad más congestionada.
- **Montevideo** rompe el patrón esperado: el PIB per cápita más alto del dataset (~26.2M) pese a tener una de las congestiones más bajas.

## Implicaciones

La congestión vial por sí sola no es un buen predictor de productividad económica en este dataset; el desempleo es una variable mucho más explicativa. Se recomienda profundizar en outliers como Ciudad de México y Montevideo antes de tomar decisiones de inversión basadas únicamente en índices de tráfico.
