---
title: 'Revisión de código en envíos de cursos'
author: 'Juan Pablo Gómez'
author_email: 'juan.pablo@omegaup.com'
date: Thu, 19 Aug 2024 23:12:06 +0000
draft: false
tags: ['Anuncios', 'omegaUp']
---

Nos es grato informar que hemos liberado una nueva funcionalidad llamada **“Revisión de código en envíos de cursos”**, la cual servirá para que organizadores de cursos puedan brindar retroalimentación de los envíos de sus estudiantes directamente en el código que se han enviado. Permitiendo agilizar el proceso de revisiones.

## Antecedentes


Anteriormente en los cursos de _omegaUp_ solamente se contaba con una campo general donde se podía escribir una retroalimentación por cada envío que creaba el estudiante. Esto ocasionaba que el organizador no tuviera las herramientas suficientes para detallar si es que se requería.

Esta retroalimentación se podía editar, pero al realizar la modificación el mensaje original no se podía volver a ver.

Con esta nueva funcionalidad se pretende que el organizador tenga más posibilidades al dar una retroalimentación dentro de un envío. Además de que tenga la posibilidad de registrar una lista de usuarios que puedan ayudar en la tarea de revisión de código tan importante en el tema de desarrollo de software.

## Definición de la nueva funcionalidad

Para explicar como funcionarán las retroalimentaciones de código es necesario iniciar explicando la creación de un nuevo rol dentro de los cursos en _omegaUp_

## Rol de asistente de enseñanza

Con la creación de la nueva funcionalidad la tarea de revisiones de código puede llegar a crecer de tal forma que el organizador del curso se pueda ver rebasado en el momento que una gran cantidad de estudiantes soliciten retroalimentación en sus soluciones enviadas.

La primera alternativa para solventar este problema es que el organizador agregue más administradores del curso los cuales tendrán los mismos privilegios que el organizador, por ende tendrán la posibilidad de realizar revisiones de código.

El problema principal de esto es que todos los administradores pueden modificar la configuración del curso. Lo cual no es lo recomendable porque el organizador podría perder el control las tareas, fechas, listado de problemas, entre otras cosas.

Es por eso que se tomó la decisión de crear este nuevo rol, el cual permite al organizador agregar tantos usuarios requiera con el perfil de **asistentes de enseñanza** dentro de un curso.

## ¿Cómo agregar asistentes de enseñanza en un curso?

El proceso para agregar asistentes de enseñanza es similar a la forma en la que se agrega un administrador. Como se puede mostrar en la _imagen 1_ Lo primero que se tiene que hacer es ingresar a la vista de _Editar curso_ que se encuentra en la sección de _Cursos que administro_:

{{< figure src="/images/image_01-Courses_List.png" alt="Image 1"  height="146" width="549" link="/images/image_01-Courses_List.png" >}}

Y después ir al tab de _Admins_ donde se podrá agregar cuentas individuales o si así se prefiere, agregar un grupo de cuentas:

{{< figure src="/images/image_02-Course_Edit_Admins.png" alt="Image 2"  height="329" width="549" link="/images/image_02-Course_Edit_Admins.png" >}}

Una vez realizados los pasos anteriores todas las cuentas que les fue asignado el rol de **Asistente de enseñanza** podrán ingresar al curso donde podrán dar retroalimentación a cualquier envío que vayan subiendo los estudiantes.

{{< figure src="/images/Image_03-Courses_List_TA.png" alt="Image 3" height="160" width="549" link="/images/Image_03-Courses_List_TA.png" >}}

Los **Asistentes de enseñanza** sólo pueden ver los detalles del curso, pero no pueden editar nada del mismo, como se muestra en la siguiente imagen:

{{< figure src="/images/Image_04-Course_Details_TA.png" alt="Image 4" height="363" width="549" link="/images/Image_04-Course_Details_TA.png" >}}

## ¿Cómo puedo solicitar retroalimentación si soy estudiante?

El proceso para solicitar retroalimentación como estudiantes es sencillo. Una vez que se ha ingresado a alguna actividad de un curso y se realiza un envío a cualquiera de los problemas, los estudiantes encontrarán un botón en la tabla de envíos de dicho problema:

{{< figure src="/images/Image_05-Runs_List_Student_Requests_Feedback.png" alt="Image 5" height="152" width="549" link="/images/Image_05-Runs_List_Student_Requests_Feedback.png" >}}

Al dar click en el botón se enviará una notificación a todos los organizadores y asistentes de enseñanza del curso. Así que sólo habrá que esperar su retroalimentación.

## ¿Cómo brindo retroalimentación siendo organizador del curso o asistente de enseñanza?

Una vez que el organizador del curso o **Asistente de enseñanza** reciben la notificación de que un usuario solicitó retroalimentación en un envío, puede brindarla de la siguiente manera:

Ingresarán al curso y a la tarea correspondiente, después seleccionan el tab de __Envíos__ y por último dan click en el botón de detalles del envío al que darán retroalimentación. Es fácil identificarlos, debido a que muestran un globo indicando que tienen una solicitud de revisión, como se muestra a continuación:

{{< figure src="/images/Image_06-Runs_List_Admin_Notification.png" alt="Image 6" height="137" width="549" link="/images/Image_06-Runs_List_Admin_Notification.png" >}}

Al dar clic en el botón de los detalles del envío, ahora será posible agregar comentarios de retroalimentación en las líneas de código donde el organizador considere se pueda agregar comentarios que ayuden a que el estudiante comprenda en que puede mejorar su código. En la siguiente animación se muestra la manera en la que se puede realizar:

{{< figure src="/images/Image_07-Admin_Feedback.gif" alt="Image 7" height="344" width="549" link="/images/Image_07-Admin_Feedback.gif" >}}

En este momento se abre la comunicación entre estudiante y organizador del curso, debido a que los estudiantes ahora pueden interactuar en cada uno de los comentarios brindados por los organizadores, en la siguiente imagen se muestra lo antes mencionado:

{{< figure src="/images/Image_08-Student_Response.gif" alt="Image 8"  width="549" link="/images/Image_08-Student_Response.gif" >}}

Esta nueva funcionalidad se recomienda para cursos que no son precenciales en donde la distancia entre organizadores y estudiantes ya no será una barrera, pero también muy útil para profesores que cuentan con mucha caraga de trabajo y puedan apoyarse de asistentes para la labor de revisar código de los estudiantes.
