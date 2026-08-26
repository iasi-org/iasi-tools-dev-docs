

## Propósito del documento

Las herramientas utilizadas por IASI comparten palabras como *publicar* o *desplegar*, pero no siempre les atribuyen el mismo significado.

En este documento, cada término tiene una definición concreta. Cuando decimos **construir**, **publicar**, **confirmar** o **desplegar**, nos referimos exclusivamente a las operaciones descritas aquí.

## Workspace

En este documento, cuando decimos **workspace**, nos referimos al directorio que contiene los repositorios IASI como carpetas hermanas.

``` text
iasi-org/
├── iasi-common/
├── iasi-quarto/
├── iasi-quarto-docs/
└── iasi-tools-dev/
```

El workspace permite ejecutar una misma operación sobre varios repositorios. No es en sí mismo un repositorio Git.

## Git y GitHub

En este documento, cuando decimos **Git**, nos referimos al sistema que registra la historia y los cambios de los archivos de un proyecto.

En este documento, cuando decimos **GitHub**, nos referimos al servicio donde se alojan y comparten los repositorios remotos de IASI.

## Repositorio

En este documento, cuando decimos **repositorio**, nos referimos a un directorio gestionado por Git y conectado normalmente con un repositorio remoto en GitHub.

Un workspace contiene varios repositorios. Una operación puede dirigirse a todo el workspace, a un repositorio o a un directorio más concreto.

## Destino

En este documento, cuando decimos **destino**, nos referimos a la ruta indicada al final de un comando para limitar su alcance.

``` bash
iasi-dev build iasi-quarto-docs/01-user-guide
```

En este ejemplo, `iasi-quarto-docs/01-user-guide` es el destino. Cuando se omite, muchos comandos utilizan el directorio actual.

Los comandos que seleccionan publicaciones o repositorios siguen una misma regla: sin destinos procesan todos los aplicables; con uno procesan solo ese destino; con varios procesan exactamente la selección indicada.

## Publicación

En este documento, cuando decimos **publicación**, nos referimos a un proyecto documental reconocido por `iasi.quarto` que puede generar uno o varios formatos de salida.

Una publicación puede ser, por ejemplo, una guía de usuario. Un repositorio puede contener una sola publicación o varias.

## Fuentes

En este documento, cuando decimos **fuentes**, nos referimos a los archivos editables a partir de los que se genera una publicación: documentos QMD, configuración, imágenes y otros recursos.

Las fuentes no son todavía el sitio HTML ni el PDF final.

## Formato de salida

En este documento, cuando decimos **formato de salida**, nos referimos a una de las formas finales que puede generar una publicación, como HTML o PDF.

## Construir y `build`

En este documento, cuando decimos **construir**, nos referimos a transformar las fuentes en uno o varios formatos de salida que puedan revisarse.

El comando correspondiente es:

``` bash
iasi-dev build [destino]
```

Construir no crea commits, no realiza `push` y no despliega cambios. Tampoco significa necesariamente que el contenido de `publish/` haya sido actualizado.

## Resultado de construcción

En este documento, cuando decimos **resultado de construcción**, nos referimos al HTML, PDF u otro formato generado por `build`.

Estos resultados sirven para comprobar la publicación antes de prepararla para el despliegue.

## Artefacto publicable

En este documento, cuando decimos **artefacto publicable**, nos referimos a un archivo o directorio preparado para ser distribuido, como un sitio HTML o un PDF.

## Publicar, `publish` y `publish/`

En este documento, cuando decimos **publicar** como operación, nos referimos a reunir resultados ya construidos dentro del directorio `publish/`.

El comando correspondiente es:

``` bash
iasi-dev publish [destino]
```

En este documento, cuando escribimos **`publish/`**, nos referimos al directorio que contiene los artefactos publicables preparados para su despliegue.

`publish` no sustituye a `build`: prepara resultados existentes. Tampoco crea commits ni realiza `push`.

## Cambio Git

En este documento, cuando decimos **cambio Git**, nos referimos a una diferencia local que Git puede registrar: un archivo añadido, modificado o eliminado.

Un resultado construido puede producir cambios Git si sus archivos se guardan dentro del repositorio.

## Remoto y `push`

En este documento, cuando decimos **remoto**, nos referimos al repositorio Git compartido, normalmente alojado en GitHub.

En este documento, cuando decimos **realizar `push`**, nos referimos a enviar al remoto los commits locales.

