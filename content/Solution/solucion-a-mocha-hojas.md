---
title: 'Solución a "Mocha Hojas"'
author: 'Freddy'
author_email: 'me@freddy.mx'
date: Sat, 18 Jan 2014 23:25:14 +0000
draft: false
tags: ['Solution', 'beto', 'Etapa 1', 'Examen 17', 'Freddy', 'preselectivo', 'solución', 'Soluciones Preselectivo 2013']
math: true
aliases: ['/solucion-a-mocha-hojas']
---

**Concurso:** [Preselectivo para la IOI 2014, Etapa 1, Problemset 17](https://omegaup.com/arena/IOI2014E1P17#problems/Mocha-Hojas) **Autor:** [Freddy Román Cepeda](http://freddy.mx/) **Fuente**: Alberto José Ramírez Valadez

Para simplificar el análisis, podemos notar que la respuesta que nos piden es igual al total de los pesos de las hojas del árbol menos el total de los pesos de las hojas del árbol ya balanceado. De ahora en adelante, trataremos el problema como si tuviéramos que conseguir este segundo valor, en vez del número de operaciones. Entonces queremos maximizar el peso total del árbol balanceado, para minimizar la cantidad de operaciones.

Consideremos el caso de un árbol con un solo nivel. Ya que sólo podemos restarle a los pesos de las hojas, evidentemente el peso máximo del árbol se alcanza cuando se emparejan todas las hojas al peso de la hoja con peso mínimo.

Ahora, consideremos un árbol con dos niveles. Si la raíz tiene $latex k$ hijos, para cada hijo $latex i$ sea $latex h\_i$ el subárbol de $latex i$, $latex b\_i$ el número de hojas de $latex h\_i$, y $latex c\_i$ el peso del árbol obtenido de realizar el procedimiento del párrafo anterior a $latex h\_i$. Si todas las $latex c\_i$ son iguales, entonces nuestro árbol está balanceado. De lo contrario, debemos restar aún más para poder balancearlo. Sin embargo, también necesitamos que cada $latex h\_i$ continúe estando balanceado. La única manera que le podemos restar peso a $latex h\_i$ sería restarle la misma cantidad de peso a cada una de sus hojas. Entonces, a cada $latex h\_i$ sólo podemos restarle peso en múltiplos de $latex b\_i$. Como queremos maximizar el peso del árbol resultante, necesitamos encontrar el número más grande $latex x$ tal que a todos los $latex c\_i$ les podamos restar un múltiplo de su respectivo $latex b\_i$ para obtener $latex x$. Notemos también que $latex c\_i$ es un múltiplo de $latex b\_i$ porque los nodos internos del árbol no tienen peso. Si $latex m$ es el mínimo común múltiplo de todos los $latex b\_i$, entonces $latex x$ también es un múltiplo de $latex m$. Entonces, el máximo $latex x$ posible es igual al múltiplo de $latex m$ más grande que sea menor o igual a todos los $latex c\_i$. Por lo tanto, el valor máximo obtenible del árbol completo es igual a $latex kx$. Por último, si tuviéramos que restarle más peso a este árbol pero mantenerlo balanceado, es evidente que lo menos que podemos restar para mantenerlo balanceado es $latex km$, y si seguimos restando $latex km$ continuará balanceado.

De esta observación podemos obtener la solución para cualquier árbol. Reusando la notación del párrafo anterior, $latex k$ es la cantidad de hijos de la raíz, $latex h\_i$ el subárbol del $latex i$ésimo hijo, y $latex c\_i$ el peso del árbol obtenido de realizar recursivamente el procedimiento de éste párrafo a $latex h\_i$ (o el del anterior si $latex h\_i$ tiene 2 niveles). Ahora $latex b\_i$ es igual a lo mínimo que le podemos restar a $latex h\_i$ y que continúe balanceado. El análisis del párrafo anterior también es correcto para la nueva definición de $latex b\_i$ y $latex c\_i$.

El código siguiente implementa esta solución:

{{< gist OlimpiadaMexicanadeInformatica 8498208 >}}