---
title: 'Concursos por equipos'
author: 'Juan Pablo Gómez'
author_email: 'juan.pablo@omegaup.com'
date: Thu, 24 Mar 2022 14:35:06 +0000
draft: false
tags: ['Uncategorized']
---

Nos es grato informar que hemos liberado una nueva funcionalidad llamada **"Concursos por equipos"**, para poder atender los concursos con formato de **ICPC**, los cuales se realizan en equipos. Para que esta nueva modalidad de concursos pueda utilizarse, también se han liberado algunas características extras que se describirán más adelante.

Si estás familiarizado con la plataforma encontrarás similitud con funcionalidades que ya existen desde hace tiempo. Si no es el caso, comenzamos con el primer paso.

1.- Creación de grupo de equipos
======================

Para tener un mejor control de los equipos que van a participar en un concurso con la modalidad de equipos, es necesario crear un grupo de equipos, el cual es muy similar a los grupos que se utilizan al día de hoy, sólo que en este caso existen algunas variantes, ya que en lugar de identidades se agregarán equipos que contienen usuarios y/o identidades.

Para crear el grupo es necesario ir al menú superior derecho y elegir la opción de *Mis grupos de equipos*. Aquí se mostrará el listado de grupos de equipos que hayas creado, con la opción de editarlos. En caso de ser la primera vez que ingresas, sólo te aparecerá el botón de Crear nuevo grupo de equipos.

En esta pantalla encontrarás un formulario donde tendrás que ingresar el nombre del grupo, una breve descripción que indique el propósito del mismo y el número límite de integrantes permitidos por equipo. El alias no es necesario escribirlo ya que se autogenera de acuerdo al nombre que indiques. En caso de que el alias ya sea utilizado en otro grupo de equipos, habrá necesidad de elegir un nombre distinto para que se regenere el alias, así hasta encontrar uno disponible.

En la siguiente animación se muestra lo mencionado anteriormente:

<iframe width="560" height="315" src="https://www.youtube.com/embed/CdbX11oY_yc" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

2.- Carga de equipos
======================

