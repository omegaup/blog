---
title: 'Solución a "Temblor"'
author: 'darknut'
author_email: 'golden.darknut@gmail.com'
date: Fri, 24 Jul 2015 07:07:00 +0000
draft: false
tags: ['Solution', 'bitmask', 'bits', 'búsqueda', 'felix', 'máscara de bits', 'Material de estudio', 'preselectivo', 'soluciones']
---

Problema: [Temblor](https://omegaup.com/arena/problem/temblor)

Primero que nada, tratemos de entender qué es lo que se nos pide, pues es un problema poco tradicional: Dado un mapa de a lo más 4x4, hay que dar una serie de instrucciones que, sin importar en donde te encuentres en el mapa, logre llevarte a una salida; esta secuencia además, debe de ser la más pequeña posible.

Este es el caso de ejemplo:

![mapa](http://2.bp.blogspot.com/-_cxWM1TGYS4/T32p22oRTxI/AAAAAAAACVg/xtv0PTznyo8/s1600/mapa.png)

La solución correcta es ONNEE, pues con esas instrucciones, podemos salir no importando en que lugar estemos (el lugar inicial está marcado con un punto rojo):

![](http://i.imgur.com/QD8Rlaz.png)

*   En el caso 1, las instrucciones ONN no hacen nada pues hay paredes, y las instrucciones EE nos sacan del mapa.
*   En el caso 2, ONN no hacen nada de nuevo y la primera E nos saca del mapa (la última E ya no importa).
*   En el caso 3, O no hace nada, pues hay pared, N nos sube un lugar, la segunda N no hace nada, y EE nos saca del mapa.
*   El caso 4, O nos lleva a la izquierda, donde se vuelve el mismo caso que el caso 3.
*   En el caso 5, O no hace nada, y NN nos lleva al caso 1.
*   Y finalmente, en el caso 6, O nos lleva al caso 5 y de ahí podemos salir.

Es mucho más fácil ver la solución si vemos a todos los olímpicos moverse al mismo tiempo:

![](http://i.imgur.com/UWonMkj.png) Esto ejemplifica dos cosas: en primer lugar, el camino no debe de ser óptimo para cada uno, sino para todos en general, por ejemplo, el punto que inicia en la esquina superior derecha (cerca de la salida), podría salir yendo hacia la derecha, y saliendo en un único movimiento, pero si lo primero que hacemos es un "este", estaremos complicando más las cosas para el resto de los olímpicos atrapados. En segundo lugar, puede haber más de un olímpico en un mismo lugar, y una vez que hay dos olímpicos en un mismo lugar, no importa realmente cuántos hay, sino que hay al menos 1 olímpico en ese lugar:

![](http://i.imgur.com/fNMNkXW.png)

O bien, si lo vemos como unos y ceros:

![](http://i.imgur.com/mE1ISfk.png)

Donde 1 significa hay al menos un olímpico ahí y 0 significa no hay ningún olímpico ahí.

Por lo tanto podemos concluir que nuestra tarea es convertir un tablero lleno de 1's en un tablero lleno de 0's.

A estas alturas, ya tenemos lo suficiente como para hacer una búsqueda en amplitud sobre el problema. Los estados de nuestro espacio de búsqueda están representados por un mapa de NxM lleno de 1's y 0's y las transiciones entre un estado y otro son las operaciones Norte, Sur, Este y Oeste.

Nuestro árbol de búsqueda empezaría más o menos así:

![](http://i.imgur.com/PE9EBdZ.png)

Solo tendríamos que hacer una búsqueda en amplitud hasta llegar al mapa con puros ceros y reconstruir la solución para resolver el problema.

Sin embargo, representar un mapa entero como un estado puede ser algo problemático, pues podemos tener hasta 16 casillas. Como puede haber un total de 2^16 estados, eso quiere decir que tendremos un arreglo de 17 dimensiones y estaremos usando 2^32 casillas de enteros, lo cual es completamente absurdo, pues aunque nos cupiera en memoria, dudo mucho que un compilador soporte tantas dimensiones y mucho menos que vaya a ser fácil manipularlas.

Lo que nos tenemos que dar cuenta es que como nuestro estado son únicamente 1's y 0's podemos olvidarnos de la representación del arreglo, pues podemos convertir cada estado en un número binario. Por ejemplo, a continuación presentamos diferentes mapas y su representación binaria: ![](http://i.imgur.com/MY4v6m4.png) Esto simplifica muchísimo nuestro espacio de búsqueda, ya que en vez de necesitar dieciséis enteros para representar un estado, ahora solo necesitamos 1, donde cada bit del estado representa una casilla del mapa.

La pregunta que nos tenemos que hacer ahora es si es posible representar todos los estados con nuestra representación numérica, y la respuesta es que sí, pues solo son hasta 16 casillas en el mapa, o lo que es igual a 16 bits, y sabemos que un entero en la mayoría de los lenguajes modernos soporta hasta 32 bits, por lo tanto nos alcanza y nos sobra para representar todos los enteros.

La siguiente pregunta que nos tenemos que hacer es si nos va a alcanzar la memoria. Y la respuesta también es sí, pues tenemos hasta 2^16 estados, lo cual es alrededor de 65,000 casillas, cada una de ellas puede guardar ya sea la operación que se hizo para llegar a ella, o el estado del que se llegó, ¡o incluso se pueden guardar ambas cosas! Pues solo necesitamos 16 bits para representar el estado de donde vienes y otros 2 para representar la operación que hiciste. Pero la implementación del problema ya se la dejamos a los competidores. En todo caso, necesitamos únicamente 65,000 enteros lo cual cabe en menos de 300 KB.

De esta forma, nuestro árbol de búsqueda se transforma, y se vuelve más fácil de manipular:

![](http://i.imgur.com/UzvlkDg.png) Una vez hecha la conversión con bits, esto se vuelve una búsqueda en amplitud común y corriente desde un número con NxM bits prendidos, hasta 0. Una búsqueda así debe de ser fácil de hacer para cualquier competidor.