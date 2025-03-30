---
title: 'Solución a "Poema Equino"'
author: 'Freddy'
author_email: 'me@freddy.mx'
date: Sun, 27 Jul 2014 07:08:35 +0000
draft: false
tags: ['Solution', '2014', 'bfs', 'búsqueda', 'dfs', 'Etapa 1', 'Freddy', 'nieves', 'poema equino', 'preselectivo', 'Problemset 5', 'solución', 'soluciones', 'Soluciones Preselectivo 2014']
math: true
---

**Concurso:** [Preselectivo para la IOI 2015, Etapa 1, Problemset 5](https://omegaup.com/arena/IOI2015E1P5/#problems/Poema-Equino) **Autor:** [Freddy Román Cepeda](http://freddy.mx/) **Fuente**: Edgar Augusto Santiago Nieves, [Freddy Román Cepeda](http://freddy.mx/)

Los límites de este problema permitían hacer una búsqueda sobre todos los estados posibles de los caballos sobre el teclado, ya que si el estado es $ (\\text{poema},\\text{fila caballo}\_1,\\text{columna caballo}\_1,\\text{fila caballo}\_2,\\text{columna caballo}\_2)$, solamente hay $ 100 \\times (4 \\times 10)^2 = 160,000$ estados distintos.

Además, como el problema no pide la cantidad mínima de movimientos no hace falta hacer una BFS (búsqueda en amplitud), sino que una DFS (búsqueda en profundidad) utilizando el mismo stack del lenguaje es suficiente. Para simplificar la implementación, se podían utilizar varias observaciones. Particularmente, no importa qué caballo es el 1 o el 2, por lo que en vez de escribir código para mover a ambos basta con añadir una transición que cambie los roles de los caballos en cada estado. Esto además de simplificar la implementación sirve como una poda ya que ¡reduce la cantidad de estados a la mitad! (¿por qué?). También, se puede aprovechar que los operadores booleanos en C/C++ evalúan a 1 cuando son verdaderos y a 0 cuando son falsos, lo cual es bastante útil para indexar arreglos.

Varios competidores fallaron en su primer intento por no revisar que los caballos no podían ocupar la misma tecla al mismo tiempo. ¡Cuidado!

La siguiente solución implementa las simplificaciones descritas anteriormente.

{{< gist OlimpiadaMexicanadeInformatica 3f4d3496fe0e3aadd12b >}}