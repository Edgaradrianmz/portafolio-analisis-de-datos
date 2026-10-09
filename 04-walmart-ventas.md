# Resumen ejecutivo de ventas Walmart

**Herramientas:** Google Sheets/Excel (tablas dinámicas, BUSCARV, formato condicional, dashboards), informe ejecutivo C→F→I

## Contexto

Caso simulado como analista en Walmart: la Dirección Comercial necesitaba un resumen ejecutivo para decidir ajustes de presupuesto e inventario a partir de los datos de ventas semanales de 2012 (más de 95,000 registros transaccionales).

## Proceso

- **Limpieza y enriquecimiento**: normalicé formatos de fecha y montos, y uní la tabla transaccional con los catálogos de tiendas y departamentos usando BUSCARV/VLOOKUP.
- **KPIs**: diseñé dos métricas de negocio mediante tablas dinámicas — *ventas por metro cuadrado* (eficiencia) y *participación por departamento* (% del total de ventas).
- **Dashboard interactivo**: filtro desplegable por departamento, formato condicional y gráficos que se actualizan en tiempo real según la selección del usuario.
- **QA**: validé que no hubiera tiendas sin departamento asignado, ventas negativas o nulas, ni tamaños en m² en cero.

## Hallazgos clave

- Los departamentos de **Ropa, Salud y Bienestar y Snacks y Bebidas** mostraron la mayor eficiencia en ventas por metro cuadrado.
- **Automotriz** tuvo el desempeño más bajo en eficiencia.
- En participación sobre el total de ventas, **Despensa y Básicos** (15.8%) y **Comida Fresca** (11.2%) concentraron la mayor proporción, mientras que **Jardín y Vida al Aire Libre** (1.0%) y **Oficina, Escuela y Manualidades** (1.4%) aportaron muy poco.

## Implicaciones

- Priorizar inventario y presupuesto en los departamentos de mayor eficiencia (como Snacks y Bebidas).
- Desarrollar una estrategia de venta específica para reactivar departamentos rezagados como Automotriz.
