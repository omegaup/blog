---
title: 'Soluciones de la Fase 1 de la Liga de Programación omegaUp'
author: 'DiegoBriaares'
author_email: 'briaares@gmail.com'
date: Wed, 01 Apr 2020 18:08:10 +0000
draft: false
tags: ['Solution', 'Concursos', 'liga omegaup', 'Material de estudio', 'solución', 'soluciones']
---

## [Problema A](https://omegaup.com/arena/problem/Rango-simple)

Para este problema, consideramos un arreglo de ocurrencias $O$ sobre los elementos del arreglo. De modo que la respuesta está dada por

$\\sum\\limits\_{i=A}^B O\_{i}$

{{< gist DBriaares df979afcf721ba5aee429f948350e051 >}}

## [Problema B](https://omegaup.com/arena/problem/A-contar-lapices)

Si consideramos el mismo arreglo de ocurrencias $O$ sobre los elementos del arreglo, la respuesta está dada por $O\_k$.

{{< gist DBriaares 2380189d0e29c2e29ab52771f353ebbe >}}

## [Problema C](https://omegaup.com/arena/problem/nofib)

Podemos generar todos los elementos de la secuencia de Fibonacci hasta $30000$, y guardarlos en un mapa $M$, de modo que $M\_k = 1$ si $k$ es un elemento de Fibonnaci, y $M\_k = 0$ en caso contrario. Generamos la respuesta simplemente iterando desde $i = 4$ hasta $i = N - 1$, e imprimimos $i$ si $M\_i = 0$.

{{< gist DBriaares 7d2a6b7afb388ceb9b22cf2f077670f5 >}}

## [Problema D](https://omegaup.com/arena/problem/Posicion-Fibonacci)

La clave para este problema, es usar variables que no provoquen un desbordamiento, por ejemplo, unsigned long long. Luego, es conocido que la serie de Fibonacci crece rápidamente, lo suficiente, como para generar la secuencia con todos sus elementos menores o iguales a $N$, guardando por cada uno su respectiva posición en ella. Por lo tanto, basta con checar si $N$ es un elemento, e imprimir su posición. En caso de no serlo, imprimimos $-1$.

{{< gist DBriaares 00ea7419ff9454b86d63b052d44d0337 >}}

## [Problema E](https://omegaup.com/arena/problem/estacion)

Este tipo de problema es conocido como straight-forward. Podemos guardar las estaciones de radio, y checar cuál estación es la mas cercana a la frecuencia dada, con una simple resta. En caso de haber dos estaciones con la misma distancia, la respuesta es la mayor. Solo debemos cuidar que la frecuencia esté dentro del rango permitido.

{{< gist DBriaares f1fb91811095dee376d6961c65b8e017 >}}

## [Problema F](https://omegaup.com/arena/problem/Tu-y-tu-Futuro)

En este problema lo que tenemos es un grafo dirigido acíclico con aristas pesadas (intuitivamente, es un árbol, sin la propiedad de que cualquier par de nodos estan conectados por un único camino). Los vértices son los eventos temporales, las aristas son dirigidas de $p\_i$ a $i$, y su peso es $d\_i$. Además, cada vértice contiene un valor extra $r\_i$. Un grafo que podemos asociar al primer caso de ejemplo es el siguiente.

![](/images/example_graph_correct.jpg)

Sean $v\_1$ y $v\_k$ dos vértices distintos, tales que $v\_1$ es ancestro de $v\_k$. Es decir, existe un camino $v\_1 \\rightarrow v\_2 \\rightarrow \\ldots \\rightarrow v\_k$ en el grafo. Definimos $S(v\_1, v\_k)$ como

$\\sum\\limits\_{i=1}^{k - 1} d\_{v\_i}$

Es decir, la suma de los pesos en las aristas del camino. De modo que el problema se convierte en: Para cada vertice $v$, contar cuántos vértices $u$ en su "subárbol" $\\;$ existen tales que

$r\_u - S(v, u) \\geq 0 $

Porque esto siginifica que tenemos suficientes segundos para viajar por el tiempo desde $u$ hasta $v$.

Consideremos un arreglo $E$, donde la entrada $E\_v$ guarda cuántos descendientes $u$ de $v$ satisfacen

$r\_u - S(v, u) \\geq 0 $

