---
title: 'Solución a "Químicos"'
author: 'Freddy'
author_email: 'me@freddy.mx'
date: Thu, 23 Jan 2014 03:51:39 +0000
draft: false
tags: ['Solution', 'Etapa 1', 'Ethan', 'Examen 6', 'lhchavez', 'preselectivo', 'solución', 'Soluciones Preselectivo 2013']
math: true
aliases: ['/solucion-a-quimicos']
---

**Concurso:** [Preselectivo para la IOI 2014, Etapa 1, Problemset 6](https://omegaup.com/arena/IOI2014E1P6#problems/quimicos) **Autor:**  [Luis Héctor Chávez (lhchavez)](http://lhchavez.com/) **Fuente**: Ethan Jiménez Vargas

Éste es un problema que tiene una solución elegante y determinística pero requiere algoritmos avanzados bastante complicados. Lo bueno es que es posible aproximar a la solución utilizando fuerza bruta mediante backtracking.

El problema nos pide encontrar una manera de asignar sustancias a los tubos y después mezclarlas con las dos operaciones disponibles (suma y diferencia absoluta) para terminar con un acomodo homogéneo de sustancias: la diferencia entre el tubo con más cantidad y con menos cantidad de sustancia debe ser lo más pequeña posible. Una manera de hacerlo es proponer un intervalo $latex \[a,b\]$ y ver si es posible asignar sustancias y aparear los tubos de manera que la cantidad de sustancia resultante de la mezcla en todos los tubos esté contenido dentro del intervalo. Para acelerar el proceso, puedes elegir los intervalos haciendo una búsqueda binaria de acuerdo a su ancho $latex b-a$, porque a fin de cuentas lo que nos pide el problema es precisamente el ancho mínimo. Para cada intervalo propuesto $latex \[a,b\]$, podemos hacer un grafo con $latex 2N$ nodos (uno para cada tubo), agregando un arco entre dos nodos $latex A$ y $latex B$ si $latex A+B\\in\[a,b\]$ ó $latex |A-B|\\in\[a,b\]$. Después, buscamos un [apareamiento máximo](http://es.wikipedia.org/wiki/Apareamiento_(teor%C3%ADa_de_grafos)) en el grafo: buscamos el conjunto de arcos con cardinalidad máxima tal que cada nodo tenga a lo más un arco incidente. Esto se puede encontrar con el [algoritmo de Edmonds](http://es.wikipedia.org/wiki/Algoritmo_de_Emparejamiento_de_Edmonds) (también conocido como el Blossom algorithm por la forma de los ciclos de longitud impar) en tiempo $latex O(|2N|^4)$, lo cual encontraría todas las soluciones en solo un par de segundos.

Lamentablemente la implementación del algoritmo de Edmonds es bastante complicada. Como este es un problema de solo-salida y todo se vale, en vez de hacer el intento por implementarlo, utilicé la librería [Boost](http://www.boost.org/) de C++ que ya tiene muchísimos algoritmos de [grafos](http://www.boost.org/doc/libs/1_55_0/libs/graph/doc/index.html) ya implementados.

{{< gist OlimpiadaMexicanadeInformatica 8572476 >}}

Ahora, si no se te ocurre usar el algoritmo de Edmonds o no tienes acceso a Boost, aún así puedes obtener una cantidad decente de puntos usando una heurística: podemos _intentar_ hacer un apareamiento máximo usando fuerza bruta, rindiéndonos si el problema suena muy complicado y asumimos que no existe un apareamiento. Una fuerza bruta naïve con un contador que se decrementa cada vez que se llama la función de búsqueda es más que suficiente. Haciendo un par de modificaciones al algoritmo anterior nos da una solución que nos da el 80% de los casos bien:

{{< gist OlimpiadaMexicanadeInformatica 8572478 >}}

Claro que si te quieres ver greedy, puedes subirle al número de intentos, pero posiblemente no haya suficiente tiempo en el concurso para que termine. Si llegas a utilizar estas técnicas "impuras", asegúrate primero de obtener cualquier solución que te de puntos antes de subirle para encontrar mejores respuestas.