---
title: 'Solución a "Cambio"'
author: 'Lira'
author_email: 'elira@elira.me'
date: Tue, 08 Jan 2013 17:18:25 +0000
draft: false
tags: ['Solution', 'Enrique Lira', 'Etapa 1', 'Examen 7', 'preselectivo', 'solución', 'Soluciones Preselectivo 2013']
---

**Concurso:** [Preselectivo para la IOI 2013, Etapa 1, Examen 7](https://omegaup.com/arena/IOI2013E1P7) **Autor: **[Enrique Lira Vargas](mailto:elira@elira.me)

Lo importante de este problema es notar como se puede usar un backtracking para contar cosas. En este caso lo que se debía contar era la cantidad de formas de llegar a una cantidad sumando una o más veces una serie de cantidades dadas.

Solución de 30, 50 puntos
-------------------------

Generar todas las combinaciones que sumen la cantidad C pedida. Para hacer esto se puede hacer con una búsqueda en profundidad de manera ordenada de la misma forma que se calculan permutaciones pero cuidando que la suma no sobrepase el valor C deseado. Esto se puede considerar una búsqueda podada.

Solución de 100 puntos
----------------------

Consideremos la solución anterior y tratemos de calcularlo de abajo hacia arriba, habría que crear una función que nos dijera para una cantidad dada y un set de monedas que se pueden usar (para no repetir) nos diga cuantas formas distintas hay de completar dicha cantidad. Si se logra construir dicha función la solución al problema es simple puesto que se reduce a llamar dicha función con la cantidad que nos piden y el set completo de monedas. Lo interesante radica en cómo se compone dicha función, suponiendo que la función funciona hay que tratar de construirla, primero hay que considerar los casos especiales, si la cantidad es cero significa que no hay que hacer nada y entonces hay una forma de lograrlo (es una combinación válida), si la cantidad es mayor a cero hay que sumar las combinaciones de tomar una moneda de la primera denominación disponible con las de dejar de tomar monedas de dicha denominación.

*   Para calcular las combinaciones de tomar una moneda de dicha denominación se puede usar la función a partir de la cantidad restante (la cantidad buscada menos la denominación de la moneda) y el mismo set de monedas.
    
*   Para calcular las combinaciones de dejar de tomar monedas de cierta denominación de igual forma se puede usar la función con la misma cantidad pero con un set de monedas que no incluya la denominación que decidimos dejar de tomar.
    

Si se toma la moneda sin considerar si la denominación es más grande que la cantidad entonces existe el caso donde la cantidad es negativa y en ese caso la respuesta debiera ser cero puesto que es una combinación no válida.

De igual forma si el set de denominaciones disponibles está vacío significa que ya no hay más denominaciones para probar y por lo tanto no hay ninguna forma de lograrlo.

  

Como podemos notar dicha función es recursiva y se llama a si misma hasta que la cantidad se vuelve cero, negativa y/o el set de denominaciones queda vació, y si lo analizamos un poco podemos darnos cuenta de que funciona. La forma simple de saber que set de monedas es usable es guardar el índice de la primera moneda usable y eliminarlas en orden. Hay que notar que hasta el momento no hemos mejorado en nada la solución anterior, y la complejidad de esto es similar a la de nuestra idea anterior.

Lo que hay que notar es que la cantidad no tendrá más de 10,000 valores distintos y que nunca habrá más de 100 sets distintos, por lo tanto dicha función solo se puede mandar a llamar 1,000,000 de veces con parámetros distintos. Sin embargo sabemos que la cantidad de combinaciones puede llegar a ser mucho mayor. Entonces ¿Qué sucede?, pues es sencillo darse cuenta que dicha función se mandará a llamar más de una vez con los mismos parámetros y en todos esos casos siempre deberá entregar la misma solución, es por esto que podemos guardar las respuestas para cada uno de los casos en un array y así nunca tener que calcularlos más de una vez, esto hace que nuestro programa pueda correr en tiempo.

_El asunto de los módulos creo que es algo que debiesen saber sin embargo les digo que el modulo se puede aplicar al sumar el tomar y el no tomar, puesto que (A + B) modulo X es igual a (A modulo X + B modulo X ) modulo X._

{{< gist OlimpiadaMexicanadeInformatica 6559217 >}}