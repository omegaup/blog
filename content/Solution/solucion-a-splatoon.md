---
title: 'Solución a "Splatoon"'
author: 'darknut'
author_email: 'golden.darknut@gmail.com'
date: Mon, 05 Oct 2015 08:20:43 +0000
draft: false
tags: ['Solution', 'busquedas', 'felix', 'Material de estudio', 'preselectivo', 'solución']
aliases: ['/solucion-a-splatoon']
---

Problema: [Splatoon](https://omegaup.com/arena/problem/splatoon/).

Este problema pide llevar a un inkling desde el inicio de una calle hasta el final siguiendo sus reglas de movimiento.

Ignoremos por un momento el hecho de que los inklings pueden pintar el piso y con ello alterar la calle en donde se realiza la carrera. Si los inklings no tuvieran esta habilidad, se puede hacer un algoritmo de fuerza bruta intentando todas las operaciones posibles, es decir, hacer una búsqueda en amplitud para encontrar el camino más corto, en donde el estado está representado únicamente por la posición en donde se encuentre el inkling.

**Recuerda que en las búsquedas es importante marcar visitados para que la complejidad del algoritmo no se vuelva exponencial.**

Para cada posición, se tienen dos posibles operaciones, saltar, o caminar, ambas toman 1 segundo y la distancia a la que se llega depende directamente del color sobre el que se está parado. El movimiento de saltar es muy fácil pues solo hay una casilla donde se puede caer, pero el movimiento de avanzar difiere cada vez pues depende directamente del color de las siguientes casillas.

Es posible hacer un ciclo para ver hasta donde puedes llegar avanzando desde la casilla en donde estás, y agregar a la búsqueda el lugar más lejano a donde puedas llegar. Sin embargo, si únicamente registramos la última casilla a donde se puede llegar, casos como el siguiente se nos escaparán:

![](http://i.imgur.com/t1iBoPQ.png)

En la solución superior, primero se avanza todo lo que se puede en la pintura naranja hasta llegar a la casilla azul, de ahi ya sea saltando o avanzando únicamente se puede llegar a la casilla blanca, y de ahí, no importa lo que hagas, te tomará dos segundos llegar al final.

En cambio, en la solución inferior, se avanza solo 3 casillas en la pintura naranja, lo cual es 1 casilla menos del máximo, de ahí se hace un salto el cual nos deja de nuevo en pintura naranja, desde donde podemos llegar caminando hasta el final en un total de tan solo 3 segundos, 1 segundo menos que la solución anterior.

Por lo tanto, no es suficiente visitar la distancia máxima, también hace falta visitar la distancia máxima - 1. Si intentamos hacer cosas similares con otro color de pintura, o más deteniéndonos todavía más atrás del máximo, no hay realmente ninguna ventaja, por lo que el caso presentado anteriormente es el único caso especial.

Una búsqueda en amplitud bien hecha que considere este caso sacará 30 puntos, una que no considere este caso sacará únicamente 5 puntos. Da perfectamente en tiempo y memoria porque a lo más tendremos un total de 1000 estados. Sin embargo, la parte interesante de este problema es que los inklings son capaces de alterar el estado de la calle usando la pintura que traen en su tanque para poder recorrer más rápido la calle, utilizando hasta D disparos de tinta.

En este caso, necesitamos agregar una segunda dimensión al estado de nuestra búsqueda, ahora no sólamente es suficiente con guardar el lugar en donde estamos, sino que es necesario guardar también cuanta tinta queda en el tanque. En este caso, agregamos una operación más, la cual es pintar, la cual cuesta 0 segundos, nos avanza 0 casillas y nos quita una unidad D de pintura.

Si hacemos esto, nuestro espacio de búsqueda crece del N que era en la solución de 30 puntos, a N x D, lo cual es 1000 x 1000 y aún da en tiempo y memoria.

No obstante, la operación de pintar altera el mapa, por lo que si no guardamos también en el estado que las casillas siguientes ahora son de otro color, pintar no servirá de nada. Podríamos agregar una dimensión más a la búsqueda para considerar este caso, pero esto solo le agregaría complejidad innecesaria a la búsqueda.

La clave está en que pintar toma 0 segundos, por lo que podemos convertir la operación de pintar en una operación compuesta, que sea pintar y avanzar.

Pintar y avanzar toma 1 segundo, y nos permite avanzar 4 casillas hacia adelante **siempre**, por lo que hacer una operación de pintar y avanzar nos lleva del estado _(i, d)_ al estado _(i + 4, d - 1)_ con un costo de 1 segundo.

El detalle con esta solución, es que estamos ignorando de nuevo el caso especial explicado en la solución de 30 puntos, por lo que si se nos olvida que es posible ahorrarnos un segundo en ciertas ocasiones, sacaremos entre 35 y 90 puntos dependiendo de la implementación.

Para sacar los 100 puntos, es necesario agregar una operación más, la cual es pintar, avanzar y saltar, la cual nos lleva del estado _(i, d),_  al estado _(i + 6, d - 1)_ con un costo de 2 segundos. Y como esta operación toma 2 segundos en vez de tan solo 1, no es suficiente con utilizar una cola común y corriente para hacer la búsqueda en amplitud, sino que es necesario utilizar una estructura de datos más avanzada, como una cola de prioridad o un montículo que nos ayude a ordenar los estados y elegir siempre con el tiempo más pequeño.