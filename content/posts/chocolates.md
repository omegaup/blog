---
title: 'Solución a "Los Chocolates del Agente Nieves"'
author: 'darknut'
author_email: 'golden.darknut@gmail.com'
date: Wed, 05 Aug 2015 07:02:46 +0000
draft: false
tags: ['Solution', 'dinámica', 'felix', 'Material de estudio', 'preselectivo', 'solución']
---

Problema: [Los Chocolates del Agente Nieves](https://omegaup.com/arena/problem/chocolates)

En este problema tenemos un tubo de chocolates los cuales se van a vender uno cada día, pudiendo vender únicamente los que están en ese momento en los extremos. El precio por vender un chocolate es igual al precio base de chocolate multiplicado por el número de días que se han vendido chocolates (empezando en 1).

El objetivo es encontrar la mayor ganancia posible al vender todos los chocolates.

Si lo quisiéramos resolver como una búsqueda, ¿qué tendríamos que considerar? En una búsqueda, nos importa obtener dos cosas, el espacio de búsqueda (es decir, cómo estará representado nuestro estado y qué valores puede tener), y las operaciones en nuestra búsqueda.

En cuanto a nuestros estados en la búsqueda, nos importa saber qué chocolates aún tenemos disponibles y cuántos días han pasado. Podríamos empezar teniendo N valores booleanos por cada chocolate y un número para saber cuántos días han pasado, por ejemplo, si tenemos 3 chocolates y aún no vendemos nada, tendríamos el estado (1, 1, 1, 1), si ya vendimos el primer chocolate, tendríamos (0, 1, 1, 2), si vendimos el tercer chocolate tendríamos (1, 1, 0, 2) y si vendemos los chocolates 1 y 2, tendríamos (0, 0, 1, 3). Sin embargo, esta representación es un poco inútil, ya que en el peor de los casos, tendríamos 1000 chocolates, lo cual hace un estado de 1000 posibles valores.

Podemos mejorar esto solo guardando únicamente los índices a los extremos del tubo, ya que ya sabemos que aún tenemos todos los chocolates entre estos dos valores. Eso transforma los estados anteriores a los siguientes estados respectivamente: (1, 3, 1), (2, 3, 2), (1, 2, 2). y (3, 3, 3). Esto vuelve al estado muchísimo más manejable, pues cada valor puede valer únicamente entre 1 y 1000.

Ya que tenemos nuestro estado, definimos las operaciones que hay que hacer para ir entre estado y estado, y estas operaciones son únicamente 2, vender el chocolate de la izquierda, o vender el chocolate de la derecha, si estamos en el estado (1, 3, 1) y vendemos el de la izquierda, nos lleva al estado (2, 3, 2), y si vendemos el de la derecha, nos lleva al estado (1, 2, 2). Podemos continuar estas instrucciones recursivamente sobre los estados que resulta y generar un árbol de búsqueda:

![](http://i.imgur.com/SXmtBPI.png)

Una vez teniendo el árbol de búsqueda, podemos proceder a darle valor a cada uno de los nodos. Del nodo inicial (1, 3, 1), si decides vender el chocolate de la izquierda, obtendrás una ganancia igual a lo que te de el nodo (2, 3, 2) más el precio del chocolate 1 multiplicado por el número de días, que en este caso es 1, y si decides vender el chocolate de la derecha, la ganancia será lo que de el nodo (1, 2, 2) más el precio del chocolate 3 (múltiplicado por 1). De las dos opciones, tomaremos el máximo.

Llenemos ahora el resto del árbol de búsqueda con estos datos:

![](http://i.imgur.com/HseaiuL.png)

De aquí podemos ver dos cosas, la primera es que los nodos de hasta abajo, que son nuestros nodos hoja, tienen el mismo valor en el chocolate izquierdo como en el derecho, por lo que el valor máximo que podemos obtener de ellos es el precio de ese único chocolate por el número de días que llevamos. Y la segunda cosa es que tenemos nodos repetidos, por lo que cuando hagamos nuestra búsqueda, necesitamos guardar cálculos que ya hayamos hecho para no calcular un mismo estado más de una vez.

Nuestro árbol de búsqueda ya está terminado, así que es hora de convertirlo a una función matemática. Nuestra función recibe como entrada un estado, en este caso el chocolate más a la izquierda que nos queda, el más a la derecha y el nivel en el que estamos, y dado lo que aprendimos de nuestro árbol de búsqueda, regresará el siguiente valor:

![](http://i.imgur.com/s3XYfw9.png)

Con esto, y considerando que debemos evitar repetir valores duplicados, es más que suficiente para resolver el problema con el método que más te guste, ya sea dinámica o memorización, aunque hay un pequeño problema para guardar los valores visitados.

Vamos a necesitar un arreglo de 1000 x 1000 x 1000 si es que queremos guardar un arreglo que se identifique de esta forma:

arreglo\[izquierda\]\[derecha\]\[nivel\]

Y esto es mucho más de lo que cabe en memoria, por lo que tenemos que encontrar una forma de reducir la memoria que necesitamos.

Lo que nos tenemos que dar cuenta es que la variable nivel es innecesaria, pues puede calcularse utilizando el número de chocolates que nos quedan en el tubo y el número de chocolates que teníamos originalmente:

nivel = total - chocolates\_en\_el\_tubo + 1

Y para calcular el número de chocolates que nos quedan en el tubo solo se necesitan el índice del chocolate más a la izquierda, y más a la derecha, que ya tenemos en nuestro estado.

chocolates\_en\_el\_tubo = derecha - izquierda + 1

Despejando:

nivel = total - derecha + izquierda \- 1 + 1

nivel = total - derecha + izquierda

De esta forma, podemos eliminar el nivel de todos nuestros estados y cambiar el valor de nivel de todas las fórmulas por el valor de arriba. Esto simplifica nuestro arreglo de visitados de 1000 x 1000 x 1000 a un arreglo de tan solo 1000 x 1000, lo cuál es suficiente en tiempo y memoria.