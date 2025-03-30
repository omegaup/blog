---
title: 'Solución a "DP Genérica"'
author: 'Freddy'
author_email: 'me@freddy.mx'
date: Wed, 25 Sep 2013 06:00:06 +0000
draft: false
tags: ['Solution', 'Etapa 1', 'Examen 13', 'Freddy', 'preselectivo', 'solución', 'Soluciones Preselectivo 2014']
math: true
---

**Concurso:** [Preselectivo para la IOI 2014, Etapa 1, Problemset 13](https://omegaup.com/arena/IOI2014E1P13#problems/DP-Generica) **Autor:** [Freddy Román Cepeda](http://freddy.mx/) **Fuente**: Project Euler

Podemos tratar este problema de varias maneras distintas, 3 de las cuales discutiré en esta solución.

Análisis 1
----------

Primero, una idea que hubiera obtenido 50 puntos.

Podemos observar que el problema es equivalente a encontrar de cuántas maneras se le puede asignar un número $ n\_i$ del conjunto $ \\{0,1,2\\}$ a cada potencia de 2 tal que $ \\sum\_{i=0}^{\\infty} n\_i 2^i = x$. Esto también es equivalente a encontrar cuántos números $ a$ y $ b$ hay tales que $ a + b = x$ y no haya ningún bit encendido en $ b$ que no esté encendido en $ a$.

Consideremos la expansión binaria de $ a = \\sum\_{i=0}^{\\infty} a\_i 2^i$ y $ b = \\sum\_{i=0}^{\\infty} b\_i 2^i$ , donde cada $ a\_i$ y $ b\_i$ es 1 o 0. Al sumar $ a + b = \\sum\_{i=0}^{\\infty} (a\_i + b\_i) 2^i$ tenemos que $ 0 \\le n\_i = a\_i + b\_i \\le 2$, como se necesita. Para contar solamente una vez cada configuración distinta de la secuencia $ n$, añadimos la restricción de que cualquier $ b\_i$ puede ser 1 sólo si $ a\_i$ también lo es.

Subtarea 1
==========

Para esta subtarea es suficiente probar todas las $ a$ y $ b$ posibles, revisando con un loop para cada bit si la condición sobre $ b$ se cumple. Este algoritmo corre en tiempo $ O(N^2 \\log N)$.

Subtarea 2
==========

Para esta subtarea podemos hacer una observación sencilla: a cada $ a$ sólo le puede corresponder una $ b$, igual a $ x - a$, lo que reduce la complejidad en tiempo del algoritmo a $ O(N \\log N)$.

Subtarea 3
==========

Podemos comprobar si $ b$ cumple la condición en tiempo constante utilizando operaciones de bits. Si `~a & b` es igual a 0, $ b$ no tiene ningún bit encendido que $ a$ no tenga encendido. Ahora tenemos un algoritmo lineal. Desafortunadamente, ya no podemos mejorar nuestra solución fácilmente continuando con esta idea.

El siguiente código implementa esta solución:

{{< gist OlimpiadaMexicanadeInformatica 6702819 >}}

Análisis 2
----------

Podemos hacer programación dinámica de forma _top-down_. En ésta, contamos la cantidad de maneras de escribir $ x$ como pide el problema incluyendo o no cada una de las potencias distintas.

Consideremos la función $ f(n,p)$, que cuenta de cuántas maneras podemos escribir $ n$ utilizando potencias de 2 menores o iguales a $ p$ no más de 2 veces cada una. Es evidente que la respuesta se encontraría evaluando $ f(x,63)$.

Sabemos que $ f(n,p) = 0$ si $ n$ es negativo o si $ p$ es negativo. Del mismo modo, $ f(n,p) = 1$ si $ n = 0$. De lo contrario, es igual a la suma de $ f(n,p-1)$, $ f(n-2^p,p-1)$ y $ f(n-2^{p+1},p-1)$, que corresponden a poner 0, 1, o 2 veces la potencia $ 2^p$.

Subtarea 1
==========

Aplicando directamente el análisis anterior, la subtarea 1 queda resuelta.

Subtarea 2
==========

Varios de estos estados se repiten, así que convendría memorizarlos. Utilizando un contenedor como `std::map`, la solución se vuelve lo suficientemente rápida para resolver esta subtarea.

Subtarea 3
==========

Podemos determinar en algunos casos rápidamente si la función se evaluará a 0. Sabemos que $ \\sum\_{i=0}^{k} 2^i = 2^{k+1} - 1$. Entonces, el número más grande que podemos escribir sólo usando potencias de 2 menores o iguales a $ p$ a lo más dos veces es $ 2\\sum\_{i=0}^{p} 2^p = 2 (2^{p+1} - 1) = 2^{p+2} - 2$. Por lo tanto, $ f(n,p) = 0$ si $ n > 2^{p+2} - 2$.

Esa optimización por sí misma (sin memorización), resuelve la subtarea 3.

Subtarea 4
==========

Combinando las ideas de las dos subtareas anteriores, el algoritmo es lo suficientemente rápido para resolver todos los casos. Específicamente, la cantidad de estados que no podemos determinar como no viables instantáneamente es proporcional a $ \\log x$, y cada estado lo podemos evaluar en tiempo $ O(\\log \\log x)$ por nuestro `std::map`, dándonos una complejidad total de $ O(\\log x \\log \\log x)$. Esta cota puede quedar más clara después de describir la tercera solución.

El siguiente código implementa esta solución:

{{< gist OlimpiadaMexicanadeInformatica 6702849 >}}

Análisis 3
----------

Esta solución es equivalente a la anterior, pero no precisa de un `std::map`.

Consideremos la función $ n(k)$, que definimos como el número que obtenemos tomando los bits $ 0..k$ de $ x$. En otras palabras, si $ x = \\sum\_{i=0}^{\\infty} x\_i 2^i$ donde $ x\_i$ es el $ i$-ésimo bit de $ x$, $ n(k) = \\sum\_{i=0}^k x\_i 2^i$. Ahora, definimos la función $ g(i,r)$, que cuenta de cuántas maneras se puede escribir el número $ n(i) + r2^i$, utilizando potencias de 2 menores o iguales a $ i$ a lo más 2 veces. La respuesta, por lo tanto, se obtendría evaluando $ g(63,0)$.

Ahora, sabemos que $ g(i,r) = 1$ si $ i < 0$ y $ r = 0$, porque podemos escribir sólo de una manera 0. Recordando que $ x\_i$ es el $ i$-ésimo bit de $ x$, podemos decir que $ g(i,r)$ cuenta la cantidad de formas que se puede escribir el número $ (r+x\_i)2^i + n(i-1)$. De ahora en adelante, por conveniencia, $ t = r + x\_i$.

Usando esto, podemos definir $ g(i,r)$ recursivamente:

$ g(i,r) = \\begin{cases} 1 & \\text{si } i < 0 \\text{ y } r = 0 \\\\ \\sum\_{k=0}^{min(t,2)}g(i-1,2(t-k)) & \\text{de lo contrario} \\end{cases}$

En otras palabras, si tenemos que poner $ t$ veces la potencia $ i$, podemos elegir ponerla hasta $ min(t,2)$ veces, y contar las maneras de escribir el resto usando potencias de 2 menores a $ p$. Pero como dejamos $ t-k$ veces la potencia $ i$ sin poner, es igual a poner $ 2(t-k)$ veces la potencia $ i-1$.

La siguiente observación es que si $ t$ es mayor a 3, $ g(i,r) = 0$ porque $ 2\\sum\_{k=0}^{i} 2^k < 4 \\times 2^{i}$. Entonces, sólo nos interesan los casos en los que $ 0 \\le t \\le 3$. En total, sólo hay 4 valores posibles para $ t$ en los que $ g(i,r)$ no es 0: 0, 1, 2, y 3. Enumerémoslos:

$ g(i,r) = \\begin{cases} g(i-1,0) & \\text{si } t = 0 \\\\ g(i-1,2) + g(i-1,0) & \\text{si } t = 1 \\\\ g(i-1,4) + g(i-1,2) + g(i-1,0) & \\text{si } t = 2 \\\\ g(i-1,6) + g(i-1,4) + g(i-1,2) & \\text{si } t = 3 \\end{cases}$

Pero $ g(i,r) = 0$ si $ t > 3$, y como $ t \\ge r$, nos quedamos con:

$ g(i,r) = \\begin{cases} g(i-1,0) & \\text{si } t = 0 \\\\ g(i-1,2) + g(i-1,0) & \\text{si } t = 1 \\\\ g(i-1,2) + g(i-1,0) & \\text{si } t = 2 \\\\ g(i-1,2) & \\text{si } t = 3 \\end{cases}$

Tomando en cuenta que $ r$ sólo puede ser 0 o 2, y $ x\_i$ sólo 0 o 1:

$ (g(i,0),g(i,2)) = \\begin{cases} (g(i-1,0),g(i-1,2)+g(i-1,0)) & \\text{si } x\_i = 0 \\\\ (g(i-1,2)+g(i-1,0),g(i-1,2)) & \\text{si } x\_i = 1 \\end{cases}$

El siguiente código implementa esta solución, que corre en tiempo $ O(\\log n)$ y espacio constante:

{{< gist OlimpiadaMexicanadeInformatica 6702863 >}}

Como podemos observar, esta solución considera los mismos estados que la anterior, sólo que aquí evitamos computarlos, mientras que la otra los descarta inmediatamente.

Consideraciones
---------------

Varios competidores no consideraron que $ x$ no cabe en un entero signado de 64 bits. Si bien la _respuesta_ cabe en uno, en los límites del problema se especifica que $ x < 2^{64}$.

Análisis adicional:
-------------------

[Diego Roque](https://omegaup.com/profile/DiegoRoque) escribió una solución distinta, la cual detallaré a continuación.

Consideremos la función $ f(x)$ como la define el problema: la cantidad de maneras de escribir $ x$ como una suma de potencias no negativas de 2 sin usar cada una más de 2 veces.

Enfoquémonos en la paridad de $ x$ (es decir, el último bit de $ x$). Si $ x$ es impar, necesariamente tenemos que poner una vez la potencia $ 2^0$, porque las otras dos opciones: ponerla 0 veces o ponerla 2 veces cambiarían la paridad de $ x$. Por lo tanto, $ f(x) = f(\\frac{x-1}{2})$ si $ x$ es impar. En cambio, si es par, podemos elegir poner la potencia $ 2^0$ 0 o 2 veces, lo que nos deja con $ f(x) = f(\\frac{x}{2}) + f(\\frac{x}{2}-1)$. Sólo falta definir los casos base: $ f(0) = f(1) = 1$.

Aquí está su código que implementa esta solución, que corre en tiempo $ O(\\log^2 x \\log \\log^2 x):$

{{< gist OlimpiadaMexicanadeInformatica 6702891 >}}