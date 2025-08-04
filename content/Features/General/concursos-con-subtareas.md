---
title: 'Concursos con Subtareas'
type: docs
sidebar:
  open: true
author: 'Juan Pablo Gómez'
author_email: 'juan.pablo@omegaup.com'
date: Thu, 15 Aug 2023 23:25:06 +0000
draft: false
tags: ['Features', 'Concursos', 'Anuncios', 'omegaUp']
aliases: ['/concursos-con-subtareas','/features/concursos-con-subtareas']
---

Nos es grato informar que hemos liberado una nueva modalidad de concursos llamada **“Concursos con subtareas”**, para poder cubrir satisfactoriamente las necesidades de los concursos realizados en la **Olimpiada Internacional de Informática** (**IOI** por su siglas en inglés), el cual ha modificado la fórmula para calcular el puntaje asignado a un concursante para un problema en específico.

Antecedentes
======================

Anteriormente en _omegaUp_ sólo se contaba con dos distintos tipos de concursos:

- _Calificación parcial_: En este modo de concursos se tomaba en cuenta el mayor puntaje de la suma de todos los grupos de casos. El modo era utilizado para los concursos de la OMI, entre otros.

- _Calificación todo o nada_: En este modo de concursos el participante tenía que obtener el 100% de los casos correctos para que se contaran en su puntaje, de otra forma el marcador para dicho problema sería 0 sin importar si tenía respuestas parcialmente correctas. Para los concursos del ICPC era para los que se utilizaba este modo de concursos.

Con este nuevo modo de concursos podremos cubrir una mayor parte de concursos desde la plataforma de _omegaUp_, lo cual puede ayudar a escuelas, organizaciones a realizar estos concursos con la seguridad de que se pueden calcular los puntajes correctamente.

Definición del nuevo método de evaluación
======================

Al dar de alta un problema, este ya cuenta con una división de subtareas (o grupos de casos) y a cada subtarea se le asigna un porcentaje de puntaje, de tal forma que la suma de todas las subtareas nos da un 100%.

La definición de este nuevo método de evaluación es la siguiente:

> “El puntaje final para cada subtarea será el máximo puntaje de esta subtarea a lo largo de todos los envíos. El puntaje para cada tarea será la suma de los puntajes para sus subtareas. (Por ejemplo, considere a un concursante que hizo 2 envíos en una tarea que contiene 2 subtareas. En la primera solución enviada obtuvo 30 puntos para la primera subtarea y 10 puntos para la segunda subtarea, en la segunda solución obtuvo 0 puntos para la primera subtarea y 40 puntos para la segunda subtarea. Entonces el puntaje final para esta tarea será 70)”

Para representar gráficamente el ejemplo anterior, véase la la siguiente imagen:

{{< figure src="/images/Contest-With-Subtasks-Image-1.png" alt="Image 1" title="Image 1" height="649" width="1472" link="/images/Contest-With-Subtasks-Image-1.png" caption="Image 1" >}}

Para el método de concursos parcial, el puntaje del problema sería 40, debido a que es el mayor puntaje por envío obtenido.

Tomando en cuenta el nuevo método, donde se tienen que sumar los puntajes mayores por cada subtarea, el puntaje total sería 70, debido a que para la subtarea (caso)  1 se obtendría 30 y para la subtarea (caso) 2 se obtendría 40.  

¿Cómo crear un concurso con la modalidad de subtareas?
======================

La forma de crear un concurso con la modalidad de subtareas se realiza de la misma forma que ya se crean los concursos al día de hoy. Sólo existe un campo nuevo en el formulario llamado _“Modo de puntaje”_ donde se tiene que elegir la opción de _“Máximo por grupo”_:

{{< figure src="/images/Contest-With-Subtasks-Image-2.png" alt="Image 2" title="Image 2" height="572" width="936" link="/images/Contest-With-Subtasks-Image-2.png" caption="Image 2" >}}

En la vista de Arena, no hay cambios de interfaz considerables. Los elementos continúan siendo los mismos. En el caso de la lista de envíos seguirá mostrando los mismos veredictos.

Lo único que cambia es el modo en el que se calcula el ranking, tanto en la tabla de mini-ranking:

{{< figure src="/images/Contest-With-Subtasks-Image-3.png" alt="Image 3" title="Image 3" height="398" width="344" link="/images/Contest-With-Subtasks-Image-3.png" caption="Image 3" >}}

Como en el scoreboard:

{{< figure src="/images/Contest-With-Subtasks-Image-4.png" alt="Image 4" title="Image 4" height="509" width="854" link="/images/Contest-With-Subtasks-Image-4.png" caption="Image 4" >}}

Y en el navegador de problemas:

{{< figure src="/images/Contest-With-Subtasks-Image-5.png" alt="Image 5" title="Image 5" height="509" width="278" link="/images/Contest-With-Subtasks-Image-5.png" caption="Image 5" >}}

Atentamente, el equipo de omegaUp.