Una vez que guardas el grupo, te aparecerá la vista de edición, y se seleccionará la pestaña de cargar equipos. Este paso es similar a la carga de identidades de un grupo, en este [post](https://blog.omegaup.com/administracion-de-identidades/) puedes ver la manera de cargar el archivo. La diferencia con ese proceso es que estas identidades son para equipos, quiere decir que dentro de cada identidad se podrán asociar tantos miembros como se hayan configurado en el formulario de *Crear grupo de equipos*. Estos miembros se pueden cargar en el archivo ***.csv***, en caso de que conozcas los nombres de usuarios (*usernames*) de cada miembro o lo puedes hacer posteriormente en la pestaña de equipos donde podrás agregarlos manualmente a cada equipo.

La regla principal en la creación de equipos es que un usuario no puede pertenecer a dos equipos distintos del mismo grupo de equipos. Así que si por equivocación se llegara a intentar realizar esta acción, la plataforma mandaría un mensaje de error.

Cabe destacar que la carga de identidades y equipos está en una etapa experimental que aún no se abre en su totalidad al público en general hasta probar que se le está dando un uso adecuado, así que si estás interesado en crear grupos de equipos, nos puedes escribir a engineering@omegaup.com para que te podamos habilitar los privilegios necesarios.

En la siguiente animación se muestra el proceso de lo antes descrito:

<iframe width="560" height="315" src="https://www.youtube.com/embed/mgR6EclyRHw" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## 2.1.- Carga de equipos con identidades auto-generadas

Habrá ocasiones en que se requiera organizar un concurso con una gran cantidad de equipos, lo cual hará más complicada la carga de los miembros de cada equipo debido a que este número pudiera llegar a ser demasiado grande. 

Para esta situación se considera una opción de generar las identidades para cada equipo una vez que se carga el archivo ***.csv***. Esto quiere decir que sólo será necesario cargar el archivo sin incluir nombres de usuarios, y en su lugar habrá que seleccionar la casilla de Autogenerar identidades que se encuentra en el formulario. Para este caso en particular es de suma importancia descargar el archivo con las identidades que se generaron antes de guardar los cambios, ya que aquí se van a mostrar el listado de usernames junto a su contraseña, la cual sólo se podrá visualizar en este punto, ya que al guardar los cambios estas contraseñas de van a encriptar. Lo cual ocasionará que ya no sea posible volverlas a ver en la plataforma.

En la siguiente animación se muestra el proceso antes mencionado:

<iframe width="560" height="315" src="https://www.youtube.com/embed/Yx9xzIe_FAU" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

3.- Creación de concurso por equipos
======================

Una vez que ya hayas creado los grupos de equipo, es momento de generar el concurso por equipos. En este caso, el formulario es exactamente el mismo que se utiliza para  cualquier tipo de concurso, sólo que ahora se agregó un nuevo campo en el formulario llamado *Concurso por equipos* y aparece como una casilla de tipo checkbox. Al momento de activar dicha casilla también se habilita un campo de texto donde tendrás que buscar el grupo de equipos, ya sea por nombre o por alias. En caso de tener activa la casilla, pero no hayas escrito el nombre del grupo, obtendrás un error indicando que este campo es obligatorio.

Ya que se haya creado el concurso, te aparecerá la vista de *Editar concurso*, y a diferencia de los concursos normales, en este tipo de concurso verás en las opciones una sección de *Agregar grupo*, en lugar de la opción de *Agregar concursante*, debido a lo explicado al inicio de este post. También se oculta la opción de *Modo de acceso*, esto con la finalidad  de evitar que se creen concursos para equipos públicos (sólo por el momento, en un futuro se evaluará si se abre esta opción).

En la sección de *Agregar grupo* podrás reemplazar al equipo, siempre y cuando ninguno de los equipos haya realizado al menos un envío de alguno de los problemas.

En la siguiente animación se muestra todo lo que se comentó previamente:

<iframe width="560" height="315" src="https://www.youtube.com/embed/G_X_-NCOblU" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## 3.1.- Ingreso como equipo con cuenta previamente existente

Una vez que ya se creó el grupo de equipos y el concurso por equipos. Es momento de notificar a los usuarios que fueron inscritos al concurso por medio de un equipo, para que puedan acceder al concurso.

Cabe destacar que estos usuarios ya contarán con una identidad de equipo, la cual se muestra en el menú superior derecho. La forma de distinguir una identidad  de una identidad de equipo es por la nomenclatura del nombre de usuario (*username*). La nomenclatura de una identidad de grupo es la siguiente:

 [`group_name`]:[`identity_name` ].

En tanto la nomenclatura de las identidades de un grupo de equipos es la siguiente:

`teams`:[`group_name`]:[`identity_name`].

Entonces, para poder visualizar el concurso que fue creado para equipos es necesario hacer un intercambio a la sesión de esta nueva identidad a la que fue asociado el concursante.

En la siguiente animación se muestra lo mencionado anteriormente:

<iframe width="560" height="315" src="https://www.youtube.com/embed/qiD2ElDky5o" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## 3.2.- Ingreso como equipo con cuenta auto-generada

En el caso de las identidades que se crearon mediante la carga de archivo ***.csv*** y se eligió la opción de *Autogenerar identidades* ya no es necesario hacer el cambio de cuenta para poder ver el concurso en el listado. Esto quiere decir que una vez que inicia sesión aparecerá el nombre del equipo en la parte superior derecha, tal como se muestra en la siguiente animación:

<iframe width="560" height="315" src="https://www.youtube.com/embed/JYjPwfR07EM" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

4.- Envío de soluciones a problemas de concurso por equipos
======================

Por último, ya que el usuario encontró el concurso por equipos al que fue añadido sólo será necesario que ingrese a dicho concurso y comience a realizar envíos a las soluciones de los problemas. Al ser un concurso por equipos, los integrantes del equipo también podrán acceder de la misma forma y todos podrán realizar envíos simultáneamente. Las reglas del concurso son las mismas que en el resto de concursos, no podrán realizar envíos de un mismo problema hasta que haya transcurrido el tiempo entre cada envío con el que fue configurado el concurso (60 segundos por defecto).

En la animación se muestra un ejemplo de lo antes mencionado:

<iframe width="560" height="315" src="https://www.youtube.com/embed/1JR_xw9JQzs" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Atentamente, el equipo de omegaUp.
