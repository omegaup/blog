---
title: 'Solución alternativa a "Decepción"'
author: 'Freddy'
author_email: 'me@freddy.mx'
date: Fri, 17 Jan 2014 02:14:47 +0000
draft: false
tags: ['Solution', 'Etapa 1', 'Ethan', 'Examen 8', 'Freddy', 'preselectivo', 'solución', 'Soluciones Preselectivo 2013']
math: true
aliases: ['/solucion-alternativa-a-decepcion']
---

**Concurso:** [Preselectivo para la IOI 2014, Etapa 1, Problemset 8](https://omegaup.com/arena/IOI2014E1P8#problems/decepcion) **Autor:** [Freddy Román Cepeda](http://freddy.mx/) **Fuente**: Ethan Jiménez Vargas

Esta es una solución alternativa al problema. La solución pensada originalmente consiste en una búsqueda podada. Sin embargo, esta solución corre en tiempo y memoria $latex O(N^2)$, mucho mejor de lo necesario para obtener todos los puntos.

Podemos dividir el problema a la mitad con una observación simple: la torre más alta debe verse desde ambos lados. Además, no dejará que el resto de las torres que ocurren después de ella se vean. Podemos aprovechar este hecho para separar el problema en dos partes: izquierda y derecha. Si $latex f(n,m)$ cuenta de cuántas maneras se pueden poner $latex n$ torres de tal manera de que sólo $latex m$ se pueden ver de un lado, la respuesta que queremos es $latex \\sum\_{i=0}^{N-1} ({N-1 \\choose i} \* f(i,F-1) \* f(N-i-1,B-1))$.

En otras palabras, esta expresión es la suma de las maneras de cumplir las condiciones originales del problema colocando la torre más alta en la posición $latex i$. Es decir, hay $latex {N-1 \\choose i}$ maneras de distribuir el resto de las torres a la izquierda o derecha de la torre más alta (porque la única cosa que importa es el orden relativo de las torres y todas las alturas son distintas), las cuales multiplicamos por las maneras de hacer que se cumpla la condición sobre el lado izquierdo y lo mismo con el lado derecho.

Ahora, para computar $latex f$, podemos reusar la misma observación. Cuando colocamos la torre más alta en el índice $latex i$, cualquier torre que pongamos después de $latex i$ ya no se podrá ver. Del lado visible, necesitamos reordenar las torres restantes de tal manera que sólo se puedan ver $latex m-1$. Además, podemos reordenar el lado oculto de la manera que queramos. Con esto tenemos que

$latex f(0,0) = 1$ $latex f(n,m) = \\begin{cases} 0 & \\text{si } m > n\\\\ \\sum\_{i=0}^{n-1}({n-1 \\choose i} \* f(i,m-1) \* (n-i-1)!) & \\text{de lo contrario} \\end{cases}$

con lo que resolvemos el problema en tiempo $latex O(N^3)$ y memoria $latex O(N^2)$.

Esto se puede mejorar aún más observando que $latex f(n,m)$ está computando los números de Stirling de primera clase, para los cuales hay una recurrencia que se puede utilizar para calcularlos en tiempo $latex O(N^2)$.

Los números de Stirling de primera clase cuentan las permutaciones de $latex n$ elementos con $latex m$ ciclos. Considere una permutación con $latex m$ ciclos de los $latex n$ edificios. Cada ciclo debe tener un elemento máximo. Además podemos ordenar los ciclos entre sí por su elemento mayor. De esta manera, tenemos $latex m$ edificios visibles. Ya que estamos contando todas las permutaciones con $latex m$ ciclos, cada posible ordenamiento con $latex m$ edificios visibles será considerada. Esto se debe a que cada ciclo tiene únicamente un ordenamiento en el cual sólo uno de sus elementos es visible: el que comienza con el edificio más grande.

Aquí está el código que implementa esta solución.

{{< gist OlimpiadaMexicanadeInformatica 8467347 >}}