Pero

$r\_u - S(p\_v, u) < 0 $

Donde $p\_v$ es el padre de $v$. Si $v = 0$, entonces no hace falta considerar a su padre, puesto que no podemos viajar por el tiempo a algún ancestro de $0$ (ya que ni siquiera existe alguno).

En otras palabras, $E\_v$ guarda cuántos descendientes de $v$ llegan a lo mas al vértice $v$.

También consideremos un arreglo $D$, donde la entrada $D\_v$ guarda cuántos descendientes $u$ de $v$ satisfacen

$ r\_u - S(v, u) < 0 $

Es decir, $D\_v$ guarda cuántos descendientes de $v$ no pueden llegar al vertice $v$.

Y además mantengamos un arreglo $T$, donde la entrada $T\_v$ guarda el tamaño del "subárbol" de $v$ (incluyendo a $v$). En otras palabras, cuántos descendientes tiene $v$ en total mas el mismo.

Por lo tanto, la respuesta final para el vértice $v$ está dada por

$(T\_v - 1) - \\sum\\limits\_{v \\rightarrow u} (E\_u + D\_u)$

donde $u$ es un hijo directo de $v$. Ya que esto calcula cuántos descendientes de $v$ si pueden llegar a $v$.

Para el cálculo de nuestros arreglos, hacemos una dfs sobre el "árbol"  (partiendo del vertice 0). Para cada vértice $u$, hacemos una búsqueda binaria sobre un arreglo que mantenga la suma acumulada de los costos sobre las aristas que forman parte del camino de $0$ a $u$, que nos devuelva el máximo ancestro $v$ al que podemos llegar desde $u$.  Lo que nos dice que  $E\_v$ actualiza su valor a $E\_v + 1$ (inicialmente, $E\_1 = E\_2  = \\ldots = E\_n = 0$). Esto se puede hacer usando un arreglo global. La idea es añadir la suma acumulada, luego explorar recursivamente el subárbol de $u$, y luego quitar la suma acumulada que añadimos. Esto es particularmente sencillo si usamos un vector de la STL para el arreglo global.

El arreglo $T$ se calcula facilmente en la misma dfs, ya que

$T\_v = 1 + \\sum\\limits\_{v \\rightarrow u} (T\_u)$

Ahora podemos generar $D$, al estilo de programacion dinámica usando $E$. Notemos que

$D\_v = \\sum\\limits\_{v \\rightarrow u} (E\_ u + D\_u)$

Lo que se puede hacer en la misma DFS.

Por lo tanto, nuestro algoritmo tiene complejidad $O(Nlog(N))$.

{{< gist DBriaares 230bf4f852d80fba75be9f2c322124b4 >}}

## [Problema G](https://omegaup.com/arena/problem/Karel-y-los-quebrados)

Primero reescribamos la expresión dada como

$k = \\dfrac{xy}{x + y}$

De donde podemos despejar $y$ como

$y = \\dfrac{xk}{x - k}$

Sin perdida de generalidad, supongamos $x \\leq y$, entonces se tiene

$x \\leq \\dfrac{xk}{x - k}$

$x^2 \\leq 2xk$

$x \\leq 2k$

Por lo tanto, podemos iterar $x$ desde $1$ hasta $2k$, obtenemos $y$, y verificamos que $k = \\dfrac{xy}{x + y}, y > 0$.

Guardamos las parejas que satisfazcan dichas condiciones y las imprimimos en el orden requerido, cuidando no repetir alguna respuesta.

Lo que nos deja con un algoritmo de complejidad $O(k)$.

Una solución alternativa es la siguiente:

Te puedes dar cuenta que $x, y > k$, entonces el problema se convierte a  buscar $a$ y $b$ que cumplan

$\\dfrac{1}{k} = \\dfrac{1}{k + a} + \\dfrac{1}{k + b}$

con $a,b > 0$. Si simplificas la igualdad llegas a que $k^2 = ab$, así que todo se reduce a encontrar las parejas de divisores $a, b$ de $k^2$.  Lo que deja también un algoritmo de complejidad $O(k)$.

Nota: Agradezco a José Tapia y a Carlos Galeana por su colaboración en el problema $G$.

{{< gist DBriaares 1bf8bac6ba8c1040befc7b4b64900ac2 >}}
