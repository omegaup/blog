---
title: 'Solución a "Metro"'
author: 'Lira'
author_email: 'elira@elira.me'
date: Mon, 07 Jan 2013 17:22:45 +0000
draft: false
tags: ['Solution', 'Alain Acevedo', 'Etapa 1', 'Examen 12', 'preselectivo', 'solución', 'Soluciones Preselectivo 2013']
aliases: ['/solucion-a-metro']
---

**Concurso:** [Preselectivo para la IOI 2013, Etapa 1, Examen 12](https://omegaup.com/arena/IOI2013E1P12) **Autor: **[Alain Acevedo Mejía](mailto:alainacme@gmail.com)

El problema en cuestión se reduce a encontrar un árbol de expansión mínima. La solución es una aplicación directa de alguno de los algoritmos existentes para ello (bien implementada), por lo que hablaré brevemente sobre una de las posibilidades y daré referencias donde puedan encontrar información más detallada.

Para encontrar el costo mínimo de unir todas las estaciones debemos encontrar el árbol de expansión mínima de la gráfica en cuestión (es decir, una subgráfica conexa que una todos los vértices de la gráfica original y cuyo peso (la suma de los costos de todas sus aristas) sea el mínimo posible (siempre es un árbol)). Para ello una opción es usar el algoritmo de Kruskal: Ordenamos las aristas por su peso y vamos agregando cada arista de peso mínimo que no cree un ciclo en la gráfica. Hacemos esto hasta haber conectado todos los vértices de nuestra gráfica. Por la cantidad de aristas que tenemos requerimos ordenar eficientemente y verificar si las aristas forman un ciclo o no eficientemente en cada paso, de lo contrario el programa no correrá en tiempo.

Para verificar si se forma o no un ciclo agregando una determinada arista empleamos el algoritmo conocido como Union Find, que se explica ampliamente en las secciones 16.7, 16.8 y 16.9 del libro Problemas y Algoritmos de Luis E. Vargas Azcona. Es importante mencionar que para obtener los 100 puntos en el problema es necesario implementar las optimizaciones que se mencionan (y aunque no fuera así no está de más que las conozcan).

Además del libro de Luis E. Vargas, que recomiendo ampliamente, sugiero la página de Pier Guillen http://pier.guillen.com.mx/ , que en ->Algorithms ->10. Gráficas ->10.6 Árboles Mínimos Generadores desarrolla el tema en cuestión. Y claro, no está de más que consulten el tema en el libro Introduction to Algorithms de Thomas H. Cormen, que en la tercera edición trabaja el tema en el capítulo VI. Graph Algorithms ->23 Minimum Spanning Trees.

El siguiente código resuelve el problema:

{{< gist OlimpiadaMexicanadeInformatica 6559170 >}}