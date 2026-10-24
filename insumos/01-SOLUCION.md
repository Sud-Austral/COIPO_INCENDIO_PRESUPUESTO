# Solución: calculadora de una sola página

Actualizado el 2026-10-24 tras leer `index.html` completo. No lo ejecuté en un navegador ni verifiqué los cálculos con casos. Marcas: VERIFICADO (visto en el código), INFERIDO, `[PENDIENTE]`.

## Arquitectura (VERIFICADO)

Un único archivo `index.html` con estilos, marcado y JavaScript. Sin servidor, sin base de datos, sin build, sin variables de entorno. Recursos externos: SheetJS `xlsx` 0.18.5 desde cdnjs y fuentes de Google Fonts. El estado vive en memoria (`b` para la brigada en edición, `saved` para las guardadas) y se pierde al recargar.

## Componentes

| Pieza | Qué hace |
|---|---|
| Catálogos | `REGIONES` (16), `TIPOS` (4), `CARGOS` (13), `BBSS_LINES` (14 líneas del subtítulo 22), `TEMPLATES` (dotación y bienes y servicios de referencia por tipo) |
| `TARIFARIO` | Tarifas mensuales ($) por zona, jornada y clase (estándar o heliataque) para cada cargo; etiquetado «tarifario real 26-27» en el código |
| `zonaDe`, `tarifaDe` | Elige la zona (Aysén y Magallanes: «PALENA, XI y XII»; resto: «XV a X, RM y OC») y busca la tarifa de un cargo; sin tarifa nocturna de heliataque cae a estándar |
| `calc(b)` | Jornal mensual, bienes y servicios, totales por semestre y de temporada, advertencias de cargos sin tarifa |
| Render y eventos | Tarjeta de costo, formulario, dotación con botones +/−, desglose de bienes y servicios, lista de brigadas guardadas |
| Exportación | Hoja «Brigadas» a `Brigadas_costeo.xlsx` con SheetJS |

## Flujo de datos

Selecciones del usuario → objeto `b` → `calc(b)` → tarjeta de costo (se repinta en cada cambio). «Guardar» copia `b` a `saved`; «Exportar» calcula cada brigada guardada y genera el Excel.

## Fórmula (VERIFICADO)

Total = (jornal mensual + bienes y servicios mensuales) x (meses 2.° semestre + meses 1.er semestre) + asignación única. Los valores están en M$ (miles de pesos); el jornal divide por 1.000 las tarifas en pesos.

## Decisiones visibles

- Todo en un archivo para que se abra sin infraestructura.
- Plantillas por tipo de brigada «editables» para reducir el ingreso de datos.
- Los datos no se envían a ningún servidor (no hay llamadas de red propias).

## Estado actual y pendientes

- Funcional según lectura del código; sin pruebas automáticas.
- `[PENDIENTE]` origen y vigencia del tarifario y de las plantillas de dotación; dónde está publicada; quién la mantiene; si el campo «Plan» (Base o Fortalecimiento) debe cambiar el cálculo (hoy solo se guarda y se exporta, no entra a `calc`; VERIFICADO).
- `insumos/MANIFIESTO.yaml` sigue con las marcas del analizador anterior (por ejemplo, dice que el contenido de `index.html` es desconocido); conviene regenerarlo.