## Confirmar, commit y `commit`

En este documento, cuando decimos **confirmar cambios**, nos referimos a crear un commit de Git que registra un conjunto de cambios con un mensaje.

El comando `iasi-dev commit` añade todos los cambios del repositorio seleccionado, crea el commit y lo envía al remoto:

``` bash
iasi-dev commit -m "mensaje" [repositorio]
```

Por tanto, en esta guía `commit` no significa únicamente crear el commit local: el comando también realiza `push`.

## Desplegar y `deploy`

En este documento, cuando decimos **desplegar**, nos referimos a confirmar los cambios de uno o varios repositorios y enviarlos al remoto.

El comando correspondiente es:

``` bash
iasi-dev deploy [destino]
```

`deploy` crea un único commit por repositorio con el estado local completo, incluido `publish/` cuando existe, y después realiza `push`.

`deploy` sin opciones no construye ni publica. Utiliza el estado que ya existe.

## Despliegue completo y `deploy --full`

En este documento, cuando decimos **despliegue completo**, nos referimos a ejecutar consecutivamente:

1.  `build`;
2.  `publish`;
3.  `deploy`.

El comando correspondiente es:

``` bash
iasi-dev deploy --full [destino]
```

Si la construcción o la publicación falla, el despliegue no continúa.

## Flujo documental

Con las definiciones anteriores, el recorrido completo es:

``` text
fuentes
  → build
  → resultados de construcción
  → publish
  → artefactos en publish/
  → deploy
  → commits enviados al remoto
```

Durante la edición normal se repite `build` y se revisan los resultados. `publish` se utiliza cuando los resultados ya están preparados. `deploy` se reserva para enviar cambios.

## Clonar

En este documento, cuando decimos **clonar**, nos referimos a obtener una nueva copia local de un repositorio remoto.

El comando `iasi-dev clone` trabaja con el conjunto de repositorios IASI y, por defecto, recrea las copias existentes. `clone --resume` conserva las que ya existen y añade solo las ausentes.

## Actualizar con `pull`

En este documento, cuando decimos **actualizar con `iasi-dev pull`**, nos referimos a sustituir el estado local por el estado de la rama remota predeterminada.

No debe confundirse con una integración conservadora: el comando elimina cambios locales y archivos no seguidos.

`pull` opera siempre sobre repositorios completos. Para seleccionar uno o varios, recibe únicamente los nombres de sus directorios raíz, donde se encuentra `.git`. Sin nombres, selecciona todos los repositorios aplicables.

## Sincronizar con `sync`

En este documento, cuando decimos **sincronizar**, nos referimos a copiar desde `iasi-common` un archivo o directorio compartido hacia las copias existentes en el workspace.

`sync` no consulta GitHub, no crea commits y no despliega los cambios copiados.

## Log

En este documento, cuando decimos **log**, nos referimos al archivo con el registro detallado de una ejecución.

Los logs se guardan normalmente bajo `logs/` y utilizan una marca temporal para distinguir cada ejecución.

## Elegir la operación

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr>
<th>Quiero…</th>
<th>Operación</th>
</tr>
</thead>
<tbody>
<tr>
<td>preparar por primera vez todo el entorno IASI</td>
<td><code>init</code></td>
</tr>
<tr>
<td>recuperar todos los repositorios desde cero</td>
<td><code>clone</code></td>
</tr>
<tr>
<td>añadir únicamente los repositorios que faltan</td>
<td><code>clone --resume</code></td>
</tr>
<tr>
<td>sustituir el estado local por el remoto</td>
<td><code>pull</code></td>
</tr>
<tr>
<td>distribuir un recurso de <code>iasi-common</code></td>
<td><code>sync</code></td>
</tr>
<tr>
<td>generar resultados revisables</td>
<td><code>build</code></td>
</tr>
<tr>
<td>preparar artefactos en <code>publish/</code></td>
<td><code>publish</code></td>
</tr>
<tr>
<td>confirmar y enviar el estado ya preparado</td>
<td><code>deploy</code></td>
</tr>
<tr>
<td>construir, publicar y desplegar</td>
<td><code>deploy --full</code></td>
</tr>
<tr>
<td>confirmar y enviar todos los cambios sin tratamiento documental</td>
<td><code>commit</code></td>
</tr>
<tr>
<td>gestionar los servicios locales</td>
<td><code>docker</code></td>
</tr>
</tbody>
</table>
