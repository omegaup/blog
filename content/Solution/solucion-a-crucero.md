---
title: 'Solución a "Crucero"'
author: 'Freddy'
author_email: 'me@freddy.mx'
date: Thu, 23 Jan 2014 03:41:06 +0000
draft: false
tags: ['Solution', 'Etapa 1', 'Examen 4', 'Germán', 'preselectivo', 'solución', 'Soluciones Preselectivo 2013', 'USACO']
aliases: ['/solucion-a-crucero']
---

**Concurso:** [Preselectivo para la IOI 2014, Etapa 1, Problemset 4](https://omegaup.com/arena/IOI2014E1P4#problems/Crucero) **Autor:** [Saúl Germán Gutiérrez Calderón](mailto:saul.g.gutierrez@gmail.com) **Fuente**: USACO Enero 2009 Gold

Como se puede notar, al trazar la ruta óptima del crucero se está desperdiciando mucho espacio, y daría lo mismo si expandiésemos la isla para que no se desperdiciara espacio entre la ruta y la orilla de ésta.

[![](/images/image002.jpg "image002")](/images/image002.jpg) [![](/images/image004.jpg "image004")](/images/image004.jpg)

Si supiéramos cual es la ruta óptima del crucero para expandir la isla bastaría con hacer un Flood Fill para rellenar los espacios con agua que quedan dentro de la ruta.

Resulta que el flood fill e puede hacer aun sin conocer cuál sería la ruta óptima. Si nos ponemos a hacer todos los tipos de celdas adyacentes a la celda actual en un flood fill, nos toparemos con que solo hay 2 que permiten que la isla crezca y 1 que evita que se expanda. El resto de las celdas adyacentes no nos dice nada acerca de si tenemos que poner algo ahí o no (de momento).

Si se pone un pedazo de isla nuevo en el centro de las figura de abajo, entonces la cosa peligrosa tendría que ser rodeada de alguna manera para poder pasar, lo cual nos llevaría a tomar una ruta mas larga. Por ello, no es una buena idea poner un pedazo de isla ahí.

[![](/images/image005.png "image005")](/images/image005.png)

Si es como la de la figura de abajo,

[![](/images/image006.png "image006")](/images/image006.png)

ambos caminos tienen la misma longitud. Por ello, se puede poner un pedazo de isla ahí y esto nos simplifica el problema.

[![](/images/image007.png "image007")](/images/image007.png)[![](/images/image008.png "image008")](/images/image008.png)

La ruta óptima no puede pasar por el cuadro del centro ya que esto sería un desperdicio de tiempo, por lo cual podemos expandir la tierra ahí.

[![](/images/image009.png "image009")](/images/image009.png)

Entonces, sólo hay que hacer todas las expansiones de tierra hasta que ya no se pueda más y después de esto se puede hacer una mano derecha para buscar la orilla de la isla que al mismo tiempo será la ruta óptima.

{{< gist OlimpiadaMexicanadeInformatica 8572582 >}}