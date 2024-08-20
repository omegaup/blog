---
title: 'Revisión de código en envíos de cursos'
author: 'Juan Pablo Gómez'
author_email: 'juan.pablo@omegaup.com'
date: Thu, 19 Aug 2024 23:12:06 +0000
draft: false
tags: ['Anuncios', 'omegaUp']
---

Nos complace anunciar la liberación de una nueva funcionalidad llamada **“Revisión de código en envíos de cursos”**. Esta herramienta permitirá a los organizadores de cursos brindar retroalimentación directamente en el código enviado por sus estudiantes, agilizando así el proceso de revisión.

## Antecedentes

Anteriormente, en los cursos de _omegaUp_, solo se disponía de un campo general para escribir retroalimentación por cada envío realizado por el estudiante. Esto impedía que el organizador contara con las herramientas necesarias para detallar adecuadamente los comentarios.

Aunque esta retroalimentación podía ser editada, al modificar el mensaje original, este ya no podía ser visualizado nuevamente.

Con esta nueva funcionalidad, se busca que el organizador tenga más opciones para proporcionar retroalimentación detallada en cada envío. Además, se ofrece la posibilidad de registrar una lista de usuarios que puedan colaborar en la importante tarea de revisión de código, fundamental en el desarrollo de software.

## Definición de la nueva funcionalidad

Para entender cómo funcionarán las retroalimentaciones de código, es necesario comenzar explicando la creación de un nuevo rol dentro de los cursos en _omegaUp_.

## Rol de asistente de enseñanza

Con la creación de la nueva funcionalidad, la tarea de revisión de código puede aumentar significativamente, al punto de que el organizador del curso se vea abrumado cuando una gran cantidad de estudiantes soliciten retroalimentación en sus soluciones enviadas.

La primera alternativa para solucionar este problema es que el organizador agregue más administradores al curso. Estos administradores tendrán los mismos privilegios que el organizador, incluyendo la capacidad de realizar revisiones de código.

El principal inconveniente de esta solución es que todos los administradores pueden modificar la configuración del curso, lo cual no es recomendable, ya que el organizador podría perder el control sobre las tareas, fechas, listado de problemas, entre otras cosas.

Por esta razón, se decidió crear un nuevo rol que permite al organizador agregar tantos usuarios como sea necesario con el perfil de **asistentes de enseñanza** dentro de un curso.

## ¿Cómo agregar asistentes de enseñanza en un curso?

El proceso para agregar asistentes de enseñanza es similar al de agregar un administrador. Como se muestra en la _imagen 1_, lo primero que se debe hacer es ingresar a la vista de _Editar curso_ en la sección de _Cursos que administro_:

{{< figure src="/images/image_01-Courses_List.png" alt="Imagen 1" height="146" width="549" link="/images/image_01-Courses_List.png" >}}

Luego, dirígete a la pestaña de _Admins_, donde podrás agregar cuentas individuales o, si lo prefieres, un grupo de cuentas:

{{< figure src="/images/image_02-Course_Edit_Admins.png" alt="Imagen 2" height="329" width="549" link="/images/image_02-Course_Edit_Admins.png" >}}

Una vez realizados estos pasos, todas las cuentas a las que se les haya asignado el rol de **Asistente de enseñanza** podrán ingresar al curso y proporcionar retroalimentación a cualquier envío realizado por los estudiantes.

{{< figure src="/images/Image_03-Courses_List_TA.png" alt="Imagen 3" height="160" width="549" link="/images/Image_03-Courses_List_TA.png" >}}

Los **Asistentes de enseñanza** solo pueden ver los detalles del curso, pero no pueden editar nada, como se muestra en la siguiente imagen:

{{< figure src="/images/Image_04-Course_Details_TA.png" alt="Imagen 4" height="363" width="549" link="/images/Image_04-Course_Details_TA.png" >}}

## ¿Cómo puedo solicitar retroalimentación si soy estudiante?

El proceso para solicitar retroalimentación como estudiante es sencillo. Una vez que hayas ingresado a una actividad de un curso y realizado un envío a cualquiera de los problemas, encontrarás un botón en la tabla de envíos de dicho problema:

{{< figure src="/images/Image_05-Runs_List_Student_Requests_Feedback.png" alt="Imagen 5" height="152" width="549" link="/images/Image_05-Runs_List_Student_Requests_Feedback.png" >}}

Al hacer clic en el botón, se enviará una notificación a todos los organizadores y asistentes de enseñanza del curso. Solo tendrás que esperar su retroalimentación.

## ¿Cómo brindar retroalimentación como organizador del curso o asistente de enseñanza?

Una vez que el organizador del curso o el **Asistente de enseñanza** reciben la notificación de que un usuario ha solicitado retroalimentación en un envío, pueden proceder de la siguiente manera:

1. Ingresar al curso y a la tarea correspondiente.
2. Seleccionar la pestaña de __Envíos__.
3. Hacer clic en el botón de detalles del envío al que se dará retroalimentación. Estos envíos son fáciles de identificar, ya que muestran un globo indicando que tienen una solicitud de revisión, como se muestra a continuación:

{{< figure src="/images/Image_06-Runs_List_Admin_Notification.png" alt="Imagen 6" height="137" width="549" link="/images/Image_06-Runs_List_Admin_Notification.png" >}}

Al hacer clic en el botón de detalles del envío, será posible agregar comentarios de retroalimentación en las líneas de código donde el organizador considere necesario. Estos comentarios ayudarán al estudiante a comprender en qué puede mejorar su código. En la siguiente animación se muestra cómo realizar este proceso:

{{< figure src="/images/Image_07-Admin_Feedback.gif" alt="Imagen 7" height="344" width="549" link="/images/Image_07-Admin_Feedback.gif" >}}

En este momento se abre la comunicación entre el estudiante y el organizador del curso, ya que los estudiantes pueden interactuar en cada uno de los comentarios brindados por los organizadores. En la siguiente imagen se muestra lo antes mencionado:

{{< figure src="/images/Image_08-Student_Response.gif" alt="Imagen 8" width="549" link="/images/Image_08-Student_Response.gif" >}}

## Conclusión

La nueva funcionalidad de revisión de código en _omegaUp_ transforma la manera en que los organizadores de cursos y asistentes de enseñanza pueden interactuar con los estudiantes. Al permitir una retroalimentación detallada y específica en el código, se mejora significativamente el proceso de aprendizaje y se facilita la comunicación efectiva entre todas las partes involucradas.

Esta herramienta es especialmente valiosa para cursos en línea y para profesores con una gran carga de trabajo, ya que permite delegar la tarea de revisión sin perder el control sobre el contenido del curso.

Invitamos a todos los organizadores de cursos a aprovechar esta nueva funcionalidad y a experimentar de primera mano los beneficios de una retroalimentación más precisa y eficiente. ¡Empieza hoy mismo a mejorar la calidad de tus cursos con la revisión de código en _omegaUp_!