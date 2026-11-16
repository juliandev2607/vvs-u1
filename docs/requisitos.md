# Requisitos: revisión y trazabilidad

## Matriz de revisión

| ID | Problema | Impacto | Propuesta | Artefacto | Estado |
|----|----------|---------|-----------|-----------|--------|
| R-01 | «Rápidamente» no es medible | No se puede verificar ni aceptar | RF-01 | docs/requisitos.md | Propuesto |
| R-02 | «Clientes importantes» y «descuento especial» sin definir (quién, cuánto, unidad) | Cada desarrollador implementa algo distinto | RF-02 | docs/requisitos.md | Pendiente de SP-02 |
| R-03 | «Excepto en promociones» sin definir; el tope no dice qué ocurre al excederlo | Totales negativos o cobros indebidos | RF-03 | docs/requisitos.md | Pendiente de SP-03 |
| R-04 | «Correcto» sin oráculo ni redondeo | Imposible diseñar pruebas | RF-04 | docs/requisitos.md | Propuesto |

## Requisitos funcionales verificables

- **RF-01.** Con entradas válidas, `calcularDescuento` debe responder en 50 ms o menos en el percentil 95 de 1000 invocaciones consecutivas (umbral sujeto a SP-01).
- **RF-02.** Si `esVip` es `true`, se aplica al descuento por porcentaje un descuento adicional de 10 unidades monetarias (valor y unidad sujetos a SP-02).
- **RF-03.** El descuento total no puede superar el precio. Si lo supera y no hay promoción activa, el total es 0. Un porcentaje fuera de 0–100 se rechaza con un error identificable (regla para promociones sujeta a SP-03).
- **RF-04.** El total es `precio - descuento`, redondeado a 2 decimales. Casos de aceptación: (100, 10, false) = 90.00; (100, 10, true) = 80.00. Precio negativo o no numérico se rechaza con error.

## Supuestos de negocio pendientes de confirmación

- **SP-01.** ¿Cuál es el umbral de tiempo aceptable y en qué entorno se mide?
- **SP-02.** ¿Qué es un cliente importante? ¿El adicional son 10 unidades monetarias o 10 puntos porcentuales?
- **SP-03.** ¿Cómo se identifica una promoción y qué tope tiene? ¿Se acota o se rechaza el exceso?
