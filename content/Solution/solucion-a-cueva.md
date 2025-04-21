---
title: 'Solución a "Cueva"'
author: 'Lira'
author_email: 'elira@elira.me'
date: Mon, 14 Jan 2013 16:27:54 +0000
draft: false
tags: ['Solution', 'Etapa 1', 'Ethan Jiménez', 'Examen 4', 'preselectivo', 'solución', 'Soluciones Preselectivo 2013']
aliases: ['/solucion-a-cueva']
---

**Concurso:** [Preselectivo para la IOI 2013, Etapa 1, Examen 4](https://omegaup.com/arena/IOI2013E1P4) **Autor:** [Ethan Jiménez Vargas](http://twitter.com/erosethan)

Después de comprender el problema podemos deducir dos cosas:

*   Los **N** puntos de la cueva modelan un árbol, esto debido a la propiedad de que existirán **N-1** aristas y siempre hay un camino entre cualquier par de nodos.
*   Podemos traducir la tarea principal del problema a lo siguiente “Para cada una de las **Q** preguntas, ¿el nodo A es un ancestro del nodo **B**?”, de modo que necesitamos encontrar una manera óptima de saberlo.

_**Subtarea 1**_. Para obtener los primeros 25 puntos del problema solo necesitamos implementar el método de fuerza bruta que nos permita conocer si **A** es ancestro de **B**, esto puede conseguirse con una búsqueda en profundidad (DFS) que desde el nodo **A** encuentre la manera de llegar al nodo 1, restringiendo que no sea posible pasar por el nodo **B**, si existe un camino del nodo **A** al nodo raíz la respuesta es 1, en caso contrario la respuesta es 0. Hay que cuidar los casos especiales cuando el nodo B es el nodo raíz o cuando el nodo **A** es el mismo nodo **B**, en ambos casos la respuesta es 0.

_Complejidad de la solución: **O(NQ)**_

**_Subtarea 2._** Es notable que esta vez el número de preguntas es mucho mayor, por ello la solución anterior tardaría demasiado. Cambiemos nuestra estrategia, esta vez realicemos una búsqueda en profundidad desde el nodo 1 hasta los demás **N** nodos, llevando una lista **L** de los nodos que forman parte del camino desde el nodo 1 hasta el nodo **K**, incluyendo los nodos 1 y **K**, esto puede lograrse mediante recursividad.

La tabla **ancestro\[K\]\[M\]** nos permitirá saber si el nodo **M** es un ancestro del nodo **K**, dándonos cuenta que todos los ancestros de **K** se encuentran en la lista **L** cuando la búsqueda en profundidad llega al nodo **K**, podemos llenar la tabla **ancestro\[K\]\[M\]** durante la búsqueda en profundidad. Con la tabla anterior es fácil responder las preguntas, pues la respuesta depende de **ancestro\[B\]\[A\]**.

_Complejidad de la solución: **O(N2+Q)**_

_**Subtarea 3**_. Para obtener los puntos de esta subtarea podemos utilizar cualquier algoritmo para resolver el clásico problema del ancestro común de dos nodos en un árbol, puesto que la respuesta es 1 si el ancestro común entre los nodos **A** y **B** es el nodo **A**. Este problema ya ha sido estudiado ampliamente y tiene diversas formas de ser resuelto con complejidad **O(NlogN)**, en el foro de tutoriales de TopCoder podemos encontrar un buen artículo con algunos de los algoritmos que pueden ser utilizados:

[TopCoder Lowest Common Ancestor](http://community.topcoder.com/tc?module=Static&d1=tutorials&d2=lowestCommonAncestor)

El algoritmo que utiliza programación dinámica es el más recomendado, puesto que se puede responder a las **Q** preguntas en un tiempo constante.

_Complejidad de la solución: **O(NlogN+Q)**_

_**Subtarea 4**_. Para empezar, notemos que la solución anterior no funciona para este conjunto de puntos porque utiliza demasiada memoria, el simple hecho de almacenar los nodos y las aristas ocupa bastante espacio en memoria (aproximadamente 100Mb) y una solución para la subtarea 3 requeriría al menos 50Mb más, por lo tanto no es posible completar la subtarea 4 con una solución como la anterior, para obtener los 100 puntos en este problema necesitamos una idea mucho más creativa.

Renombremos todos los nodos del árbol enumerandolos del 1 al **N** siguiendo el orden establecido por el recorrido en postorden del árbol comenzando por el nodo 1, después, para cada nodo, con su respectivo número **Y**, hay que obtener el menor número presente en el subárbol con raíz en el nodo **Y**, denotemos este número menor como **X**, con los números **X** y **Y** definimos entonces un intervalo cerrado **\[X,Y\]** que nos representa que en el subárbol con raíz en el nodo **Y** se contienen todos los nodos cuyo número se encuentra en el intervalo **\[X,Y\]**. Podemos interpretar esta información de una manera más conveniente, un nodo con número **Y** es ancestro de un nodo con número **K** si **X ≤ K ≤ Y**, lo cual nos permitirá responder las preguntas planteadas.

Es recomendable que el olímpico experimente y se convenza que la propiedad del intervalo **\[X,Y\]** es siempre correcta debido a que el recorrido en postorden establecerá que el nodo con el número **X**, que establece la cota inferior del intervalo, siempre será una hoja del subárbol y el nodo con valor **Y**, que establece la cota superior del intervalo, siempre será la raíz del subárbol, cualquier otro valor fuera del intervalo estará excluido del subárbol con raíz en el nodo **Y**.

_Complejidad de la solución: **O(N+Q)**_