---
title: 'Solución a "Suma Manhattan"'
author: 'Freddy'
author_email: 'me@freddy.mx'
date: Sat, 21 Jun 2014 14:34:14 +0000
draft: false
tags: ['Solution', 'Etapa 1', 'etapa 1', 'Freddy', 'manhattan', 'matemáticas', 'preselectivo', 'Problemset 1', 'problemset 1', 'soluciones', 'Soluciones Preselectivo 2014', 'sumas']
math: true
---

**Concurso:** [Preselectivo para la IOI 2015, Etapa 1, Problemset 1](https://omegaup.com/arena/IOI2015E1P1#problems/Suma-Manhattan) **Autor:** [Freddy Román Cepeda](http://freddy.mx/) **Fuente**: [Freddy Román Cepeda](http://freddy.mx/)

Este problema requería manipular con cuidado la expresión que había que computar. Recordemos que nos piden computar

$latex \\sum\_{0 \\leq i < j < N} manhattan(S\_i,S\_j).$

Para resolver la primer subtarea bastaba con iterar sobre todas las parejas de puntos y calcular su distancia. Esto corre en tiempo cuadrático y no es suficiente para obtener todos los puntos.

La siguiente subtarea era una pista: se puede computar la distancia Manhattan de dos puntos considerando por separado sus coordenadas en $latex x$ y $latex y$. Ahora nos preocuparemos por calcular la siguiente expresión:

$latex \\sum\_{0 \\leq i < j < N} |a\_i - a\_j|.$

Donde $latex a$ son las coordenadas en $latex x$ o $latex y$. El problema está en el valor absoluto. La manera más sencilla de deshacernos de él es ordenar la secuencia $latex a$, de tal manera que $latex a\_i \\leq a\_j$. Entonces tenemos:

$latex \\sum\_{0 \\leq i < j < N} |a\_i - a\_j| = \\sum\_{0 \\leq i < j < N} |a\_j - a\_i| = \\sum\_{0 \\leq i < j < N} a\_j - a\_i.$

La primer igualdad es verdadera porque $latex |x| = |-x|$ para cualquier $latex x$. La segunda es porque como ahora $latex a$ está ordenado, como $latex a\_j \\geq a\_i \\implies a\_j - a\_i \\geq 0$, el valor absoluto no hace nada.

Podemos entonces separar la suma en dos términos:

$latex \\sum\_{0 \\leq i < j < N} a\_j - \\sum\_{0 \\leq i < j < N} a\_i.$

Analicemos el primer término. Estamos sumando sobre todas las $latex j$ tantas veces haya una $latex i$ menor que ella. Eso quiere decir que cada $latex a\_j$ la vamos a sumar $latex j$ veces (nota que $latex a\_0$ la sumamos $latex 0$ veces).

El segundo término nos dice que sumaremos todas las $latex a\_i$ tantas veces haya una $latex j$ mayor a ella. Eso quiere decir que cada $latex a\_i$ la vamos a sumar $latex N-i-1$ veces (nota que $latex a\_{N-1}$ la sumamos $latex 0$ veces).

Juntando esas ideas, entonces tenemos:

$latex \\sum\_{j = 0}^{N-1} j \\cdot a\_j - \\sum\_{i = 0}^{N-1} (N - i - 1) \\cdot a\_i$

$latex = \\sum\_{i = 0}^{N-1} i \\cdot a\_i - \\sum\_{i = 0}^{N-1} (N - i - 1) \\cdot a\_i.$

$latex = \\sum\_{i = 0}^{N-1} (i - (N - i - 1)) \\cdot a\_i.$

$latex = \\sum\_{i = 0}^{N-1} (2i - N + 1) \\cdot a\_i.$

Y con eso terminamos: ahora tenemos una expresión que podemos computar fácilmente en tiempo lineal. Hay que tener cuidado al computar esto: La primera observación es que hay que estar tomando módulo después de cada operación porque en cualquier momento puede haber un _overflow_. Algunos competidores obtuvieron 60 puntos en este problema por no tomar esto en cuenta. La segunda observación es que el término $latex (2i - N + 1) \\cdot a\_i$ no necesariamente cabe en un entero signado de 32 bits -- hacía falta utilizar enteros de 64 bits para realizar este cálculo.

Aquí está mi código que implementa la solución anterior.

{{< gist OlimpiadaMexicanadeInformatica 0614f2d1added587c2fc >}}