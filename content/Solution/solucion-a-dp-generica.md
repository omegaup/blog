---
title: 'Solución a "DP Genérica"'
author: 'Freddy'
author_email: 'me@freddy.mx'
date: Wed, 25 Sep 2013 06:00:06 +0000
draft: false
tags: ['Solution', 'Etapa 1', 'Examen 13', 'Freddy', 'preselectivo', 'solución', 'Soluciones Preselectivo 2014']
---

**Concurso:** [Preselectivo para la IOI 2014, Etapa 1, Problemset 13](https://omegaup.com/arena/IOI2014E1P13#problems/DP-Generica) **Autor:** [Freddy Román Cepeda](http://freddy.mx/) **Fuente**: Project Euler

Podemos tratar este problema de varias maneras distintas, 3 de las cuales discutiré en esta solución.

Análisis 1
----------

Primero, una idea que hubiera obtenido 50 puntos.

Podemos observar que el problema es equivalente a encontrar de cuántas maneras se le puede asignar un número $latex n\_i$ del conjunto $latex \\{0,1,2\\}$ a cada potencia de 2 tal que $latex \\sum\_{i=0}^{\\infty} n\_i 2^i = x$. Esto también es equivalente a encontrar cuántos números $latex a$ y $latex b$ hay tales que $latex a + b = x$ y no haya ningún bit encendido en $latex b$ que no esté encendido en $latex a$.

Consideremos la expansión binaria de $latex a = \\sum\_{i=0}^{\\infty} a\_i 2^i$ y $latex b = \\sum\_{i=0}^{\\infty} b\_i 2^i$ , donde cada $latex a\_i$ y $latex b\_i$ es 1 o 0. Al sumar $latex a + b = \\sum\_{i=0}^{\\infty} (a\_i + b\_i) 2^i$ tenemos que $latex 0 \\le n\_i = a\_i + b\_i \\le 2$, como se necesita. Para contar solamente una vez cada configuración distinta de la secuencia $latex n$, añadimos la restricción de que cualquier $latex b\_i$ puede ser 1 sólo si $latex a\_i$ también lo es.

Subtarea 1
==========

Para esta subtarea es suficiente probar todas las $latex a$ y $latex b$ posibles, revisando con un loop para cada bit si la condición sobre $latex b$ se cumple. Este algoritmo corre en tiempo $latex O(N^2 \\log N)$.

Subtarea 2
==========

Para esta subtarea podemos hacer una observación sencilla: a cada $latex a$ sólo le puede corresponder una $latex b$, igual a $latex x - a$, lo que reduce la complejidad en tiempo del algoritmo a $latex O(N \\log N)$.

Subtarea 3
==========

Podemos comprobar si $latex b$ cumple la condición en tiempo constante utilizando operaciones de bits. Si `~a & b` es igual a 0, $latex b$ no tiene ningún bit encendido que $latex a$ no tenga encendido. Ahora tenemos un algoritmo lineal. Desafortunadamente, ya no podemos mejorar nuestra solución fácilmente continuando con esta idea.

El siguiente código implementa esta solución:

{{< gist OlimpiadaMexicanadeInformatica 6702819 >}}

Análisis 2
----------

Podemos hacer programación dinámica de forma _top-down_. En ésta, contamos la cantidad de maneras de escribir $latex x$ como pide el problema incluyendo o no cada una de las potencias distintas.

Consideremos la función $latex f(n,p)$, que cuenta de cuántas maneras podemos escribir $latex n$ utilizando potencias de 2 menores o iguales a $latex p$ no más de 2 veces cada una. Es evidente que la respuesta se encontraría evaluando $latex f(x,63)$.

Sabemos que $latex f(n,p) = 0$ si $latex n$ es negativo o si $latex p$ es negativo. Del mismo modo, $latex f(n,p) = 1$ si $latex n = 0$. De lo contrario, es igual a la suma de $latex f(n,p-1)$, $latex f(n-2^p,p-1)$ y $latex f(n-2^{p+1},p-1)$, que corresponden a poner 0, 1, o 2 veces la potencia $latex 2^p$.

Subtarea 1
==========

Aplicando directamente el análisis anterior, la subtarea 1 queda resuelta.

Subtarea 2
==========

Varios de estos estados se repiten, así que convendría memorizarlos. Utilizando un contenedor como `std::map`, la solución se vuelve lo suficientemente rápida para resolver esta subtarea.

Subtarea 3
==========

Podemos determinar en algunos casos rápidamente si la función se evaluará a 0. Sabemos que $latex \\sum\_{i=0}^{k} 2^i = 2^{k+1} - 1$. Entonces, el número más grande que podemos escribir sólo usando potencias de 2 menores o iguales a $latex p$ a lo más dos veces es $latex 2\\sum\_{i=0}^{p} 2^p = 2 (2^{p+1} - 1) = 2^{p+2} - 2$. Por lo tanto, $latex f(n,p) = 0$ si $latex n > 2^{p+2} - 2$.

Esa optimización por sí misma (sin memorización), resuelve la subtarea 3.

Subtarea 4
==========

Combinando las ideas de las dos subtareas anteriores, el algoritmo es lo suficientemente rápido para resolver todos los casos. Específicamente, la cantidad de estados que no podemos determinar como no viables instantáneamente es proporcional a $latex \\log x$, y cada estado lo podemos evaluar en tiempo $latex O(\\log \\log x)$ por nuestro `std::map`, dándonos una complejidad total de $latex O(\\log x \\log \\log x)$. Esta cota puede quedar más clara después de describir la tercera solución.

El siguiente código implementa esta solución:

{{< gist OlimpiadaMexicanadeInformatica 6702849 >}}

Análisis 3
----------

Esta solución es equivalente a la anterior, pero no precisa de un `std::map`.

Consideremos la función $latex n(k)$, que definimos como el número que obtenemos tomando los bits $latex 0..k$ de $latex x$. En otras palabras, si $latex x = \\sum\_{i=0}^{\\infty} x\_i 2^i$ donde $latex x\_i$ es el $latex i$-ésimo bit de $latex x$, $latex n(k) = \\sum\_{i=0}^k x\_i 2^i$. Ahora, definimos la función $latex g(i,r)$, que cuenta de cuántas maneras se puede escribir el número $latex n(i) + r2^i$, utilizando potencias de 2 menores o iguales a $latex i$ a lo más 2 veces. La respuesta, por lo tanto, se obtendría evaluando $latex g(63,0)$.

Ahora, sabemos que $latex g(i,r) = 1$ si $latex i < 0$ y $latex r = 0$, porque podemos escribir sólo de una manera 0. Recordando que $latex x\_i$ es el $latex i$-ésimo bit de $latex x$, podemos decir que $latex g(i,r)$ cuenta la cantidad de formas que se puede escribir el número $latex (r+x\_i)2^i + n(i-1)$. De ahora en adelante, por conveniencia, $latex t = r + x\_i$.

Usando esto, podemos definir $latex g(i,r)$ recursivamente:

$latex g(i,r) = \\begin{cases} 1 & \\text{si } i < 0 \\text{ y } r = 0 \\\\ \\sum\_{k=0}^{min(t,2)}g(i-1,2(t-k)) & \\text{de lo contrario} \\end{cases}$

En otras palabras, si tenemos que poner $latex t$ veces la potencia $latex i$, podemos elegir ponerla hasta $latex min(t,2)$ veces, y contar las maneras de escribir el resto usando potencias de 2 menores a $latex p$. Pero como dejamos $latex t-k$ veces la potencia $latex i$ sin poner, es igual a poner $latex 2(t-k)$ veces la potencia $latex i-1$.

La siguiente observación es que si $latex t$ es mayor a 3, $latex g(i,r) = 0$ porque $latex 2\\sum\_{k=0}^{i} 2^k < 4 \\times 2^{i}$. Entonces, sólo nos interesan los casos en los que $latex 0 \\le t \\le 3$. En total, sólo hay 4 valores posibles para $latex t$ en los que $latex g(i,r)$ no es 0: 0, 1, 2, y 3. Enumerémoslos:

$latex g(i,r) = \\begin{cases} g(i-1,0) & \\text{si } t = 0 \\\\ g(i-1,2) + g(i-1,0) & \\text{si } t = 1 \\\\ g(i-1,4) + g(i-1,2) + g(i-1,0) & \\text{si } t = 2 \\\\ g(i-1,6) + g(i-1,4) + g(i-1,2) & \\text{si } t = 3 \\end{cases}$

Pero $latex g(i,r) = 0$ si $latex t > 3$, y como $latex t \\ge r$, nos quedamos con:

$latex g(i,r) = \\begin{cases} g(i-1,0) & \\text{si } t = 0 \\\\ g(i-1,2) + g(i-1,0) & \\text{si } t = 1 \\\\ g(i-1,2) + g(i-1,0) & \\text{si } t = 2 \\\\ g(i-1,2) & \\text{si } t = 3 \\end{cases}$

Tomando en cuenta que $latex r$ sólo puede ser 0 o 2, y $latex x\_i$ sólo 0 o 1:

$latex (g(i,0),g(i,2)) = \\begin{cases} (g(i-1,0),g(i-1,2)+g(i-1,0)) & \\text{si } x\_i = 0 \\\\ (g(i-1,2)+g(i-1,0),g(i-1,2)) & \\text{si } x\_i = 1 \\end{cases}$

El siguiente código implementa esta solución, que corre en tiempo $latex O(\\log n)$ y espacio constante:

{{< gist OlimpiadaMexicanadeInformatica 6702863 >}}

Como podemos observar, esta solución considera los mismos estados que la anterior, sólo que aquí evitamos computarlos, mientras que la otra los descarta inmediatamente.

Consideraciones
---------------

Varios competidores no consideraron que $latex x$ no cabe en un entero signado de 64 bits. Si bien la _respuesta_ cabe en uno, en los límites del problema se especifica que $latex x < 2^{64}$.

Análisis adicional:
-------------------

[Diego Roque](https://omegaup.com/profile/DiegoRoque) escribió una solución distinta, la cual detallaré a continuación.

Consideremos la función $latex f(x)$ como la define el problema: la cantidad de maneras de escribir $latex x$ como una suma de potencias no negativas de 2 sin usar cada una más de 2 veces.

Enfoquémonos en la paridad de $latex x$ (es decir, el último bit de $latex x$). Si $latex x$ es impar, necesariamente tenemos que poner una vez la potencia $latex 2^0$, porque las otras dos opciones: ponerla 0 veces o ponerla 2 veces cambiarían la paridad de $latex x$. Por lo tanto, $latex f(x) = f(\\frac{x-1}{2})$ si $latex x$ es impar. En cambio, si es par, podemos elegir poner la potencia $latex 2^0$ 0 o 2 veces, lo que nos deja con $latex f(x) = f(\\frac{x}{2}) + f(\\frac{x}{2}-1)$. Sólo falta definir los casos base: $latex f(0) = f(1) = 1$.

Aquí está su código que implementa esta solución, que corre en tiempo $latex O(\\log^2 x \\log \\log^2 x):$

{{< gist OlimpiadaMexicanadeInformatica 6702891 >}}