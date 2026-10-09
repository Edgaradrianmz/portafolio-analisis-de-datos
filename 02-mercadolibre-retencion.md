# Análisis de embudo y retención para MercadoLibre

**Herramientas:** análisis de embudo y cohortes, Excel, informe ejecutivo C→F→I

## Contexto

Caso simulado como analista de MercadoLibre. El objetivo: analizar el embudo de conversión (select_item → add_to_cart → begin_checkout → add_shipping_info → add_payment_info → purchase) y la retención de usuarios entre el 01/01/2025 y el 31/08/2025, entregando un informe ejecutivo bajo el formato Contexto–Hallazgos–Implicaciones (C→F→I).

## Hallazgos — Embudo de conversión

- La mayor caída del embudo ocurre entre **select_item y add_to_cart** (de 76.9% a 11.0%), una pérdida de ~66 puntos porcentuales — muy por encima de cualquier otra transición.
- Por país: **Uruguay** tuvo la mejor tasa de compra (4.55%). **Ecuador** y **Colombia** llegaron hasta el pago sin que ningún usuario completara la compra. **Paraguay** colapsó antes, desde el checkout.

## Hallazgos — Retención de cohortes

- La retención se mantuvo estable (85.9%–87.7%) de enero a julio, con la cohorte de marzo como la mejor.
- La cohorte de **agosto** tuvo una caída marcada (70.8% en D7), ~15 puntos por debajo del promedio.
- Por país, **Perú** y **México** lideraron la retención en D28 (3.2% y 3.1%); **Colombia** tuvo la más baja (1.6%). **Bolivia** y **Ecuador** mostraron mayor fricción en etapas tempranas.

## Implicaciones

- Priorizar la página de producto (imágenes, precio, reseñas) y pruebas A/B para reducir el abandono antes de "agregar al carrito" — el cuello de botella principal del embudo.
- Implementar campañas de reactivación entre D14 y D28, e investigar la caída de la cohorte de agosto.
- Priorizar activación temprana en Bolivia y Ecuador; mejorar la permanencia a largo plazo en Colombia usando a México y Perú como referencia.

## Reflexión personal

El abandono principal no ocurre en el checkout sino mucho antes, en la decisión de agregar el producto al carrito — un hallazgo que reorienta la prioridad de optimización hacia la presentación del producto en vez del proceso de pago.
