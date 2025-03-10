---
title: 'Solución a "Minecraft"'
author: 'Lira'
author_email: 'elira@elira.me'
date: Tue, 08 Jan 2013 17:14:15 +0000
draft: false
tags: ['Solution', 'Enrique Lira', 'Etapa 1', 'Examen 5', 'preselectivo', 'solución', 'Soluciones Preselectivo 2013']
aliases: ['/solucion-a-minecraft']
---

**Concurso:** [Preselectivo para la IOI 2013, Etapa 1, Examen 5](https://omegaup.com/arena/IOI2013E1P5) **Autor: **[Enrique Lira Vargas](mailto:elira@elira.me)

Este problema no requiere ninguna observación específica y realmente lo único que hay que hacer es una búsqueda.

Para los primeros 50 puntos
aliases: ['/solucion-a-minecraft']
---------------------------

Este primer sub set de casos se puede resolver implementando una búsqueda en amplitud que nos dé el camino más corto entre dos puntos en un mapa con paredes.

Para los 75 puntos
aliases: ['/solucion-a-minecraft']
------------------

Para este punto se me ocurrió una solución factible para aquellos que no saben construir una cola de prioridad, correr una búsqueda en amplitud con dos colas cuidando elegir siempre la siguiente posición con una menor cantidad de movimientos de las dos colas.

Para los 100 puntos
aliases: ['/solucion-a-minecraft']
-------------------

Esta solución era para aquellos que supieran hacer una búsqueda utilizando una cola de prioridad. La idea es que al sacar un elemento de la cola siempre nos dé aquel al que se puede llegar con la menor cantidad de movimientos. Este procedimiento es idéntico a una búsqueda en amplitud solo que se utiliza una cola de prioridad. En la solución hago uso de un montículo como cola de prioridad.

{{< gist OlimpiadaMexicanadeInformatica 6559202 >}}