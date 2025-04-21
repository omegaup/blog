---
title: 'Solución a "Carretera"'
author: 'Freddy'
author_email: 'me@freddy.mx'
date: Fri, 25 Jul 2014 04:28:19 +0000
draft: false
tags: ['Solution', '2014', 'carretera', 'Etapa 1', 'Examen 1', 'Freddy', 'nieves', 'preselectivo', 'solución', 'Soluciones Preselectivo 2014']
math: true
aliases: ['/solucion-a-carretera']
---

**Concurso:** [Preselectivo para la IOI 2015, Etapa 1, Examen 1](https://omegaup.com/arena/IOI2015E1E1/#problems/carretera) **Autor:** [Freddy Román Cepeda](http://freddy.mx/) **Fuente**: Edgar Augusto Santiago Nieves, [Freddy Román Cepeda](http://freddy.mx/)

Para obtener los puntos de la primer subtarea bastaba notar que las condiciones especificadas significan que hay dos bloques de coches yendo en diferentes sentidos que inicialmente no se intersectan y eventualmente lo harán, por lo que la respuesta simplemente es el máximo de los anchos de estos bloques.

Este código obtiene los primeros 30 puntos:

{{< gist OlimpiadaMexicanadeInformatica 94cddcf809bc5a583540 >}}

Para el resto de los puntos: Sea $latex f(t)$ el ancho necesario para la fotografía en el segundo $latex t$. La observación crucial es que $latex f$ es una función unimodal: es decir, existe un punto $latex t\_0$ tal que $latex f$ es decreciente a la izquierda de $latex t\_0$ y es creciente a la derecha.

Computar $latex f(t)$ para $latex t$ fijo es trivial: basta con obtener el coche más a la izquierda y más a la derecha en el segundo $latex t$, lo cual toma tiempo $latex O(N)$. Como $latex f$ es unimodal, podemos utilizar búsqueda ternaria o búsqueda binaria para encontrar el mínimo de la función en tiempo $latex O(\\lg T)$, donde $latex T$ es el tamaño del rango a evaluar. Con eso obtenemos un algoritmo con complejidad $latex O(N \\lg T)$, suficiente para obtener todos los puntos del problema.

El siguiente código implementa la solución anterior con búsqueda binaria.

{{< gist OlimpiadaMexicanadeInformatica eee062837acde7bcd8ea >}}