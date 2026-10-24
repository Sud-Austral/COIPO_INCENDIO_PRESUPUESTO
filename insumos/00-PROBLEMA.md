# Problema: costear brigadas de incendios

Actualizado el 2026-10-24 tras abrir y leer `index.html` (la versión anterior de este documento, generada por un analizador, decía que el contenido de la página era desconocido). Marcas: VERIFICADO (visto en el archivo), INFERIDO, `[PENDIENTE]` (lo confirma una persona del área). No ejecuté la página en un navegador.

## Contexto

INFERIDO del título y la marca de `index.html` («Costear una brigada», «SIFOP-IF · CONAF · GEPRIF») y del nombre del repositorio: CONAF debe presupuestar la temporada de incendios, y una pieza de ese presupuesto es el costo de cada brigada (personal y bienes y servicios). Qué significan SIFOP-IF y GEPRIF y quién pidió la herramienta: `[PENDIENTE]`.

## Qué dolor resuelve (INFERIDO)

Armar el costo de una brigada exige combinar un tarifario de remuneraciones mensuales por cargo (según zona, jornada y tipo de brigada), una dotación típica, bienes y servicios mensuales repartidos en líneas del subtítulo 22, y los meses operativos del segundo semestre de 2026 y primero de 2027. La página trae todo precargado para que el usuario solo elija tipo y meses. Cómo se hacía antes (planilla, otra herramienta): `[PENDIENTE]`.

## Usuarios

`[PENDIENTE]` quiénes y cuántos. El texto de la página («Todo lo demás viene precargado — tócalo solo si cambia») sugiere personas que no son especialistas en el tarifario.

## Alcance (VERIFICADO)

- Costear una brigada por región (16), tipo (línea, mixta, helitransportada, recurso cisterna), plan (base o fortalecimiento), jornada (diurna o nocturna) y heliataque sí o no.
- Editar dotación por 13 cargos y bienes y servicios (monto único o 14 líneas).
- Guardar varias brigadas, ver el total de temporada y exportar a Excel.

## Fuera de alcance (VERIFICADO por ausencia en el código)

Persistencia, usuarios o roles, conexión con sistemas institucionales, validación contra el presupuesto oficial.

## Criterios de éxito

No constan en el repositorio. Que las cifras coincidan con el presupuesto oficial o con la planilla de origen: `[PENDIENTE]`, no lo comprobé. Origen y vigencia del tarifario «26-27» embebido: `[PENDIENTE]`.
