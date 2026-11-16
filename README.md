# VVS · Unidad 1: Auditoría estática del módulo de descuentos

Repositorio de la actividad de evaluación estática: requisitos, inspección por pares y detección temprana de defectos con ESLint.

## Estructura

- `src/descuentos.js`: módulo auditado (versión con correcciones confirmadas).
- `docs/requisitos.md`: matriz de revisión, RF-01 a RF-04 y supuestos pendientes.
- `docs/checklist.md`: lista de verificación (11 preguntas).
- `docs/acta-inspeccion.md`: hallazgos de la inspección por pares y comentarios del pull request.
- `evidencias/lint-inicial.txt` y `evidencias/lint-final.txt`: salida de ESLint antes y después.
- `eslint.config.js`: reglas `no-var`, `eqeqeq`, `no-unused-vars`, `curly` y `no-console`.

## Reproducir

```bash
npm install
npm run lint
```

Node.js 22 y ESLint 9. El código original antes de las correcciones está en `evidencias/descuentos-original.js` y en el primer commit del historial.
