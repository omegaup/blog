---
title: 'Invasion Zombie'
author: 'Rafael'
author_email: 'rafaelrendonpablo@gmail.com'
date: Thu, 12 Nov 2015 17:06:59 +0000
draft: false
tags: ['Solution', 'búsqueda binaria', 'geometría', 'Material de estudio']
math: true
---

Hola!, este es mi primer post en Omegaup y voy a describir mi solución para el problema [Invasion zombie](https://omegaup.com/arena/IOI2014E1P3/practice/#problems/invasionzombie). Hace un año encontré este problema, me pareció interesante y logre resolverlo, aunque algo tricky. Hace unos días me tope con este problema nuevamente y lo resolví por segunda ocasión, pero con una solución más simple, al menos eso creo.

Primer solución
---------------

La idea principal tanto en la primera como en la segunda solución es diseñar una función $latex f(d)$ que nos retorne el número de colonias infectadas después de $latex d$ días, nos interesa el mínimo valor de $latex d$ tal que el número de colonias infectadas sea mayor o igual a $latex C$. Una propiedad importante es la siguiente, $latex f(d)$ nunca decrece, es decir $latex f(d) <= f(d+1)$. Esta propiedad nos permite utilizar búsqueda binaria para encontrar las respuesta en $latex O(\\lg\_{2}(n))$. Diseñar una función que determine el número de colonias infectadas, dependiendo del background de cada uno, es la parte interesante, y es donde difieren las dos versiones, bueno, un poco. Este es el código de la primer versión, no voy a entrar en detalles porque ni yo me acuerdo bien que trucos aplique, pero la idea es parecida a la de la de la segunda versión, lo que cambia es la estrategia.

{{< gist rendon 4298449a291244690253 >}}

Segunda versión
---------------

Bueno, empecemos, trascurridos $latex d$ días, ¿cuántas colonias han sido infectadas? Simulemos la invasión y veamos si podemos encontrar un patrón. [![zombies-pattern](/images/zombies-pattern.png)](/images/zombies-pattern.png) No es complicado llegar a la siguiente fórmula: $latex f(d) = d^{2} + (d+1)^{2}$ Si el espacio de la ciudad fuese ilimitado nuestra función de verificación sería algo parecido a:

{{< gist rendon 1308e65b73b82d452bba >}}

Sin embargo, el espacio de la ciudad es limitado y habrá casos como los siguientes: [![zombies-sc1](/images/zombies-sc1.png)](/images/zombies-sc1.png) [![zombies-sc2](/images/zombies-sc2.png)](/images/zombies-sc2.png) Entonces nuestro objetivo es encontrar el área delimitada por la ciudad (un cuadrado de N \* N unidades), lo cual se pone un poco tricky. La siguiente imagen nos ayudará a entender el código de la solución sin entrar en tantas explicaciones. [![zombies-solution](/images/zombies-solution.png)](/images/zombies-solution.png) Es decir, el área total menos el área de los triángulos superior, inferior, izquierdo y derecho. Obsérvese que los triángulos pueden traslaparse y por lo tango estaríamos restando esas áreas 2 veces, por ello tenemos que calcular las áreas de traslape (_nw_, _ne_, _se_ y _sw_ en la imagen) y regresar lo a la suma total. Lo que sigue es la implementación:

{{< gist rendon b65689354d202e562fe7 >}}

Espero que les sea útil, dudas, comentarios o correcciones son bienvenidas.
