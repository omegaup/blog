---
title: 'Solución a "La Venganza de Silvio"'
author: 'Lira'
author_email: 'elira@elira.me'
date: Thu, 08 Aug 2013 02:02:51 +0000
draft: false
tags: ['Solution', 'Etapa 1', 'Examen 1', 'Freddy', 'preselectivo', 'Silvio', 'solución', 'Soluciones Preselectivo 2014']
math: true
---

**Concurso:** [Preselectivo para la IOI 2014, Etapa 1, Problemset 1](https://omegaup.com/arena/IOI2014E1P1#problems/VenganzaDeSilvio) **Autor:** [Freddy Román Cepeda](http://freddy.mx/) **Fuente**: Freddy

Este problema es bastante sencillo de entender, la dificultad radica en que exponenciar un número de la manera obvia no es lo suficientemente rápido para obtener todos los puntos disponibles.

Subtarea 1
----------

Para obtener el primer grupo de puntos, sólo basta calcular $ N^M$ multiplicando a $ N$ por sí mismo $ M$ veces, teniendo cuidado de que no haya overflow.

Subtarea 2
----------

Para la segunda subtarea, se necesita algo más rápido, para lo que se puede usar [exponenciación binaria](http://es.wikipedia.org/wiki/Exponenciación_binaria).

Sabemos que $ x^0 = 1$, que $ (x^n)^2 = x^{2n}$, y que $ x \* x^{n-1} = x^n$ para toda $ x$ y $ n$, por lo que podemos escribir la siguiente relación:

$ \\text{potencia}(N,M) = \\begin{cases} 1 & \\text{si } M = 0 \\\\ (potencia(N,M/2))^2 & \\text{si } M \\text{ es par} \\\\ N \* (potencia(N,(M-1)/2))^2 & \\text{de lo contrario} \\end{cases}$

Aplicando esta definición directamente, la segunda subtarea queda resuelta. Esto es porque el algoritmo descrito anteriormente tiene complejidad $ O(log M)$, ya que en cada paso $ M$ se reduce a la mitad.

Subtarea 3
----------

El algoritmo anterior es lo suficientemente rápido para resolver esta subtarea, pero el rango de los enteros de la máquina no es lo suficientemente grande para guardar a $ M$. Para ello requerimos una observación adicional. Dividir entre $ 2$ en base $ 2$ ignorando el residuo es lo mismo que recorrer todos los dígitos una vez a la derecha descartando el bit menos significativo, y, además, se puede saber si un número es par o no con sólo ver el bit menos significativo del mismo.

Podemos aprovechar esta observación guardando $ M$ como una cadena de bits y modficando un poco la función descrita anteriormente. Si $ A$ es el arreglo donde guardamos los bits de $ M$, está $ 0$-indexado, tiene $ k$ bits, y los bits están ordenados del más significativo al menos (como viene en la entrada del problema), la respuesta se encuentra evaluando $ potencia2(N,k-1)$, donde $ potencia2$ es:

$ \\text{potencia2}(N,i) = \\begin{cases} 1 & \\text{si } i < 0 \\\\ (potencia2(N,i-1))^2 & \\text{si } A\[i\] = 0 \\\\ N \* (potencia2(N,i-1))^2 & \\text{de lo contrario} \\end{cases}$

Subtarea 4
----------

El problema con el algoritmo anterior es que ocupa demasiada memoria para los casos que contiene esta subtarea. Para corregirlo, podemos analizar la función anterior.

Por conveniencia, definamos $ f(i)$ como el número que se obtiene tomando los elementos $ \[0..i\]$ del arreglo $ A$, y $ f(-1) = 0$. Recordando que multiplicar por $ 2$ en base $ 2$ es lo mismo que recorrer todos los dígitos a la izquierda, $ f(i) = 2f(i-1) + A\[i\]$.

Ahora, es simple notar que $ potencia2(N,i) = N^{f(i)}$, que podemos reescribir como $ potencia2(N,i) = N^{2f(i-1) + A\[i\]} = (N^{f(i-1)})^2 N^{A\[i\]}$.

Por lo tanto, podemos escribir un ciclo en vez de utilizar recursión.

Este algoritmo ocupa espacio constante, por lo que resuelve la subtarea 4.

Aquí está la implementación del algoritmo anterior:

{{< gist OlimpiadaMexicanadeInformatica 6559240 >}}

Consideraciones
---------------

Hay que tener cuidado de que no haya overflow. Cuando un entero de $ k$ bits se eleva al cuadrado, puede ahora tener a lo más $ 2k$ bits. Como $ m$ puede tener hasta $ 31$ bits, es necesario usar enteros de 64 bits durante todos los cálculos.

También, varios competidores no consideraron el caso en el que se pide calcular $ N^0 \\pmod 1$.