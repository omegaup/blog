---
title: 'Administración de Identidades'
weight: 4
type: docs
sidebar:
  open: true
author: 'Juan Pablo Gómez'
author_email: 'juan.pablo@omegaup.com'
date: Sat, 08 Feb 2020 22:56:22 +0000
draft: false
tags: ['Features', 'Concursos', 'Uncategorized']
aliases: ['/administracion-de-identidades']
---

Hemos liberado una nueva funcionalidad en omegaUp para que puedas administrar identidades dentro de un grupo. Si has sido organizador de un concurso o curso, seguramente has requerido de la ayuda de algún miembro de omegaUp para dar de alta las cuentas de los usuarios que participarán en el evento que organizaste con este [script](https://github.com/omegaup/omegaup/blob/73db504f8494ce00d0305931730ea35a89a8aa6b/frontend/server/controllers/UserController.php#L644). Con esta nueva funcionalidad serás capaz de realizar todas las acciones por tu cuenta.

¿Qué es una Identidad?
======================

Una identidad en omegaUp es una cuenta con los privilegios suficientes para ingresar a un curso o concurso para el cual haya sido creada. Anteriormente, para que un usuario pudiera ingresar al curso o concurso, era necesario hacer los cambios necesarios en el código descrito en el párrafo anterior.

Ventajas
aliases: ['/administracion-de-identidades']
--------

Las ventajas que se tienen con esta nueva funcionalidad se describen a continuación:

### Profesor / organizador

*   Rapidez: Al poder crear sus identidades, el organizador puede disponer de ellas en el momento que las da de alta. Ya no es necesario esperar a que se haga el despliegue con los usuarios que se pretenden agregar.
*   Control: Estas cuentas de identidades ahora las podrá visualizar en el mismo lugar donde están las cuentas de los usuarios que se agregan al curso.
*   Seguridad: Es muy importante señalar que una vez que la identidad se asocia a un concursante, esta ya no puede ser utilizada por nadie más. Ya no será necesario reutilizar cuentas.

### Alumno / participante

*   Privacidad: Siempre y cuando las identidades se den de alta con nombres genéricos, los datos de los usuarios no serán expuestos en ninguna parte de la plataforma.
*   Control: El usuario podrá agregar a su cuenta tantas identidades le sean asignadas, lo cual tiene una gran ventaja, ya que todos los problemas que resuelva con cualquiera de sus identidades serán tomados en cuenta para su rankeo.

¿Cómo funciona la Administración de Identidades?
================================================

Crear Identidades
aliases: ['/administracion-de-identidades']
-----------------

[{{< video autoplay="true" loop="true" muted="true" src="/images/Video_1-Crear_Identiades.webm" type="video/mp4" >}}](/images/Video_1-Crear_Identiades.webm)

En la animación anterior se muestra cómo crear un grupo con identidades, este proceso se describe paso a paso a continuación:

##### 1\. Ingresa a la sección de Mis Grupos.

Una vez que ingresas a omegaUp, y en el menú superior busca la opción _Concursos > Mis grupos_:

[![](/images/Imagen_1-Ingresar_Grupos.png)](/images/Imagen_1-Ingresar_Grupos.png)

##### 2\. Crear el grupo

Si ya creaste el grupo pasa al punto 3, de lo contrario presiona el botón de Crear grupo:

[![](/images/Imagen_2-Crear_Grupo.png)](/images/Imagen_2-Crear_Grupo.png)

Llena los datos de nombre y descripción del Grupo, el alias se genera automáticamente de acuerdo al nombre del grupo. Una vez que has llenado los datos, presiona el botón de _Crear grupo_:

[![](/images/Imagen_3-Crear_Nuevo_Grupo.png)](/images/Imagen_3-Crear_Nuevo_Grupo.png)

##### 3\. Selecciona el grupo

Busca tu grupo en el listado, al encontrarlo da clic sobre el para que te mande al detalle:

[![](/images/Imagen_4-Seleccionar_Grupo.png)](/images/Imagen_4-Seleccionar_Grupo.png)

##### 4\. Crear las identidades

Si cuentas con los permisos suficientes, en esta pantalla encontrarás una pestaña de _Crear identidades_, al dar clic en ella te aparecerá lo siguiente:

[![](/images/Imagen_5-Seleccionar_Archivo.png)](/images/Imagen_5-Seleccionar_Archivo.png)

Vas a ver un botón que dice _seleccionar el archivo_, da clic para que puedas cargar un archivo en formato CSV.

> Nota: Esta característica aún está en etapa de experimentación, así  que si requieres subir un archivo con identidades, es necesario que envíes un correo a [engineering@omegaup.com](mailto:engineering@omegaup.com) con tu nombre de usuario y el motivo para el que utilizarás la funcionalidad.

##### 5\. Llena el archivo

Si ya tienes el archivo CSV con las identidades a crear, pasa al punto 6, de lo contrario aquí te indicamos cómo generarlo.

[Aquí](https://docs.google.com/spreadsheets/d/1okGOLoZc7l6pz8GFba0sjcETsJducJ8as8hpikhYq-g/edit?usp=sharing) puedes descargar la plantilla para que puedas registrar a todos los usuarios desde algún programa de Hoja de cálculo. Cuando guardes los cambios cerciórate de que el archivo lo guardas en el formato correcto (CSV). Este es el [ejemplo](https://docs.google.com/spreadsheets/d/1WiBrXf7MfU5zf2iUC8CD_WmnlwXQ_Qoo8UaEZ0ixFyU/edit?usp=sharing) de un archivo para subir.

Las consideraciones que debes tener al crear el archivo son las siguientes:

Todos los campos son obligatorios y deben seguir con las siguientes reglas:

*   **username**: Mismas reglas que cuando se da de alta un usuario desde la página de registro.
*   **name**: Mismas reglas que cuando se da de alta un usuario desde la página de registro.
*   **country\_id**: Debes ingresar el código del país o la región según [iso3166-2](https://en.wikipedia.org/wiki/ISO_3166-2), ejemplo: Si los concursantes son de México, entonces debes escribir el código MX.
*   **state\_id**: Mismo caso que el campo anterior, debes buscar el código del estado/provincia/distrito al que pertenezca según [iso3166-2](https://www.gefeg.com/edifact/d03a/s3/codes/cl1h.htm), este código está compuesto por \[país o región-estado o provincia o distrito\]. Sólo escribe los dígitos que están después del caracter -. Ejemplo: Si los concursantes son de Guanajuato, México, debes escribir GUA.
*   **gender**: Si tienes identificados a los concursantes, puedes indicar una de las siguientes opciones: \[male, female, other, decline\]. Recuerda que si escribes cualquier cosa distinta a las 4 opciones listadas, te aparecerá un error al querer subir el archivo.
*   **school**: Si ya tienes registrada la escuela en la plataforma, escribe el nombre tal cual está dada de alta, de lo contrario, se va a generar un nuevo registro de escuela.

Guarda el archivo en formato CSV como se mencionó anteriormente.

##### 6\. Sube el archivo

Elige el archivo con las identidades que deseas dar de alta y da clic en abrir:

[![](/images/Imagen_6-Abrir_Archivo.png)](/images/Imagen_6-Abrir_Archivo.png)

Todas las identidades te deben de aparecer en formato de tabla como se muestra en la siguiente imagen:

[![](/images/Imagen_7-Crear_Identidades.png)](/images/Imagen_7-Crear_Identidades.png)

Una vez que las puedas visualizar, revisa que los datos son correctos. En caso de que tengas información incorrecta, vuelve a modificar tu archivo de identidades, guárdalo y regresa al punto 4.

Si los datos son los correctos, da clic en el botón de Crear identidades. Listo, ahora ya cuentas con identidades ligadas a un grupo.

Como puedes notar, en la tabla de arriba se visualizan las contraseñas asignadas a cada identidad, es recomendable que las guardes en algún lugar seguro para posteriormente compartirlas con los participantes de tu concurso o curso (lo puedes hacer presionando el botón  [![](/images/Imagen_8-Descargar.png)](/images/Imagen_8-Descargar.png) que aparece justo debajo del botón de _Crear Identidades_) ya que si te sales de esta pantalla, no las podrás volver a consultar.

Nota: Las contraseñas se _hashean_ y se almacenan en la base de datos: quiere decir que ya no se puede revertir para visualizar la contraseña.

Para tener un mejor control sobre las identidades que creaste, estas cuentan con un identificador en el username: **_\[nombre-del-grupo:username\]_**, de esta forma siempre tendremos una asociación directa entre identidades y grupo.

En caso de que no hayas guardado las contraseñas, no te preocupes, las puedes regenerar volviendo a subir el .csv. Alternativamente si sólo quieres restablecer la contraseña de un sólo alumno, puedes hacer eso desde la pestaña de miembros, tal como se muestra en la siguiente animación:

[{{< video autoplay="true" loop="true" muted="true" src="/images/Video_2-Cambiar_Password.webm" type="video/mp4" >}}](/images/Video_2-Cambiar_Password.webm)

Cambiar Password
aliases: ['/administracion-de-identidades']
----------------

También puedes editar información de las identidades, recuerda que solamente el creador de las identidades puede realizar esta acción. La forma de hacerlo se muestra en la siguiente animación:

[{{< video autoplay="true" loop="true" muted="true" src="/images/Video_3-Actualizar_Info_Basica.webm" type="video/mp4" >}}](/images/Video_3-Actualizar_Info_Basica.webm)

Actualizar información básica
aliases: ['/administracion-de-identidades']
-----------------------------

Ya que le compartiste las identidades a los respectivos participantes, ellos pueden ingresar a la plataforma de la misma forma que cualquier otro usuario, la diferencia que van a notar es que estas cuentas no podrán editar sus datos, en la siguiente animación se muestra:

[{{< video autoplay="true" loop="true" muted="true" src="/images/Video_4-Ingresar_Omegaup.webm" type="video/mp4" >}}](/images/Video_4-Ingresar_Omegaup.webm)

Ingresar a omegaUp por medio de una identidad
=============================================

Un caso que pudiera ser muy común es que un usuario tenga que agregar varias identidades.

Supongamos el siguiente ejemplo: El alumno Juan Pérez utiliza frecuentemente la plataforma de omegaUp, porque en ella puede practicar con problemas de programación. En la escuela que asiste, su maestra decidió crear un curso en la plataforma y dio de alta las identidades con las que quiere que ingresen sus alumnos. Además, por su buen desempeño, Juan es invitado a un concurso estatal de programación, donde el organizador ya ha creado las identidades con las que ingresarán los participantes de dicho concurso.

En este caso Juan ya cuenta con su usuario de la plataforma, y aparte le han compartido dos cuentas con identidades adicionales. Si quiere que todos los problemas que resuelva tanto en su escuela, como en el concurso sean contabilizados para su posición en la tabla de mejores coders, lo que debe hacer es lo que se muestra en la siguiente animación:

[{{< video autoplay="true" loop="true" muted="true" src="/images/Video_5-Vincular_Identidad_Usuario.webm" type="video/mp4" >}}](/images/Video_5-Vincular_Identidad_Usuario.webm)

Vincular identidad con usuario
==============================

El usuario debe ingresar a omegaUp con su cuenta que comúnmente utiliza.

Después debe dirigirse a _Mi perfil_ en el menú superior derecho, y después da clic en _Editar Perfil_ tal como se muestra en la siguiente imagen:

[![](/images/Imagen_9-Editar_Perfil.png)](/images/Imagen_9-Editar_Perfil.png)

Una vez que dentro de la pantalla de Editar Perfil, si se desplaza un poco, debajo de Editar tu perfil se puede encontrar la sección de Administrar Identidades. Sólo es cuestión de que agregue el username y la contraseña de la identidad para que esta se asocie a la cuenta.

[![](/images/Imagen_10-Vincular_Identidad.png)](/images/Imagen_10-Vincular_Identidad.png)

Atentamente, El equipo de omegaUp