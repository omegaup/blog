---
title: 'Solución a "Juego Lento"'
author: 'Lira'
author_email: 'elira@elira.me'
date: Fri, 12 Oct 2012 21:43:58 +0000
draft: false
tags: ['Solution', 'Etapa 1', 'Ethan Jiménez', 'Examen 1', 'Soluciones Preselectivo 2013']
aliases: ['/juego-lento-ethan-jimenez']
---

**Concurso:[ ](https://omegaup.com/arena/IOI2013E1P1)**[Preselectivo para la IOI 2013, Etapa 1, Examen 1](https://omegaup.com/arena/IOI2013E1P1)  
**Autor:** [Ethan Jimenez](http://www.codechef.com/users/ethanjimenez)

Empecemos analizando el caso en que solo jugamos con un montón de fichas, dada la restricción de tomar únicamente una sola ficha el juego se vuelve predecible ya que no hay más opción que tomar una ficha de ese montón. Si el montón tiene una sola ficha el jugador con el primer turno pierde, si hay dos fichas el jugador con el primer turno gana, si hay tres fichas el jugador con el primer turno pierde, y así alternadamente, podemos entonces deducir que si hay un número impar de fichas en el montón, el jugador con el primer turno perderá, por el otro lado, si el montón tiene un número par de fichas ganará la partida.

La pregunta clave para este problema es, ¿realmente hay diferencia entre tomar una ficha de un montón y tomar una ficha de otro montón? Aumentemos la cantidad de montones en el juego, digamos que ahora tenemos dos montones de fichas, ambos montones tienen una sola ficha, el jugador con el primer turno ganará, detente por un momento a experimentar qué sucede si aumentamos la cantidad de fichas en un montón, en el otro y en ambos montones, teniendo en mente la pregunta anterior.

Después de probar con diferentes configuraciones de juego podemos decir que la respuesta a la pregunta es no, tomar primero una ficha de un montón no es diferente a haberla tomado de cualquier otro montón, con lo que podemos concluir que, si tenemos dos montones, el primero con _**a1**_ fichas y el segundo con_**a2**_fichas, este juego es equivalente a tener un solo montón con _**a1+a2**_fichas, una vez establecido podemos volver a nuestro análisis inicial y calcular quién ganará.

De manera análoga deducimos que si tenemos _**N**_montones de fichas y elegimos _**K**_de ellos, podemos reducir la configuración [herpes transmission](http://maileswaste.com/category/causes/) de esta partida a un juego con solo un montón de _**k1+k2+...+kN**_fichas, donde kies el número de fichas en el montón elegido _**i**_. Una vez que sabemos lo anterior debemos darnos cuenta que para ganar tenemos que elegir _**K**_ de los N montones cuya suma total sea un número impar.

Para asegurarnos que un conjunto de montones tiene un número impar de fichas debemos considerar lo siguiente, un número impar más un par da un número impar, un número impar sumado a un impar da un número par y un número par más un par da otro número par. Dado lo anterior podemos definir una regla para tener una suma total impar, debe existir una cantidad impar de montones con un número de fichas impar, si le agregamos cualquier cantidad montones con número de fichas par no se modifica la condición de tener un total impar.

En conclusión, es posible ganar el juego cuando existe más de un montón con número impar de fichas, si hay una cantidad impar de montones impares ya se cumple la condición deseada, pero si hay una cantidad par de montones impares debemos quitar uno para cumplirla, para obtener el juego con la mayor cantidad de fichas el montón que quitemos debe ser el que tenga menos fichas, nota que, como mencioné antes, agregar montones pares no afecta la condición de victoria, por lo que para aumentar la cantidad de fichas en el juego se deben agregar todos ellos.