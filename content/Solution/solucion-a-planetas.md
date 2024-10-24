---
title: 'Solución a "Planetas"'
author: 'Freddy'
author_email: 'me@freddy.mx'
date: Sun, 10 Aug 2014 05:16:54 +0000
draft: false
tags: ['Solution', 'Uncategorized']
---

**Concurso:** [Preselectivo para la IOI 2015, Etapa 1, Problemset 4](https://omegaup.com/arena/IOI2015E1P4#problems/Planetas) **Autor:** [Freddy Román Cepeda](http://freddy.mx/) **Fuente**: Edgar Augusto Santiago Nieves

La observación principal de este problema es que siempre hay $latex N-1$ lugares estables para el meteorito, y que cada uno de éstos se encuentra entre parejas consecutivas de planetas. Primero notemos que ningún lugar estable puede estar más a izquierda que todos los planetas, ya que la fuerza neta sobre éste lo haría moverse a la derecha. Por la misma razón, no pueden haber lugares estables después del último planeta hacia la derecha.

Ahora, para ver que siempre hay un lugar estable entre cualquier pareja consecutiva de planetas hay que analizar la función que describe la fuerza entre el meteorito y el planeta: $latex \\frac{1}{\\left | X\_i - M \\right |}$. Supongamos que el meteorito está entre los planetas $latex i$ e $latex i+1$. Cuando $latex M \\approx X\_i$ la fuerza que atrae al meteorito hacia el planeta $latex i$ es suficientemente grande para forzar al meteorito a moverse a la izquierda sin importar la fuerza de los planetas que se encuentren a la derecha (nota que el denominador se hace muy pequeño). Lo mismo ocurre con el planeta $latex i+1$ cuando el meteorito está muy cerca de él. Pero esto quiere decir que existe un único punto $latex p$ entre los dos planetas en el que la fuerza neta sobre el meteorito es 0. (Este argumento se puede formalizar utilizando cálculo.)

Además, es sencillo observar que el meteorito se movería a la izquierda si estuviera entre el planeta $latex i$ y el punto $latex p$, y a la derecha si estuviera entre el punto $latex p$ y el planeta $latex i+1$. Por lo tanto, podemos hacer una búsqueda binaria para encontrar el punto $latex p$ para cada pareja de planetas consecutivos.

Como hay $latex N-1$ parejas y calcular la fuerza neta sobre el meteorito en algún punto arbitrario toma tiempo $latex O(N)$, la complejidad total de este algoritmo es $latex O(N^2 I)$ donde $latex I$ es la cantidad de iteraciones que realice la búsqueda binaria. También hay que ordenar los planetas, ya que la descripción del problema no asegura que vendrán ordenados. Por lo tanto, la solución final tiene complejidad $latex O(N \\lg N + N^2 I)$.

El siguiente código implementa esta solución:

{{< gist OlimpiadaMexicanadeInformatica 78f6a81284ad83b69702 >}}