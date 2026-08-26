# IASI Dev User Guide


`iasi-dev` proporciona una interfaz común para realizar las tareas habituales de desarrollo y operación del ecosistema IASI desde la terminal.

Permite preparar un workspace, actualizar repositorios, construir y publicar documentación, desplegar cambios y gestionar los servicios locales sin tener que recordar el mecanismo particular de cada repositorio o herramienta.

Esta guía está dirigida a las personas que trabajan con los proyectos IASI. Explica el vocabulario utilizado, cómo preparar el entorno, qué comando elegir, qué resultado esperar y qué precauciones tomar.

No describe la implementación interna de `iasi-dev`; describe **cómo utilizarlo**.

El recorrido recomendado es sencillo:

1.  conocer los conceptos y la nomenclatura que utiliza `iasi-dev`;
2.  preparar el entorno de trabajo;
3.  conocer los comandos disponibles;
4.  aplicar los workflows habituales;
5.  acudir a la sección de seguridad y diagnóstico cuando una operación no produzca el resultado esperado.

Si ya conoce `iasi-dev`, puede ir directamente al capítulo que corresponda a la tarea que quiere realizar.

## Cómo se escribe una instrucción

``` bash
iasi-dev <comando> [opciones]
```

Para consultar la ayuda disponible:

``` bash
iasi-dev help
iasi-dev help <comando>
```

En esta guía, llamamos **comando** a la palabra que indica la operación principal, como `build` o `deploy`. Llamamos **opción** a un modificador precedido por `-` o `--`, como `--full`. Los valores entre corchetes son opcionales; los corchetes no se escriben.

Una distinción es especialmente importante desde el principio: construir, publicar, confirmar y desplegar son operaciones diferentes. Ninguna de ellas implica automáticamente las demás salvo cuando el propio comando lo establece de forma explícita.
