---
title: 'Solución a "Engranes"'
author: 'Lira'
author_email: 'elira@elira.me'
date: Sat, 13 Oct 2012 04:06:46 +0000
draft: false
tags: ['Solution', 'Etapa 1', 'Examen 1', 'Khayyam', 'Soluciones Preselectivo 2013']
math: true
aliases: ['/engranes-khayyam-solucion-enrique-lira']
---

**Concurso:** [Preselectivo para la IOI 2013, Etapa 1, Examen 1](https://omegaup.com/arena/IOI2013E1P1)**[ ](https://omegaup.com/arena/IOI2013E1P1) Autor: **[Omar Ocegueda (Khayyam)](http://www.linkedin.com/pub/jesus-omar-ocegueda-gonzalez/18/b45/5b9) **Solución por: **[Enrique Lira](http://elira.me/)

Para poder resolver este problema hay que ver ciertas propiedades a las cuales podemos llegar fácilmente a partir de ejemplos. Una primera duda que nos surge es: ¿Vuelve al estado inicial?, si hacemos un par de ejemplos podemos ver que si, otra duda que nos surge es: ¿Cuándo vuelve al estado inicial?, y aquí comienza lo complicado. Para saber cuando vuelve a su estado inicial hay que notar ciertas cosas, una de ellas es que en cuanto el diente 1 vuelve a tocar al valle 1 hemos vuelto al estado inicial, no hay forma de que el diente 0 toque al valle 0 sin haber vuelto al estado inicial, entonces hay que buscar ese instante.

Consideremos ra y rb como el número de vueltas que ha dado el engrane a y el engrane b respectivamente en un momento dado después de x pasos, hay que notar que si ra y rb son enteros significa que hemos vuelto al estado inicial o estamos en el estado inicial (ra igual a cero y rb igual a cero).

Para que tanto ra y rb sean enteros, es necesario que x sea divisible tanto por N como por M y hay que encontrar el numero más pequeño distinto de cero (cero es el momento inicial) en el que esto pasa. Para nuestra fortuna esto es fácilmente calculable y es algo que nos enseñan en la escuela, se llama mínimo común múltiplo.

$latex mcm(N,M) = \\frac{N \* M}{MCD(N, M)}&s=2$

Ya que sabemos después de cuantos pasos se repite (llamémoslos K), debemos notar que en esos K pasos ningún par (diente, valle) se va a repetir, dado que si se repite significaría que K no es el primer momento en el que se vuelve al estado inicial.

Sabiendo esto podemos saber cuantos dientes distintos pasan por cada valle, siendo K la cantidad de parejas (diente, valle) distintas que existen (no sé pueden generar más), se puede deducir que K / M es la cantidad de dientes distintos que pasan por cada valle, simplificando nos queda:

$latex \\frac{N}{MCD(N, M)}&s=2$

Ahora hay que buscar una forma de saber el primer diente que pasa por un valle x, con un poco de observación podemos saber que el numero del primer diente en tocar al valle x esta dado por el residuo de la división x sobre N ( x mod N ).

Ya que sabemos cual es el primer diente en tocar al valle x, debemos buscar la forma de calcular los otros dientes, con algunos ejemplos podemos notar que el numero del siguiente diente es M mod N veces mayor que el actual.

En el peor de los casos, los N dientes pasan por todos los valles, resultando nuestra solución actual con una complejidad de $latex O(LN)$ y funciona bastante bien para los 80 puntos del problema.

Para llegar a la solución de 100 puntos hay que notar que después de que un diente y se junta en un valle x, el siguiente diente en juntarse con el valle x no depende del valle sino solo del diente, es por esto que si el diente y pasa por un conjunto de valles y uno de ellos no es estable, ninguno de los otros lo será y viceversa si el diente y pasa por un valle x que es estable, todos los demás valles por los que pase serán estables. Sabiendo esto podemos guardarlo en un arreglo que nos diga por cada diente si pasa por valles estables o no, reduciendo la complejidad a $latex O(N)$.

{{< gist OlimpiadaMexicanadeInformatica 6559014 >}}