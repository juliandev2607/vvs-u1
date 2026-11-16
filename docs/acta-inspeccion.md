# Acta de inspección por pares

Roles: Autor: UPS. Revisor: Julian Benalcazar. Registrador: Julian Benalcazar. Fecha: 15/11/2026.

| ID | Origen | Severidad | Evidencia | Acción | Estado |
|----|--------|-----------|-----------|--------|--------|
| H-01 | Revisión humana | Alta | Líneas 4-6: con porcentaje > 100 solo se escribe un mensaje y el cálculo continúa | Rechazar con error (RF-03) | Pendiente (SP-03) |
| H-02 | Revisión humana | Alta | Línea 3: el adicional VIP no tiene tope; (100, 95, true) da -5 | Acotar total a 0 salvo promoción (RF-03) | Pendiente (SP-03) |
| H-03 | Revisión humana | Media | Línea 3: el valor 10 no declara unidad (moneda o puntos porcentuales) | Constante nombrada tras confirmar SP-02 | Pendiente (SP-02) |
| H-04 | Revisión humana | Media | Sin validación de tipo ni rango (precio negativo, valores no numéricos) | Validar entradas (RF-04) | Pendiente |
| H-05 | Revisión humana | Media | Sin redondeo a 2 decimales en aritmética de punto flotante | Redondear (RF-04) | Pendiente |
| H-06 | Revisión humana | Baja | Sin contrato documentado de la función | Añadir JSDoc | Diferido |
| H-07 | ESLint (no-var) | Media | Líneas 2 y 5 | const/let | Corregido |
| H-08 | ESLint (eqeqeq) | Media | Línea 3: `== true` | `=== true` | Corregido (cambio de contrato anotado) |
| H-09 | ESLint (curly) | Baja | Líneas 3 y 4: `if` sin llaves | Añadir llaves | Corregido |
| H-10 | ESLint (no-console) | Baja | Línea 4: `console.log` | Reemplazar al decidir SP-03 | Pendiente |

## Comentarios técnicos del pull request

1. `src/descuentos.js`, línea 3: `=== true` cambia el comportamiento si el llamador envía `"true"` o `1`. Documentar el tipo esperado en RF-02 o convertir el valor en el punto de entrada.
2. `src/descuentos.js`, línea 7: `console.log` no detiene la ejecución y el cálculo sigue con un total negativo. Se mantiene hasta resolver SP-03 (lanzar error o acotar).
