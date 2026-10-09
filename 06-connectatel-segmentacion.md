# Análisis ConnectaTel — Segmentación de Clientes de Telecomunicaciones

## 🎯 Objetivo

Como analista de datos, el objetivo de este proyecto es evaluar el comportamiento de los clientes de ConnectaTel, una empresa de telecomunicaciones en Latinoamérica, con datos registrados hasta 2024. A partir de la limpieza, exploración y segmentación de los datos, se busca construir un perfil estadístico de los clientes, detectar comportamientos atípicos y crear segmentos de clientes útiles para la toma de decisiones comerciales.

## 📊 Datasets utilizados

| Archivo | Descripción |
|---|---|
| `plans.csv` | Información de los planes actuales (precio, minutos incluidos, GB incluidos, costo por excedente) |
| `users_latam.csv` | Información de los clientes (edad, ciudad, fecha de registro, plan, fecha de baja) |
| `usage.csv` | Detalle del uso real de los servicios (llamadas y mensajes) |

## 🔄 Etapas del análisis

1. **Carga y exploración inicial**: revisión de forma (`.shape`), tipos de datos e info general (`.info()`) de los 3 datasets.
2. **Diagnóstico de calidad de datos**: conteo y proporción de nulos por columna, identificación de valores centinela (`-999` en `age`) e inconsistencias (`"?"` en `city`).
3. **Limpieza de datos**:
   - Conversión de columnas de fecha a `datetime` (a prueba de errores, con `errors='coerce'`).
   - Reemplazo del centinela `-999` en `age` por la mediana.
   - Conversión de `"?"` en `city` a nulos reales (`pd.NA`).
   - Corrección de 40 fechas futuras imposibles (`reg_date` en 2026) marcadas como `NaT`.
   - Verificación de que los nulos en `duration`/`length` son MAR (dependientes de `type`), por lo que se conservan sin imputar.
4. **Construcción de perfil de cliente**: agregación de `usage` por `user_id` (mensajes, llamadas, minutos totales) y unión con `users` mediante `merge`.
5. **Análisis exploratorio**: resumen estadístico de variables numéricas, distribución del tipo de plan, histogramas por variable (`age`, `cant_mensajes`, `cant_llamadas`, `cant_minutos_llamada`) segmentados por plan.
6. **Detección de outliers**: boxplots y cálculo de límites con el método IQR para las variables de uso.
7. **Segmentación de clientes**: creación de las columnas `grupo_uso` (Bajo/Medio/Alto) y `grupo_edad` (Joven/Adulto/Adulto Mayor) mediante comparaciones lógicas.
8. **Informe ejecutivo**: análisis de hallazgos y recomendaciones de negocio para stakeholders.

## ▶️ Cómo ejecutar el notebook

1. Descarga el notebook (`.ipynb`) y los 3 archivos CSV de este repositorio.
2. Abre [Google Colab](https://colab.research.google.com/) y selecciona **Archivo → Subir notebook**, o arrastra el archivo `.ipynb` directamente.
3. Sube los 3 CSV a la sesión de Colab (ícono de carpeta 📁 en el panel izquierdo → **Subir**), o móntalos desde Google Drive si prefieres persistencia entre sesiones.
4. Ejecuta las celdas en orden desde el inicio: **Entorno de ejecución → Ejecutar todas** (o `Ctrl+F9`).

Alternativamente, puedes ejecutarlo en **Jupyter Notebook/JupyterLab local**:
```bash
pip install pandas numpy seaborn matplotlib
jupyter notebook
```

## 🔁 Guía de reproducción

1. Clona o descarga este repositorio.
2. Verifica que los 3 archivos CSV (`plans.csv`, `users_latam.csv`, `usage.csv`) estén en la misma carpeta que el notebook, o ajusta las rutas en la primera celda (`pd.read_csv(...)`) según dónde los hayas guardado.
3. Ejecuta el notebook de principio a fin, en orden — varias celdas dependen de variables creadas en pasos anteriores (por ejemplo, `user_profile` se construye a partir de `users` y `usage_agg`).
4. Los resultados (tablas, gráficos e insights) se generan automáticamente al correr cada celda; no se requieren archivos de salida adicionales para reproducir el análisis completo.

**Librerías requeridas:** `pandas`, `numpy`, `seaborn`, `matplotlib`
