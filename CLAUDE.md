# CLAUDE.md — COIPO_INCENDIO_PRESUPUESTO

Guía para agentes. Calculadora de costo de brigadas de incendios en un único `index.html` (sin build ni dependencias locales). Detalle en [README.md](README.md) e [insumos/](insumos/).

## Estructura

- `index.html`: contiene todo. De arriba abajo: `<style>` (tokens CSS en `:root`), marcado de la tarjeta, y un `<script>` con catálogos (`REGIONES`, `TIPOS`, `CARGOS`, `BBSS_LINES`, `TEMPLATES`), el tarifario (`TARIFARIO`), el motor (`zonaDe`, `tarifaDe`, `calc`), el estado (`b`, `saved`) y el render/wiring.
- `insumos/`: documentos de problema y solución, y `MANIFIESTO.yaml` (generado por un analizador; ver abajo).
- `.github/workflows/readme.yml`: workflow compartido de la flota; no editar.

## Comandos

No hay. Para probar: abrir `index.html` en el navegador (requiere internet por SheetJS y Google Fonts) y mirar el resultado. No hay tests ni linter.

## Convenciones

- Español en toda la interfaz; montos en miles de pesos (M$) con formato `es-CL`.
- Todo cálculo vive en `calc()` y funciones auxiliares: la interfaz solo pinta. Un cambio de regla (zonas, meses, asignación única) se hace ahí.
- El tarifario es un dato de negocio embebido (etiquetado «26-27»). Si cambia el año o los valores, se actualiza `TARIFARIO` completo y se anota el origen; no inventar tarifas.

## Trampas conocidas

- Aysén y Magallanes comparten zona tarifaria con Palena (`zonaDe`); las demás regiones usan la otra. No hay tarifa nocturna de heliataque: `tarifaDe` cae a la clase estándar sin avisar.
- `Secretaria/Adm` busca la clave `Secretaria` como respaldo en el tarifario.
- Los nombres de cargo en `CARGOS[].tarifa` deben coincidir exactamente con las claves de `TARIFARIO`; si no, el cargo sale con advertencia y no suma.
- Los campos de texto (nombre de la brigada) se insertan en el HTML de la lista guardada sin escapar: no hay riesgo de datos remotos (todo es local), pero no agregar entradas que vengan de fuera sin escaparlas.
- Los datos no se persisten; no asumir `localStorage`.
- La página carga SheetJS 0.18.5 desde cdnjs: si se cambia la versión, fijarla explícitamente.

## Qué no tocar

- Los valores del tarifario sin una fuente oficial citada.
- `insumos/MANIFIESTO.yaml`: lo genera el flujo de documentación; sus marcas `[PENDIENTE]` / `[VERIFICAR]` las cierra una persona.
- Nunca agregar datos personales ni credenciales al archivo: el repositorio es público según el propio manifiesto.
