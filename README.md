# COIPO_INCENDIO_PRESUPUESTO — Costeo de brigadas de incendios (SIFOP-IF)

Página web de un solo archivo (`index.html`) para estimar el costo de una brigada de incendios forestales durante la temporada: eliges región, tipo de brigada, plan, jornada y meses operativos, ajustas dotación y bienes y servicios, y la página calcula jornales y bienes y servicios en miles de pesos (M$). La marca de la página dice «SIFOP-IF · CONAF · GEPRIF».

Para quién: personal de CONAF que arma presupuestos de brigadas (INFERIDO de la marca y del contenido; usuarios concretos y dueño del tarifario: pendiente de confirmar por el equipo).

## Stack (VERIFICADO en `index.html`)

HTML + CSS + JavaScript sin framework, sin build y sin `package.json`. Dos recursos externos cargados desde internet: la librería SheetJS `xlsx` 0.18.5 (cdnjs) para exportar a Excel y las fuentes Fraunces e Inter (Google Fonts). No hay backend, base de datos, API ni variables de entorno.

## Estructura

```
index.html                    toda la aplicación (estilos, catálogos, tarifario y motor de cálculo)
insumos/                      problema, solución y manifiesto de datos
.github/workflows/readme.yml  workflow compartido de la flota que regenera documentación
```

## Cómo usarlo

Abrir `index.html` en un navegador (necesita internet para SheetJS y las fuentes). No hay comandos de instalación, build ni pruebas.

Flujo en pantalla: el costo se recalcula al cambiar cualquier campo; «Guardar y empezar otra» agrega la brigada a la lista; la lista permite editar, eliminar y «Exportar la lista a Excel» (`Brigadas_costeo.xlsx`).

## Cómo calcula (VERIFICADO leyendo `calc()` en `index.html`; no lo ejecuté)

- Zona tarifaria: Aysén y Magallanes usan «PALENA, XI y XII»; el resto, «XV a X, RM y OC».
- Jornal mensual = suma de dotación por cargo x tarifa mensual (tarifario «26-27» embebido en el archivo, por zona, jornada diurna/nocturna y clase estándar/heliataque), en miles de pesos.
- Total = (jornal mensual + bienes y servicios mensuales) x (meses 2.° semestre + meses 1.er semestre) + asignación única del primer mes. Bienes y servicios puede ser un monto único o la suma de 14 líneas del subtítulo 22.
- Si un cargo no tiene tarifa para la zona y jornada, muestra una advertencia en vez de sumarlo.
- Los datos no se guardan: la lista vive solo en memoria y se pierde al recargar la página.

## Configuración y despliegue

Sin variables de entorno. No consta en el repositorio dónde está publicada la página: pendiente de confirmar por el equipo.

## Más documentación

[CLAUDE.md](CLAUDE.md) (guía para agentes), [insumos/00-PROBLEMA.md](insumos/00-PROBLEMA.md), [insumos/01-SOLUCION.md](insumos/01-SOLUCION.md).
