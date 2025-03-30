---
title: 'Solución alternativa a "Decepción"'
author: 'Freddy'
author_email: 'me@freddy.mx'
date: Fri, 17 Jan 2014 02:14:47 +0000
draft: false
tags: ['Solution', 'Etapa 1', 'Ethan', 'Examen 8', 'Freddy', 'preselectivo', 'solución', 'Soluciones Preselectivo 2013']
math: true
---

**Concurso:** [Preselectivo para la IOI 2014, Etapa 1, Problemset 8](https://omegaup.com/arena/IOI2014E1P8#problems/decepcion) **Autor:** [Freddy Román Cepeda](http://freddy.mx/) **Fuente**: Ethan Jiménez Vargas

Esta es una solución alternativa al problema. La solución pensada originalmente consiste en una búsqueda podada. Sin embargo, esta solución corre en tiempo y memoria $ O(N^2)$, mucho mejor de lo necesario para obtener todos los puntos.

Podemos dividir el problema a la mitad con una observación simple: la torre más alta debe verse desde ambos lados. Además, no dejará que el resto de las torres que ocurren después de ella se vean. Podemos aprovechar este hecho para separar el problema en dos partes: izquierda y derecha. Si $ f(n,m)$ cuenta de cuántas maneras se pueden poner $ n$ torres de tal manera de que sólo $ m$ se pueden ver de un lado, la respuesta que queremos es $ \\sum\_{i=0}^{N-1} ({N-1 \\choose i} \* f(i,F-1) \* f(N-i-1,B-1))$.

En otras palabras, esta expresión es la suma de las maneras de cumplir las condiciones originales del problema colocando la torre más alta en la posición $ i$. Es decir, hay $ {N-1 \\choose i}$ maneras de distribuir el resto de las torres a la izquierda o derecha de la torre más alta (porque la única cosa que importa es el orden relativo de las torres y todas las alturas son distintas), las cuales multiplicamos por las maneras de hacer que se cumpla la condición sobre el lado izquierdo y lo mismo con el lado derecho.

Ahora, para computar $ f$, podemos reusar la misma observación. Cuando colocamos la torre más alta en el índice $ i$, cualquier torre que pongamos después de $ i$ ya no se podrá ver. Del lado visible, necesitamos reordenar las torres restantes de tal manera que sólo se puedan ver $ m-1$. Además, podemos reordenar el lado oculto de la manera que queramos. Con esto tenemos que

$ f(0,0) = 1$ $ f(n,m) = \\begin{cases} 0 & \\text{si } m > n\\\\ \\sum\_{i=0}^{n-1}({n-1 \\choose i} \* f(i,m-1) \* (n-i-1)!) & \\text{de lo contrario} \\end{cases}$

con lo que resolvemos el problema en tiempo $ O(N^3)$ y memoria $ O(N^2)$.

Esto se puede mejorar aún más observando que $ f(n,m)$ está computando los números de Stirling de primera clase, para los cuales hay una recurrencia que se puede utilizar para calcularlos en tiempo $ O(N^2)$.

Los números de Stirling de primera clase cuentan las permutaciones de $ n$ elementos con $ m$ ciclos. Considere una permutación con $ m$ ciclos de los $ n$ edificios. Cada ciclo debe tener un elemento máximo. Además podemos ordenar los ciclos entre sí por su elemento mayor. De esta manera, tenemos $ m$ edificios visibles. Ya que estamos contando todas las permutaciones con $ m$ ciclos, cada posible ordenamiento con $ m$ edificios visibles será considerada. Esto se debe a que cada ciclo tiene únicamente un ordenamiento en el cual sólo uno de sus elementos es visible: el que comienza con el edificio más grande.

Aquí está el código que implementa esta solución.

{{< gist OlimpiadaMexicanadeInformatica 8467347 >}}