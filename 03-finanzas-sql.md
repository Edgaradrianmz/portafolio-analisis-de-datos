# Análisis del desempeño financiero con SQL

**Herramientas:** SQL, análisis financiero (margen, ROI), informe ejecutivo C→F→I

## Contexto

Informe ejecutivo dirigido al director de finanzas de una empresa con operación en 6 países (Estados Unidos, Australia, Reino Unido, Alemania, Francia y Canadá). Usando SQL, construí una tabla con ingresos, costos, costo de campañas, beneficio bruto, margen y ROI por país, para responder cuánto gana la empresa por país y qué tan rentable es cada mercado considerando el gasto en marketing.

## Hallazgos clave

- **Estados Unidos** es el mercado más rentable en ambas dimensiones: mayor ingreso (~$3.35M) y el ROI más alto (75.75%).
- El **margen bruto es muy similar entre países** (42%–45%), lo que indica que la estructura de costos operativos es consistente a nivel global; la verdadera diferencia entre mercados está en la eficiencia del gasto en marketing (ROI).
- **Canadá** tiene la situación más ineficiente: pese a tener el margen más alto (44.76%), registra el ROI más bajo (17.43%), porque su gasto en campañas (~$1.82M) es alto en relación con sus ingresos (~$710K).
- El gasto en campañas es similar en dólares absolutos entre países (~$1.8M–$2.3M), pero el ROI varía de 17% a 76% según cuánto ingreso genera cada mercado con ese mismo presupuesto.

## Ideas accionables

1. Aumentar la inversión en marketing en Estados Unidos, el mercado con mayor retorno comprobado por cada dólar invertido.
2. Revisar y reestructurar el gasto de campañas en Canadá (y en menor medida Francia y Alemania), que invierten montos similares a Estados Unidos sin ingresos proporcionales.

## Reflexión personal

- **Margen vs. ROI**: el margen mide qué porcentaje de los ingresos se convierte en utilidad bruta; el ROI mide el retorno específicamente sobre lo invertido en marketing. Un país puede tener buen margen y mal ROI si su marketing es ineficiente (como Canadá).
- **Por qué el ROI de EE. UU. es tan alto**: genera muchos más ingresos con un gasto en campañas similar al de otros países — la eficiencia está en la generación de ingresos, no en gastar menos.
- **Si el gasto en campañas subiera 50%**: el ROI bajaría en la mayoría de los países, a menos que ese mayor gasto se traduzca en un aumento proporcional o mayor en ingresos.
