---
title: 'Revisión de código en envíos de cursos'
author: 'Juan Pablo Gómez'
author_email: 'juan.pablo@omegaup.com'
date: Thu, 19 Aug 2024 23:12:06 +0000
draft: false
tags: ['Features', 'Cursos']
---

Nos complace anunciar la liberación de una nueva funcionalidad llamada **“Revisión de código en envíos de cursos”**. Esta herramienta permitirá a las personas organizadoras de cursos brindar retroalimentación directamente en el código enviado por sus estudiantes, agilizando así el proceso de revisión.

## Antecedentes

Anteriormente, en los cursos de _omegaUp_, solo se disponía de un campo general para escribir retroalimentación por cada envío realizado por la persona estudiante. Esto impedía que la persona organizadora contara con las herramientas necesarias para detallar adecuadamente los comentarios.

Aunque esta retroalimentación podía ser editada, al modificar el mensaje original, este ya no podía ser visualizado nuevamente.

Con esta nueva funcionalidad, se busca que la persona organizadora tenga más opciones para proporcionar retroalimentación detallada en cada envío. Además, se ofrece la posibilidad de registrar una lista de personas que puedan colaborar en la importante tarea de revisión de código, fundamental en el desarrollo de software.

## Definición de la nueva funcionalidad

Para entender cómo funcionarán las retroalimentaciones de código, es necesario comenzar explicando la creación de un nuevo rol dentro de los cursos en _omegaUp_.

## Rol de asistente de enseñanza

Con la creación de la nueva funcionalidad, la tarea de revisión de código puede aumentar significativamente, al punto de que la persona organizadora del curso se vea abrumada cuando una gran cantidad de estudiantes soliciten retroalimentación en sus soluciones enviadas.

La primera alternativa para solucionar este problema es que la persona organizadora agregue más administradores al curso. Estos administradores tendrán los mismos privilegios que la persona organizadora, incluyendo la capacidad de realizar revisiones de código.

El principal inconveniente de esta solución es que todas las personas administradoras pueden modificar la configuración del curso, lo cual no es recomendable, ya que la persona organizadora podría perder el control sobre las tareas, fechas, listado de problemas, entre otras cosas.

Por esta razón, se decidió crear un nuevo rol que permite a la persona organizadora agregar tantas personas como sea necesario con el perfil de **asistentes de enseñanza** dentro de un curso.

## ¿Cómo agregar asistentes de enseñanza en un curso?

El proceso para agregar **asistentes de enseñanza** es similar al de agregar una persona administradora. Como se muestra en la _imagen 1_, lo primero que se debe hacer es ingresar a la vista de _Editar curso_ en la sección de _Cursos que administro_:

{{< figure src="/images/image_01-Courses_List.png" alt="Imagen 1" height="146" width="549" link="/images/image_01-Courses_List.png" >}}

Luego, dirígete a la pestaña de _Admins_, donde podrás agregar cuentas individuales o, si lo prefieres, un grupo de cuentas:

{{< figure src="/images/image_02-Course_Edit_Admins.png" alt="Imagen 2" height="329" width="549" link="/images/image_02-Course_Edit_Admins.png" >}}

Una vez realizados estos pasos, todas las cuentas a las que se les haya asignado el rol de **asistente de enseñanza** podrán ingresar al curso y proporcionar retroalimentación a cualquier envío realizado por las personas estudiantes.

{{< figure src="/images/Image_03-Courses_List_TA.png" alt="Imagen 3" height="160" width="549" link="/images/Image_03-Courses_List_TA.png" >}}

Las personas con el rol de **asistentes de enseñanza** solo pueden ver los detalles del curso, pero no pueden editar nada, como se muestra en la siguiente imagen:

{{< figure src="/images/Image_04-Course_Details_TA.png" alt="Imagen 4" height="363" width="549" link="/images/Image_04-Course_Details_TA.png" >}}

## ¿Cómo puedo solicitar retroalimentación si soy estudiante?

El proceso para solicitar retroalimentación como estudiante es sencillo. Una vez que hayas ingresado a una actividad de un curso y realizado un envío a cualquiera de los problemas, encontrarás un botón en la tabla de envíos de dicho problema:

{{< figure src="/images/Image_05-Runs_List_Student_Requests_Feedback.png" alt="Imagen 5" height="152" width="549" link="/images/Image_05-Runs_List_Student_Requests_Feedback.png" >}}

Al hacer clic en el botón, se enviará una notificación a todas las personas organizadoras y **asistentes de enseñanza** del curso. Solo tendrás que esperar su retroalimentación.

## ¿Cómo brindar retroalimentación como organizador del curso o asistente de enseñanza?

Una vez que la persona organizadora del curso o el **asistente de enseñanza** reciben la notificación de que un estudiante ha solicitado retroalimentación en un envío, pueden proceder de la siguiente manera:

1. Ingresar al curso y a la tarea correspondiente.
2. Seleccionar la pestaña de __Envíos__.
3. Hacer clic en el botón de detalles del envío al que se dará retroalimentación. Estos envíos son fáciles de identificar, ya que muestran un globo indicando que tienen una solicitud de revisión, como se muestra a continuación:

{{< figure src="/images/Image_06-Runs_List_Admin_Notification.png" alt="Imagen 6" height="137" width="549" link="/images/Image_06-Runs_List_Admin_Notification.png" >}}

Al hacer clic en el botón de detalles del envío, será posible agregar comentarios de retroalimentación en las líneas de código donde la persona organizadora considere necesario. Estos comentarios ayudarán a la persona estudiante a comprender en qué puede mejorar su código. En la siguiente animación se muestra cómo realizar este proceso:

{{< figure src="/images/Image_07-Admin_Feedback.gif" alt="Imagen 7" height="344" width="549" link="/images/Image_07-Admin_Feedback.gif" >}}

En este momento se abre la comunicación entre la persona estudiante y la persona organizadora del curso, ya que las personas estudiantes pueden interactuar en cada uno de los comentarios brindados por las personas organizadoras. En la siguiente imagen se muestra lo antes mencionado:

{{< figure src="/images/Image_08-Student_Response.gif" alt="Imagen 8" width="549" link="/images/Image_08-Student_Response.gif" >}}

## Conclusión

La nueva funcionalidad de revisión de código en _omegaUp_ transforma la manera en que las personas organizadoras de cursos y **asistentes de enseñanza** pueden interactuar con las personas estudiantes. Al permitir una retroalimentación detallada y específica en el código, se mejora significativamente el proceso de aprendizaje y se facilita la comunicación efectiva entre todas las partes involucradas.

Esta herramienta es especialmente valiosa para cursos en línea y para docentes con una gran carga de trabajo, ya que permite delegar la tarea de revisión sin perder el control sobre el contenido del curso.

Invitamos a todas las personas organizadoras de cursos a aprovechar esta nueva funcionalidad y a experimentar de primera mano los beneficios de una retroalimentación más precisa y eficiente. ¡Empieza hoy mismo a mejorar la calidad de tus cursos con la revisión de código en _omegaUp_!
