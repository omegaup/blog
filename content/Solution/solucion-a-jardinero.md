---
title: 'Solución a "Jardinero"'
author: 'Freddy'
author_email: 'me@freddy.mx'
date: Thu, 14 Aug 2014 16:16:10 +0000
draft: false
tags: ['Solution', 'Uncategorized']
aliases: ['/solucion-a-jardinero']
---

**Concurso:** [Preselectivo para la IOI 2015, Etapa 1, Problemset 6](https://omegaup.com/arena/IOI2015E1P6#problems/Jardinero) **Autor:** [Saúl Germán Gutiérrez Calderón](mailto:saul.g.gutierrez@gmail.com) **Fuente**: [Saúl Germán Gutiérrez Calderón](mailto:saul.g.gutierrez@gmail.com) (recopilado de los ACM-ICPC World Finals 2010, problema I)

En este problema, una búsqueda exhaustiva con podas bastaba para que corriera en tiempo.

La búsqueda podía tener como estado al renglón y a la columna en la que se estaban, más las casillas por las que ya se había pasado más el numero de la siguiente casilla a esconderse que se necesitaba.

Las podas que se utilizaron en la solución oficial fueron las siguientes (otras podas podrían también conseguir 100 puntos):

1.  Que pasara el tiempo en el que se debería llegar a un escondite.
2.  Que se pasara por un escondite cuando no se debía.
3.  Que no fuera capaz de llegar al siguiente escondite a tiempo.
4.  Que el camino que se llevaba volviera imposible una ruta válida. Si la ruta dejaba a algunas posiciones "encerradas" o dividía al mundo en dos, entonces la ruta actual no llevaba a ningún recorrido valido. Esto se podía checar haciendo una búsqueda en profundidad o en amplitud desde alguna posición no visitada (la posición (0,1) es bastante conveniente porque siempre estará libre).

Aquí está el código de la solución:

{{< gist OlimpiadaMexicanadeInformatica 001edd04da7388cfaf7a >}}