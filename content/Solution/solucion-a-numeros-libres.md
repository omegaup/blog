---
title: 'Solución a "Números Libres"'
author: 'Freddy'
author_email: 'me@freddy.mx'
date: Sat, 21 Jun 2014 23:24:56 +0000
draft: false
tags: ['Solution', 'Uncategorized']
math: true
---

**Concurso:** [Preselectivo para la IOI 2015, Etapa 1, Problemset 1](https://omegaup.com/arena/IOI2015E1P1#problems/Suma-Manhattan) **Autor:** [Freddy Román Cepeda](http://freddy.mx/) **Fuente**: Edgar Augusto Santiago Nieves

Para resolver este problema hacía falta tener en mente la definición de _square-free_. Como tanto $ a$ y $ b$ no son divisibles por el cuadrado de un primo, la única manera de que su producto deje de ser _square-free_ sería que ambos compartieran un factor primo.

Para obtener todos los puntos de la primer subtarea bastaba con computar $ a \\times b$ e iterar sobre todos los números menores a ese producto y revisar si es divisible por el cuadrado de alguno de ellos.

Para obtener los puntos de la segunda subtarea era suficiente iterar hasta $ \\max(\\sqrt{a}, \\sqrt{b})$, para factorizar a $ a$ y $ b$.

Por último, para obtener el resto de los puntos bastaba notar que si $ a$ y $ b$ comparten un factor primo, entonces su máximo común divisor es distinto de 1.

El siguiente código implementa esta solución:

{{< gist OlimpiadaMexicanadeInformatica a08706770254e741af59 >}}