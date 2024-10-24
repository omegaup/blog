---
title: 'Análisis de diferencias en salidas para envíos de problemas educativos'
author: 'Juan Pablo Gómez'
author_email: 'juan.pablo@omegaup.com'
date: Mon, 07 Sep 2020 02:13:18 +0000
draft: false
tags: ['Features', 'Cursos', 'Uncategorized']
---

Hemos liberado una nueva funcionalidad que será muy útil para los usuarios que comienzan a utilizar la plataforma, ya que contarán con una herramienta más para apoyarlos en su aprendizaje. Esta funcionalidad les permitirá ver un análisis de las diferencias entre las salidas que dan sus programas y las salidas oficiales para los envíos de problemas educativos.

### ¿En qué consiste el análisis de las diferencias?

Para todos los problemas educativos que accedan vía cursos, los usuarios podrán comparar el resultado que obtuvo la salida de la solución que acaban de enviar, contra el resultado que se espera de acuerdo a los casos que subió el creador del problema.

### Ventajas

El uso de esta herramienta traerá beneficios, tanto para profesores como para estudiantes, los cuales se describen a continuación:

#### Profesor

*   Tiempo: Al permitir a los estudiantes ser más autodidactas, el profesor tendrá más tiempo para revisar temas de mayor relevancia o donde los estudiantes presentan más problemas. 

#### Alumno

*   Problemas auto didácticos: Al recibir retroalimentación más completa desde la plataforma, el estudiante puede realizar más problemas, los cuales lo irán guiando con las pistas para llegar a la solución de los problemas sin necesidad de contar con la figura del profesor.

### ¿Cómo funciona esta nueva herramienta?

#### Profesor

Lo primero que se debe tomar en cuenta por parte del profesor / creador de problemas es que el problema sea meramente educativo, quiere decir, que este no vaya a ser tomado en cuenta o ya se esté usando en concursos, ya que esto podría dar ventaja a usuarios que ya hayan visto las salidas esperadas. 

Una vez que ya se definió que el problema se utilizará con fines educativos se procede a la configuración. 

Si el problema es nuevo, se sigue el mismo procedimiento como para crear cualquier problema: _Menú > Problemas > Crear un problema_, donde se encontrará el siguiente campo:

[![](/images/01-Configurar-problema-nuevo.png)](/images/01-Configurar-problema-nuevo.png)

Las opciones disponibles son:

*   Ninguno (predeterminado): El problema continúa como siempre ha existido, sin mostrar diferencias de salidas en los casos.
*   Sólo ejemplos: Se mostrarán las diferencias de salidas para todos los casos que se guardaron en el directorio _examples_.
*   Todos: Se mostrarán las diferencias de salidas para todos los casos que se agregaron en el archivo _.zip_, incluidos los ejemplos.

En caso de que el problema ya exista y se desee agregar esta configuración, se debe ingresar a la sección de editar problema de la forma tradicional: _Menú > Usuario > Mis problemas_, y después dar clic en el icono de Editar problema [![](/images/001-Editar-problema.png)](/images/001-Editar-problema.png) . En este formulario también se encontrará disponible la configuración:

[![](/images/02-Configurar-problema-existente.png)](/images/02-Configurar-problema-existente.png)

El siguiente paso es agregar el problema a algún curso; recuerda que esta configuración sólo funciona en ese lugar.

#### Estudiante

Para que los estudiantes puedan aprovechar esta herramienta deben estar inscritos al curso que contenga problemas educativos. 

1.- El primer paso a realizar es ingresar al curso, tal como se hace tradicionalmente, seleccionar la tarea en la que estará trabajando y elegir el problema educativo.

2.- Después se debe enviar una solución y esperar a que el juez de omegaUp evalúe el envío. En el listado de envíos aparece el botón para ver los detalles, dar clic.

3.- En la ventana que aparece se mostrará la información de los casos, con su respectivo puntaje por cada grupo.

4.- Puedes presionar cualquiera de los botones [![](/images/002-Seleccionar-grupo-de-casos.png)](/images/002-Seleccionar-grupo-de-casos.png)  para ver la diferencia en las salidas de los casos, si todos los casos del grupo son los mismos que los esperados o si hay alguna salida que no coincide.

En la siguiente animación se puede ver su funcionamiento tal como le aparecerá al estudiante en el curso:

[{{< video autoplay="true" loop="true" muted="true" src="/images/ShowOutputDiffs_.webm" type="video/mp4" >}}](/images/ShowOutputDiffs_.webm)