---
title: 'Soluciones de la Fase 2 de la Liga de Programación omegaUp'
author: 'DiegoBriaares'
author_email: 'briaares@gmail.com'
date: Sun, 19 Apr 2020 08:05:15 +0000
draft: false
tags: ['Solution', 'Concursos', 'liga omegaup', 'Material de estudio', 'solución']
---

1.  **[Problema A](https://omegaup.com/arena/problem/No-se-molesto-en-escribir-uno)**

Las siguientes observaciones son claves para resolver el problema.

1.  Si $p \\leq n$, entonces $(w$ % $p) < n$. Así que el máximo residuo posible es $n - 1$.
2.  Si $w$ satisface la condición del enunciado, entonces hay $n - 1$ diferentes residuos, luego los residuos son un subconjunto de $n - 1$ elementos, de la colección $\\lbrace 0, 1, \\ldots , n - 1\\rbrace$.
3.  El mínimo común múltiplo de $1, 2, \\ldots , n$ es mayor o igual al producto de los primos menores o iguales a $ n$.
4.  El producto de los primos menores o iguales a $50$ es mayor a $10^{18}$

Veamos el caso donde $0$ no forma parte de los residuos. De **1**, vemos que

$w$ % $n = n - 1$

$w$ % $n - 1 = n - 2$

$\\ldots$

$w$ % $2= 1$ .

Entonces $w + 1$ es un común múltiplo de $2, 3, 4,  \\ldots,  n$.

$(\*)$ Luego, de la observación **3** vemos que

$mcm(2, 3, 4,  \\ldots,  n) \\geq P\_n$

 Donde $P\_n$ es el producto de los primos menores o iguales a $n$.

$(\*)$ Pero $P\_{50} > 10^{18}$. Así que si $w + 1$ es un común múltiplo de $2, 3, 4,  \\ldots,  n$ entonces $n \\leq 50$.

Ahora el caso donde $0$ sí forma parte de los residuos. Se sigue que existe $1 < k \\leq n$ tal que $w$ % $k = 0$. Con la misma lógica, de **1**, vemos qué

$w$ % $k - 1 = k - 2$

$\\ldots$

$w$ % $2= 1$ .

Con ayuda de  $(\*)$, vemos que $k \\leq 50$.  ¿Cuál es el orden de los residuos mayores a $k$?. Para esto, consideremos el mismo orden que usamos en el caso donde $0$ no forma parte de los residuos.

El residuo $k - 1$ que originalmente pertenecía a $k$ tiene dos direcciones: ser el residuo de un numero mayor que $k$, o $k - 1$ es el residuo que queda  descartado.

Sea $M - 1$ el residuo que queda descartado, entonces $w + 1$ debe ser común múltiplo de $n, n - 1, n - 2, \\ldots , M + 1$, y para esto,

$(w + 1) \\geq n \* (n - 1) \* (n - 2)  \* \\ldots \* (M + 1)$

Lo cual sería imposible si $n - M  \\geq 50$.

Ahora, si no descartamos los residuos de $k + 1, \\ldots , k + 50$, entonces $w + 1 \\geq  (k + 1) \* \\ldots  \* (k + 50)$ lo cual sería de nuevo imposible.

Por lo tanto, $M + 50 > n$ y $M - 50 < 1$.

De modo que, si $n > 100$, la respuesta es "No".  El problema ahora se limíta a $n \\leq 100$ y $w \\leq 10^{18}$.

Para éste problema, podemos guardar todos los residuos de $w$ con los números menores o iguales a $n$ en una estructura que nos maneje operaciones básicas de conjuntos, como un set. Usando el set, la respuesta es "Si", si el tamaño del set después de añadir los residuos es $n - 1$, y "No" en caso contrario.

*   **[Problema B](https://omegaup.com/arena/problem/La-fiesta-de-Filiberto)**

Tratemos cada query de manera independientemente, y nos tomamos $a\_1, a\_2, \\ldots, a\_k$ como los puntos dados en la query.

El problema es equivalente a encontrar un círculo con el menor radio $r$ posible, tal que todos los puntos de la query están dentro de él.  La respuesta sería el radio $r$.

Él cuál es un problema equivalente a encontrar el menor radio $r$ tal que existe al menos un punto contenido en cada círculo con centro $a\_1, a\_2, \\ldots a\_n$ y radio $r$.

Si dicho punto $p$ existe, entonces existe al menos un par de círculos que se intersecten en algun punto $T$. Por supuesto, la distancia de $p$ a $T$ es menor o igual a $r$.

Por lo tanto, la respuesta puede ser encontrada con una búsqueda binaria.

1.  Fíjamos el radio $r$, el cual mandamos a la búsqueda binaria.
2.  Enumeramos los $k$ círculos.
3.  Encontramos y enumeramos las intersecciones para cada par de círculos.
4.  Para cada intersección, recorremos cada centro. Si hay un centro $a\_i$que tiene una distancia menor o igual a $r$ entonces el menor radio que buscamos sí es menor o igual a $r$.

El costo de cada chequeo en la búsqueda binaria es $O(k^3)$. Y la búsqueda binaria tiene un costo de aproximádamente $50$ operaciones. Pero precalculando las soluciones, de **4**, para todos los $l$ puntos antes de contestar las preguntas, reducimos el costo del chequeo a $O(k^2)$, lo cual ya es suficiente para resolver el problema.

*   **[Problema C](https://omegaup.com/arena/problem/La-fiesta-de-Briares)**

Lo que buscamos, es la cantidad de subconjuntos tales que su $\\&$  es igual a $0$. Esta cantidad puede verse como la cantidad de subconjuntos totales, menos la cantidad de subconjuntos tales que su $\\&$ es diferente de $0$. Ahora, esta cantidad puede verse como la cantidad de subconjuntos cuyo  $\\&$ tienen exactamente un bit prendido, más la cantidad de subconjuntos cuyo $\\&$ tienen exactamente dos bits prendidos, $\\ldots$, más la cantidad de subconjuntos cuyo $\\&$ tienen exactamente $20$ bits prendidos (esto ya que $10^6 \\leq 2^{20}$).

Para esto usaremos el principio de inclusión - exclusión. De modo que la cantidad que buscamos esta dada por

$S\_ 0 - S\_1 + S\_2 - S\_3 + \\ldots + S\_{20}$

Donde $S\_i$ nos dice cuantos subconjuntos tienen  un ~and~ con al menos $i$ bits prendidos.

Ahora, $S\_i$ puede ser calculado con la ayuda de una SOS (Sum Over Subsets) DP.

Para esto,  sea $mask$ alguna máscara de bits en $\[1, 2^{20}\]$, y definamos $m$ como el ~and~ de algún subconjunto del arreglo, tal que $mask \\& m = mask$. Es decir, $mask$ es una submáscara de $m$. Entonces, DP\[mask\] nos dice cuántas diferentes $m$ existen. (dos $m$ se consideran diferentes, si las posiciones de los elementos en el arreglo que la componen no son todas iguales). Está DP puede calcularse de la siguiente manera.

1.  Los casos base los formamos añadiendo la cantidad de ocurrencias de $x$ en el arreglo, a $DP\[x\]$.
2.  Fíjamos $bit \\in \[1, 20\]$, de izquierda a derecha.
3.  Para cada mask en $\[0, 2^{20}\]$, tal que mask tiene el $bit$-ésimo bit apagado  (mas formalmente, $mask \\& (1 << bit)  = 0$ ) se hace la transición DP\[mask | (1 << bit)\] += DP\[mask\].

De modo que $S\_i = 2^{DP\[m\]}$, para cada $m$ una máscara con al menos $i$ bits prendidos.

*   **[Problema D](https://omegaup.com/arena/problem/Saltos-de-rana)**

Sean $p\_1, p\_2, \\ldots, p\_m$ las posiciones de la cadena en donde hay un $1$.

Definimos $r$ cómo la posición donde yace la rana, y $b$ como la cantidad de brincos que ha dado hasta el momento. Inicialmente, $r = p\_1$ y $b = 0$. La respuesta puede encontrarse mediante siguiente algoritmo.

1.  Encontrar $j$ tal que $p\_j - r \\leq k$ y $p\_{j + 1} > k$
2.  Hacemos
    
    $b = b + 1$ y $r = p\_j$
    
3.  Repetimos mientras $r \\neq p\_m$.

La respuesta final es $b$. El algoritmo se puede implementar con complejidad lineal usando la técnica de two pointers (usando $r$ y $j$ como los pointers).

*   **[Problema E](https://omegaup.com/arena/problem/Analizar-palabra)**

Rescatando la cantidad de ocurrencias para cada vocal (no hay que olvidarse de contar las mayúsculas) mientras recorremos la cadena, estamos listos para imprimir las tres respuestas. Las cuales son

**(a) ** Tamaño de la cadena.

**(b)**  Suma de las ocurrencias de cada vocal.

**(c)**  Imprimir la cadena de derecha a izquierda.

*   **[Problema F](https://omegaup.com/arena/problem/Suma-de-vectores)**

Salvemos los dos vectores dados $a\_1, a\_2, \\ldots , a\_n$ y $b\_1, b\_2, \\ldots , b\_n$, y generemos un nuevo vector $c\_1 = (a\_1 + b\_1), \\ldots, c\_n = (a\_n + b\_n)$. La solucion es imprimir $c\_1, c\_2, \\ldots, c\_n$.