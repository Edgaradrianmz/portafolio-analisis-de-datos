# Validando hipótesis de negocio con pruebas estadísticas

Análisis de un experimento A/B sobre una landing page para decidir, con evidencia estadística, qué versión implementar y si la fuente de tráfico o el tipo de usuario influyen en la conversión.

## Contexto

Una empresa expuso a sus usuarios a dos versiones de su página de inicio (A y B) y necesita saber:

- ¿Qué página genera mayor conversión y mayor gasto promedio?
- ¿Qué canales de tráfico son más efectivos para generar conversiones?
- ¿Existen diferencias según el tipo de usuario?
- ¿Qué recomendaciones se pueden tomar para optimizar la estrategia de marketing?

## Datos

- **Archivo:** `landing_experiment.csv` (dataset de práctica proporcionado por el bootcamp de TripleTen).
- **Tamaño:** 40,000 usuarios únicos, sin valores nulos ni duplicados en `user_id`.
- **Periodo:** 28 días (del 1 al 28 de enero de 2026).
- **Grupos:** casi perfectamente balanceados, 19,982 usuarios en A y 20,018 en B.

| Columna | Descripción |
|---|---|
| `user_id` | Identificador único del usuario |
| `date` | Fecha de la visita |
| `landing` | Versión de la página (A o B) |
| `region` | Región del usuario (5 categorías) |
| `dispositivo` | Mobile o Desktop |
| `traffic_source` | Fuente de tráfico: Organic, Ads, Email o Referral |
| `user_type` | Nuevo o Recurrente |
| `converted` | 1 si se convirtió en cliente, 0 si no |
| `gasto` | Gasto del usuario (0 si no convirtió) |

## Metodología

El nivel de significancia fue de 0.05 en todas las pruebas. La prueba se eligió según el tipo de variable:

| Pregunta | Prueba | Por qué |
|---|---|---|
| ¿Cambia el gasto promedio de los clientes entre A y B? | Prueba t de Welch (`ttest_ind`, `equal_var=False`) | Compara medias de dos grupos independientes con tamaños distintos |
| ¿Cambia la tasa de conversión entre A y B? | Prueba z de proporciones (`proportions_ztest`) | `converted` es una variable binaria (0/1) |
| ¿La fuente de tráfico se asocia con la conversión? | Chi-cuadrada de independencia (`chi2_contingency`) | Dos variables categóricas |
| ¿El tipo de usuario se asocia con la conversión? | Chi-cuadrada de independencia | Dos variables categóricas |

**Decisión de diseño:** el análisis de gasto se hizo solo entre los usuarios que se convirtieron en clientes (2,512 en A y 3,194 en B). Los no convertidos tienen gasto 0, y mezclarlos habría combinado dos efectos distintos: cuántos usuarios convierten y cuánto gasta cada cliente.

**Validación previa:** se verificaron nulos, tipos de dato, unicidad de `user_id`, rango de fechas, valores esperados de las variables categóricas y el balance entre los grupos A y B.

## Resultados

### Gasto promedio por cliente (A vs B)

| | Página A | Página B |
|---|---|---|
| Clientes | 2,512 | 3,194 |
| Gasto promedio | 61.09 | 68.75 |

Diferencia de 7.66 por cliente (≈ 12.5% más en B). Estadístico t = -9.48, p = 3.63 × 10⁻²¹. **La diferencia es significativa.**

### Tasa de conversión (A vs B)

| | Página A | Página B |
|---|---|---|
| Convertidos | 2,512 de 19,982 | 3,194 de 20,018 |
| Tasa de conversión | 12.57% | 15.96% |

Diferencia de 3.4 puntos porcentuales (≈ 27% más conversiones en términos relativos). Estadístico z = -9.68, p = 3.76 × 10⁻²². **La diferencia es significativa.** El signo negativo solo indica que A convierte menos que B.

### Fuente de tráfico vs conversión

| Canal | Clientes | Tasa de conversión |
|---|---|---|
| Email | 918 | 14.99% |
| Ads | 1,759 | 14.74% |
| Referral | 549 | 13.88% |
| Organic | 2,480 | 13.79% |

Chi-cuadrado = 8.66, 3 grados de libertad, p = 0.034. Hay asociación estadísticamente significativa, pero **débil**: entre el mejor y el peor canal hay solo 1.2 puntos porcentuales. Organic aporta más clientes en volumen porque es el canal más grande, pero tiene la tasa más baja.

### Tipo de usuario vs conversión

| Tipo | Clientes | Tasa de conversión |
|---|---|---|
| Nuevo | 3,738 | 14.36% |
| Recurrente | 1,968 | 14.09% |

Chi-cuadrado = 0.51, 1 grado de libertad, p = 0.474. **No hay evidencia de asociación.** Ambos perfiles responden de forma casi idéntica.

### Visualizaciones

Se incluyen gráficos de barras de cantidades absolutas y de proporciones para `traffic_source` y `user_type`, que respaldan los resultados de las pruebas.

<!-- Agrega aquí capturas de tus gráficos, por ejemplo:
![Conversión por fuente de tráfico](images/conversion_fuente_trafico.png)
![Conversión por tipo de usuario](images/conversion_tipo_usuario.png)
-->

## Conclusiones y recomendaciones

1. **Implementar la página B.** Supera a la A en tasa de conversión y en gasto por cliente. Combinando ambos efectos, B genera aproximadamente 10.97 por usuario expuesto frente a 7.68 de A (≈ 43% más). Esta cifra es una estimación descriptiva, no una prueba estadística propia.
2. **Mantener y reforzar Email y Ads**, que muestran las mejores tasas. Como la diferencia entre canales es pequeña, conviene validarlo con un experimento antes de mover presupuesto.
3. **Mejorar la conversión de Organic**, el canal con más volumen y la tasa más baja, porque cualquier mejora ahí tendría el mayor impacto en número de clientes.
4. **No diseñar estrategias distintas por tipo de usuario**, ya que nuevos y recurrentes se comportan igual.

## Limitaciones

- El experimento duró 4 semanas. Convendría confirmar que el efecto de la página B se mantiene en el tiempo y descartar un efecto de novedad.
- El análisis de gasto se limita a usuarios que convirtieron. La distribución del gasto tiene sesgo a la derecha, aunque con miles de clientes por grupo la prueba t sigue siendo confiable.
- Con 40,000 usuarios, las pruebas detectan diferencias pequeñas. Por eso se interpretó el tamaño del efecto además del valor p, sobre todo en la fuente de tráfico.
- No se analizó si el efecto de la página B cambia por dispositivo o región. Sería un siguiente paso natural.

## Herramientas

Python, pandas, SciPy, statsmodels, seaborn, matplotlib y Jupyter Notebook.

## Estructura del repositorio

```
├── notebook.ipynb   # análisis completo
├── README.md        # este documento
└── images/          # gráficos usados en el README
```
