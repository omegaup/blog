---
title: 'Solución a "Problema"'
author: 'Lira'
author_email: 'elira@elira.me'
date: Mon, 07 Jan 2013 16:34:20 +0000
draft: false
tags: ['Solution', 'Etapa 1', 'Examen 10', 'Hugo Dueñas', 'preselectivo', 'solución', 'Soluciones Preselectivo 2013']
math: true
---

**Concurso:** [Preselectivo para la IOI 2013, Etapa 1, Examen 10](https://omegaup.com/arena/IOI2013E1P10) **Autor: **[Hugo Dueñas](mailto:hugochiquito.cpp@gmail.com)

Primero, dado una secuencia $ A$ denotaremos por $ s(A)$ a la suma de los elementos de A. Entonces podemos replantear el problema como: Dada una secuencia $ S$ debemos de econtrar una subsecuencia $ A$ de $ S$ tal que $ s(A) - (s(S) - s(A))$ sea la minima posible.

Ahora, como $ s(A) - (s(S) - s(A)) = 2 \\times s(A) - s(S)$, entonces tenemos que minimizar $ 2 \\times s(A) - s(S)$ que es lo mismo que minimizar $ s(A) - s(S)/2$. O sea, debemos de encontrar una subsecuencia $ A$ cuya suma esté lo más cercana a la mitad de la suma de $ S$, en particular podemos restringir nuestra búsqueda a las subsecuencias cuya suma sea menor o igual a $ s(S)/2$.

Se plantea para este problema una solución de tipo _Programación Dinámcia_ que corre sobre los elementos de la secuencia $ S$ y considera todas las posibles diferentes sumas de subsecuencias cuyos elementos tienen índices menores o iguales al actual y cuya suma no excede $ s(S)/2$. Se tendrán entonces $ n \\times s(S)/2$ posibles estados y cada uno podrá ser procesado en tiempo constante ya que solo hay dos trancisiones posibles para cada estado: Se toma el elemento actual dentro de la subsecuencia o no. Por lo tanto la solución tendrá una complejidad temporal de $ O (n \\times s(S))$.

A continación se lista una implementación en C++ de la solución:

{{< gist OlimpiadaMexicanadeInformatica 6559155 >}}