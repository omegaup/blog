---
title: 'Solución a "Chilly Rapero"'
author: 'Lira'
author_email: 'elira@elira.me'
date: Sat, 12 Jan 2013 19:41:11 +0000
draft: false
tags: ['Solution', 'Etapa 1', 'Ethan Jiménez', 'Examen 12', 'preselectivo', 'solución', 'Soluciones Preselectivo 2013']
aliases: ['/solucion-a-chilly-rapero']
---

**Concurso:** [Preselectivo para la IOI 2013, Etapa 1, Examen 12](https://omegaup.com/arena/IOI2013E1P12) **Autor:** [Ethan Jiménez Vargas](http://twitter.com/erosethan)

  

La clave para resolver este problema es interpretar las palabras como nodos y los cambios entre palabras como aristas, de manera que podamos verlo todo como un grafo no dirigido. Asignamos a cada palabra un nodo y creamos las aristas entre nodos verificando alguna de las condiciones que se proponen en el enunciado del problema: si una palabra A es un prefijo o sufijo de la palabra B o la palabra A difiere con la palabra B por un solo caracter, establecemos una arista entre los nodos A y B.

  

Crear las aristas entre los nodos tiene una complejidad de O(LN2) y la manera más simple de almacenar dichas aristas es mediante una matriz de adyacencia. Ya que tenemos el grafo planteado, buscaremos la manera más rápida de cambiar de palabra entre cualquier par de palabras, esto puede conseguirse usando el algoritmo de [Floyd-Warshall](http://es.wikipedia.org/wiki/Algoritmo_de_Floyd-Warshall) con una complejidad de O(N3) que es suficiente para el problema.

  

Finalmente, para obtener la respuesta sumamos el mínimo número de cambios requeridos entre todos los pares de palabras consecutivas en el rap, este número de cambios fue obtenido mediante el algoritmo de Floyd-Warshall. El número total de cambios lo multiplicamos por 0.2 y será la respuesta para el problema.

  

Complejidad de la solución: O(LN2+N3)