# Que se construyo

## Lo primero: aca el analizador no ve casi nada

Este repositorio tiene tres archivos: una pagina web [index.html], la
normalizacion del tratamiento de archivos [.gitattributes] y el flujo de
documentacion automatica [.github/workflows/readme.yml].

En un repositorio con servidor, este documento seria el mas largo de los
tres y llevaria citas densas, porque el codigo es la solucion. Aca no. El
analizador no detecto ninguna tecnologia, ninguna dependencia, ninguna
variable de entorno, ninguna ruta expuesta, ninguna tabla y ningun comando.
No es que el sistema no tenga esas cosas: es que la evidencia no llega.

Decirlo es el resultado util de esta corrida. Todo lo que sigue esta
[PENDIENTE] y solo lo puede cerrar una persona que abra la pagina o que
sepa para que se hizo.

## Que hace

[INFERIDO] Muestra algo en un navegador, sin servidor y sin base de datos
[index.html]. Es la unica capacidad afirmable.

Que muestra, con que datos y con que interaccion: [PENDIENTE].
Si calcula algo o solo presenta: [PENDIENTE].
Si los datos estan dentro del archivo o se cargan de otro lado: [PENDIENTE].

## Roles: quien ve que

No hay roles. No hay guardas, decoradores de autorizacion ni tabla de
permisos, y no hay codigo de servidor donde pudieran vivir. Quien abre el
archivo lo ve entero.

Quien puede abrirlo: [PENDIENTE]. Depende de donde este publicado, y eso no
esta en el repositorio.

## De donde salen los datos

[PENDIENTE]. No hay conexion externa detectada, no hay API consumida, no hay
migraciones y no hay archivo semilla. Si la pagina lleva datos, salieron de
alguna parte y esa parte no esta versionada aca.

QUIEN ES DUENO de esos datos: [PENDIENTE].

## Que NO hace

Las ausencias siguientes se afirman porque el analizador enumero esas
categorias completas sobre los tres archivos. Siguen marcadas.

[INFERIDO] No expone ninguna ruta: la enumeracion de endpoints esta vacia.

[INFERIDO] No tiene base de datos: la enumeracion de tablas esta vacia.

[INFERIDO] No declara ninguna dependencia: no hay manifiesto de paquetes de
ningun tipo en los tres archivos del repositorio.

[INFERIDO] No lee ninguna variable de entorno: la enumeracion esta vacia.

[INFERIDO] No tiene pruebas: no hay archivo de prueba entre los tres.

## Iteraciones

[INFERIDO] La unica huella de proceso es el flujo de documentacion
automatica [.github/workflows/readme.yml], que es comun a la flota y no dice
nada de este proyecto en particular. No hay etiquetas, ni CHANGELOG, ni
migraciones numeradas.

## Lo que hay que hacer con este documento

Abrir [index.html] y leerlo. Con eso, los tres documentos se pueden
reescribir enteros y con contenido real. Sin eso, este es todo el
conocimiento que el analizador puede producir, y es honesto decir que es
poco.
