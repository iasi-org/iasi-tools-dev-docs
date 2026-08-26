

## Operaciones que pueden sobrescribir trabajo

Preste especial atención a estos comandos:

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr>
<th>Comando</th>
<th>Riesgo principal</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>clone</code></td>
<td>elimina destinos existentes antes de clonarlos, salvo con <code>--resume</code></td>
</tr>
<tr>
<td><code>pull</code></td>
<td>restablece al remoto y elimina archivos no seguidos</td>
</tr>
<tr>
<td><code>sync</code> sobre un directorio</td>
<td>reemplaza completamente las copias existentes</td>
</tr>
<tr>
<td><code>commit</code></td>
<td>incluye todos los cambios del repositorio seleccionado</td>
</tr>
<tr>
<td><code>deploy</code></td>
<td>crea commits y realiza <code>push</code></td>
</tr>
</tbody>
</table>

Antes de utilizarlos, revise `git status`, confirme las rutas resueltas y haga una copia externa de cualquier trabajo que no esté confirmado.

Las opciones `-y` y `--yes` eliminan la confirmación; no reducen el alcance ni hacen recuperable la operación.

## El comando no se encuentra

Compruebe que está usando Bash y que el directorio `iasi-tools-dev/bin` pertenece a `PATH`:

``` bash
command -v iasi-dev
iasi-dev help
```

## Un subcomando rechaza una opción

Las opciones no son globales. Consulte la ayuda específica:

``` bash
iasi-dev help <comando>
```

Por ejemplo, `-s` está disponible en algunas operaciones de workspace, pero no en `build` o `publish`.

## No se encuentra ninguna publicación

Compruebe que el destino contiene una publicación reconocible por `iasi.quarto` y que no está dentro de un directorio `tests`, excluido del descubrimiento.

Si solo desea una publicación anidada, pase su ruta exacta. Si desea todo el multiproyecto, pase la raíz que contiene las publicaciones.

También puede haberse ejecutado el comando desde un directorio distinto del esperado. Repita la operación con una ruta explícita para eliminar esa ambigüedad.

## Faltan `Rscript` o Quarto

Compruebe que ambos comandos están disponibles desde la misma sesión de Bash en la que ejecuta `iasi-dev`:

``` bash
command -v Rscript
command -v quarto
```

La presencia del CLI `iasi-dev` no implica que estas dependencias estén instaladas.

## Fallo de GitHub o Git

Compruebe autenticación y remotos:

``` bash
gh auth status
git remote -v
```

Para `commit` y `deploy`, verifique también que la rama admite `push` y que no necesita integrar cambios remotos.

## No hay cambios para desplegar

Compruebe el estado del repositorio:

``` bash
git status
```

Si esperaba cambios en `publish/`, asegúrese de haber ejecutado antes `publish` o utilice `deploy --full`. Construir una publicación no implica por sí solo preparar o desplegar sus artefactos.

## Fallo de Docker

``` bash
iasi-dev docker status
docker compose version
```

Revise si los puertos configurados ya están ocupados y consulte los logs del servicio afectado con Docker.

## Consultar el log correcto

Busque en el directorio `logs/` del workspace el archivo cuyo nombre corresponde a la operación y a su marca temporal, por ejemplo:

``` text
iasi-build-YYYYMMDDhhmmss.log
iasi-publish-YYYYMMDDhhmmss.log
iasi-pull-YYYYMMDDhhmmss.log
```

Al informar de un problema incluya el comando exacto, la ruta desde la que se ejecutó, el código de salida y el log correspondiente, eliminando previamente credenciales o datos sensibles.
