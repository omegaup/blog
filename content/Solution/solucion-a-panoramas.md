---
title: 'Solución a "Panoramas"'
author: 'Freddy'
author_email: 'me@freddy.mx'
date: Thu, 16 Jan 2014 17:36:38 +0000
draft: false
tags: ['Solution', 'Etapa 1', 'Examen 17', 'macs', 'preselectivo', 'solución', 'Soluciones Preselectivo 2013']
math: true
aliases: ['/solucion-a-panoramas']
---

**Concurso:** [Preselectivo para la IOI 2014, Etapa 1, Problemset 17](https://omegaup.com/arena/IOI2014E1P17#problems/Tour) **Autor:** Miguel Ángel Covarrubias **Fuente**: Miguel Ángel Covarrubias

El problema es un Steiner tree problem (un MST pero donde sólo hay que conectar un subconjunto de nodos) pero con costo por nodo en vez de por arista. El grafo de los panoramas es un árbol más un ciclo. Para un árbol una solución es poner como raíz a $ s\_1$ y para cada $ s\_i$ marcar los nodos en su camino hacia la raíz. Se puede usar DP o recursión para calcular el mínimo numero de vertices que conectan todos los nodos interesantes y pasan por la raíz para cada subárbol.

$ \\mathrm{dp}\_r=\\mathrm{interesante}(r)\\ \\mathrm{si}\\ \\Sigma\_h\\mathrm{dp}\_h=0$ $ \\mathrm{dp}\_r = \\Sigma\_h\\mathrm{dp}\_h+1\\ \\mathrm{si}\\ \\Sigma\_c\\mathrm{dp}\_h>0$

$ h$ es un hijo de $ r$. La arista extra $ (u,v)$ en el ciclo $ c$ permite usar otros caminos a lo largo de $ c$. Tales caminos deben conectar todos los nodos en $ c$ que tengan nodos interesantes en su árbol después de quitar las aristas del ciclo $ E-c$. Etiquetemos tales nodos con un uno y los demás nodos del $ c$ con un cero. Para $ E-(u,v)$ el ciclo sólo no cubre los últimos ceros. Para encontrar la solución sólo basta encontrar la secuencia de ceros más grande. En el siguiente diagrama, la arista que falta es $ (u,v)$. La DP sólo no usa el último cero, pero es mejor no usar los dos ceros que están adyacentes.

```cpp
  0 1
 /   \\
1     0
 \\   /
  1-0

```

Este código implementa la solución.

{{< gist OlimpiadaMexicanadeInformatica 8468920 >}}