# Guía de estilos de git

Esta guía de estilos toma como referencia las siguientes rutas:

* [Git Style Guide by agis-](https://github.com/agis-/git-style-guide)
* [Git branch naming conventions by lovingly](http://www.guyroutledge.co.uk/blog/git-branch-naming-conventions/)
* [Branching by digitalijhelms](https://gist.github.com/digitaljhelms/4287848)

# Contenido

1. [Branches](#branches)
2. [Commits](#commits)
  1. [Mensajes](#mensajes)
3. [Merge y Pull Requests](#merging)
4. [Issues](#issues)
5. [Extras](#misc)

# Branches

<table>
  <thead>
    <tr>
      <th>Instance</th>
      <th>Branch</th>
      <th>Descripción, Instrucciones, Notas</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Main</td>
      <td>main</td>
      <td>El código actual de producción, acepta merge únicamente de release.</td>
    </tr>
    <tr>
      <td>Release</td>
      <td>release</td>
      <td>El código actual en PPRD, acepta merge únicamente de Develop, debe estar a la par de main, solo que con su configuarción de PPRD.</td>
    </tr>
    <tr>
      <td>Develop</td>
      <td>develop</td>
      <td>El código de desarrollo, acepta merge de Feature, Hotfix, Docs y Refactoring.</td>
    </tr>
    <tr>
      <td>Feature</td>
      <td>feature/desc-corta</td>
      <td>Se crea a partir de develop, esta debe ser un componente especifico en el requerimiento.</td>
    </tr>
    <tr>
      <td>Refactoring</td>
      <td>refactoring/desc-corta</td>
      <td>Se crea a partir de develop, esta debe ser una rama para la reestructuración del proyecto.</td>
    </tr>
    <tr>
      <td>Hotfix</td>
      <td>hotfix/desc-corta</td>
      <td>Se crea a partir de develop una ves replicado el caso de producción, tiene prioridad sobre el desarrollo, pruebas y revisión de código, una vez resuelto el bug en desarrollo, se hace el cambio para release.</td>
    </tr>
    <tr>
      <td>Docs</td>
      <td>docs/desc-corta</td>
      <td>Se crea a partir de desarrollo, contiene documentacion que no es especificamente una componente de codigo, por ejemplo, esta guía.</td>
    </tr>
  </tbody>
</table>

* Eligiendo un nombre *corto* y *descriptivo*:

  ```shell
  # Bien
  $ git checkout -b feature/obtener-nuevas-reglas

  # Mal - ambiguo
  $ git checkout -b feature/fix
  ```

* Sigue la estructura tipo carpeta:

  ```shell
  # Bien
  $ git checkout -b feature/creacion-catalogo-division

  # Mal
  $ git checkout -b ft-creacion-catalogo-division
  ```

* Crea a partir de la rama debidamente:

  ``` shell
  # Bien
  $ git checkout -b feature/creacion-catalogo-division develop

  # Mal
  $ git checkout -b feature/creacion-catalogo-division main
  ```

* Utiliza *-* para separar palabras.

* Elimina tu rama una vez mergeada, a menos de que haya una razon especifica para no hacerlo.

 [Como eliminar branches desde terminal](https://makandracards.com/makandra/621-git-delete-a-branch-local-or-remote)

  Tip: Utiliza este comando en terminar para revisar que branches se han mergeado:

  ```shell
  $ git branch --merged | grep -v "\*"
  ```

# Commits

* Cada commit debe ser un unico *cambio lógico*. No realices varios
  *cambio lógicos* en un solo commit. Por ejemplo, si realizas un fix para un bug y optimizas una función mantenlas como dos commits distintos.

* No separes un *cambio lógico* en diferentes commits.

* Realiza commits *limpios* y *frecuentes*. Pequeños commits que sean faciles de entender por si algo sale mal y se tenga que hacer un revert.

* Antes de realizar un push, tu código debe estar correctamente probado y adecuado.

## Mensajes

* Escribe tus mensajes de manera correcta en presente:

  ```shell
  # good
  $ git commit -m "Algún mensaje descriptivo"
  ```

* Si el *commit A* resuelve un bug dentro producido en el *commit B*, debe ser descrito en el *commit A*.

# Merging y Pull Requests

* Al momento de crear un Merge Request deberás generar una descripción en la cual se pueda saber el motivo del merge, se sugiere basarse en el archivo PULL_REQUEST_TEMPLATE.md.

* **Prueba y documenta antes de hacer push:** No hagas un Merge Request de algo que esta a medias.

* Crea el Merge Request mediante la interfaz online de Gitlabs, llena el modelo y selecciona a la persona que revisará tu código.

* **Solo haz merge cuando tu merge request sea aceptado**

# Extras

* Usa [annotated tags](http://git-scm.com/book/en/v2/Git-Basics-Tagging#Annotated-Tags)
  para marcar liberaciones o otras cosas importantes.

* Manten tu repositorio en buena forma, usuando ocacionalemente estas tareas:

  * [`git-gc(1)`](http://git-scm.com/docs/git-gc)
  * [`git-prune(1)`](http://git-scm.com/docs/git-prune)
  * [`git-fsck(1)`](http://git-scm.com/docs/git-fsck)

# License

![cc license](http://i.creativecommons.org/l/by/4.0/88x31.png)

Este trabajo es licenciado por [Creative Commons Attribution 4.0
International license](https://creativecommons.org/licenses/by/4.0/).
