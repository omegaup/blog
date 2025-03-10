---
title: 'Solución a "Los Callejones de Guanajuato"'
author: 'darknut'
author_email: 'golden.darknut@gmail.com'
date: Thu, 02 Mar 2017 06:29:09 +0000
draft: false
tags: ['Solution', 'felix', 'grafos', 'Material de estudio', 'preselectivo', 'solución']
aliases: ['/solucion-a-los-callejones-de-guanajuato']
---

Problema: [Los Callejones de Guanajuato](https://omegaup.com/arena/problem/callejones/).

En este problema se nos está pidiendo que, dado [un grafo conexo no dirigido](https://es.wikipedia.org/wiki/Grafo_conexo), encontrar un [camino](https://es.wikipedia.org/wiki/Camino_(teor%C3%ADa_de_grafos)) tal que pasemos por todas las aristas.

Esta es una aplicación directa de un problema conocido de grafos, aunque no es tan común como otros problemas, estoy hablando de los [ciclos Eulerianos](https://es.wikipedia.org/wiki/Ciclo_euleriano).

<!--more-->

La teoría nos dice que un grafo tendrá un camino euleriano si y sólo sí el [grado](https://es.wikipedia.org/wiki/Grado_(teor%C3%ADa_de_grafos)) de todos sus nodos menos dos es par; es decir, solo dos de sus nodos tienen un número impar de aristas saliendo de él, mientras que todos los demás tienen un número par de aristas.

Esto es fácil de imaginar si nos ponemos a pensar que todo camino que entre a un nodo por una arista debe de tener otra arista por donde salir, a excepción claro del nodo inicial y el nodo final, que sólamente interactúan con el camino una vez.

Es posible visitar un nodo más de una vez, pero por cada vez que entremos, tenemos que salir una vez, manteniendo su grado par. También es posible visitar el nodo inicio y fin más de una vez, pero por cada vez extra que entremos a estos nodos, tendremos que salir, manteniendo su grado impar.

![](http://i.imgur.com/cKkd6nh.png)

También es posible crear un ciclo euleriano (que a diferencia de un camino, empieza y termina en el mismo nodo) si todos los nodos del grafo tienen grado par.

De nuevo imaginemos un poco: en un grafo con un ciclo de euler podemos agregar una arista más entre nodo inicio y fin; ahora todos los nodos tienen grado par, y el camino de euler se volvió un ciclo.

En ningún otro caso se puede formar un camino o ciclo de eurler. En los grafos siguientes, se puede apreciar que cada uno tiene más de dos nodos con un grado impar y por lo tanto, no habrá ningún camino o ciclo de euler, no importa cuanto lo intentes.

![](http://i.imgur.com/o7OKuIc.jpg)

Lo primero que viene a mente luego de leer esta teroría es que aunque es trivial saber si existe o no camino, ¿cómo lo vamos a encontrar si un grafo tiene ciclos? ¿cómo saber qué arista tomar para que al llegar al nodo final, hayamos pasado por todos?

Veremos que este algoritmo es también muy fácil.

Imaginemos el siguiente grafo, en forma de casita, que es muy popular para este problema, tan popular, que hasta en las primarias se ve (aunque claro, a esa edad no se nos decía lo que estábamos haciendo).

![](http://i.imgur.com/0VQqGVK.png)

Lo primero que hay que hacer es, usando un algoritmo de [búsqueda en profundidad](https://es.wikipedia.org/wiki/B%C3%BAsqueda_en_profundidad), encontramos un camino, el que sea, entre los nodos inicio y fin, se pueden repetir nodos, pero no aristas.

![](http://i.imgur.com/b8wtLgL.png)

Ahora, si todos las aristas ya fueron visitadas, entonces ya terminamos, pero si no es así (lo cual es lo más probable), hay que buscar un nodo cualquiera, dentro del camino.

Siempre que haya un nodo sin visitar, este va a tener al menos dos aristas disponibles (pues ya se explicó que siempre tendrán grado par), por lo tanto, ahora hay que hacer una segunda búsqueda, esta vez empezando desde el nodo con aristas disponibles, sin pasar por una arista que ya hemos visitado.

![](http://i.imgur.com/C8l96lD.png)

Si el grafo tiene un camino de Euler, eventualmente vamos a regresar al nodo del que partimos. Siempre. Esto es verdad debido a que, como no nos quedan aristas con grado impar, una de las aristas en ese nodo debe de formar un ciclo con otra de las aristas que salen de ese nodo. Si no hubiera ciclo sería porque el camino termina abruptamente en un nodo, lo cual sería imposible porque esto significaría que ese nodo al final tendría grado impar, y ya usamos nuestros dos nodos impar.

![](http://i.imgur.com/r9rDfW3.png)

Si seguimos este algoritmo para todos los nodos que aún tengan aristas sin visitar, eventualmente visitaremos todas, lo único que hay que hacer ahora es tomar las aristas en el orden correcto para hacer las llamadas a la función.

En el caso en que todos los nodos tengan grado par, se sigue exactamente el mismo algoritmo, con la diferencia de que el nodo inicio y el nodo fin son el mismo.

Como nota cultural, existe un problema similar, el cual en vez de visitar todos las aristas, te pide visitar todos los nodos. Este problema se llama [Camino Hamiltoniano](https://es.wikipedia.org/wiki/Camino_hamiltoniano), y a diferencia de el camino de euler, este problema es [NP completo](https://es.wikipedia.org/wiki/NP-completo),  lo cual significa que no existe una solución que resuelva el problema en tiempo polinomial.