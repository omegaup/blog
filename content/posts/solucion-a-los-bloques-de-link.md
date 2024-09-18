---
title: 'Solución a "Los Bloques de Link"'
author: 'Lira'
author_email: 'elira@elira.me'
date: Mon, 07 Jan 2013 16:54:06 +0000
draft: false
tags: ['Solution', 'Alain Acevedo', 'Etapa 1', 'Examen 8', 'preselectivo', 'solución', 'Soluciones Preselectivo 2013']
---

**Concurso:** [Preselectivo para la IOI 2013, Etapa 1, Examen 8](https://omegaup.com/arena/IOI2013E1P8) **Autor: **[Alain Acevedo Mejía](mailto:alainacme@gmail.com)

Es claro que no es posible probar todas las sucesiones posibles de movimientos de los bloques para encontrar la solución (a excepción de casos muy simples). El número de tales sucesiones puede ser infinito en caso de que se puedan formar ciclos de movimientos (lo cual sucede en muchos de lo casos de prueba), y aún en casos donde el número sea finito puede suceder que no se tenga tiempo para probarlos todos.

Una primera observación crucial es que, en el estado del mapa, solo nos interesa saber donde están los bloques de hielo en cada paso, es decir, su ubicación es lo que determina lo que nos interesa del estado. No nos interesan los pasos previos que los llevaron a su posición, solo que sea el número mínimo posible. Tenemos un problema que puede ser resuelto realizando una búsqueda en amplitud.

¿Cuántos estados es posible alcanzar? El mapa es a lo más de 40x40 espacios y las orillas siempre están bloqueadas, así que realmente tenemos 38x38=1444 espacios a los que quizá es posible llevar a los bloques. Tenemos dos bloques de hielo, así que hay (1444x1443)/2=1,041,846 formas de colocarlos en el mapa (hemos considerado aquí ya el hecho de que son indistinguibles). Para fines de la búsqueda el número que hemos calculado es en realidad una cota superior muy mala (mala en el sentido de que la cota superior mínima es muy inferior, es decir, calculamos “de más”), pues por la forma en que se mueven los bloques es claro que aún en el peor de los casos posibles la cantidad de estados a los que se puede acceder es mucho menor (¿cuál es el peor de los casos?). Es posible entonces emplear una búsqueda en amplitud común para resolver el problema, el espacio de búsqueda no es muy grande y es claro que podemos recorrerlo por completo.

Para representar los estados requerimos tener la posición de ambos bloques, y nada más. Podemos emplear una arreglo de bool's (boolean's en pascal) de cuatro dimensiones para marcar los estados a los que se ha accedido. Para la cola, en el código que se anexa más abajo, empleamos un arreglo de dos dimensiones (una matriz) donde además de guardar la posición de los bloques de los estados guardamos la cantidad de movimientos realizados para llegar a cada estado. Para ver a que estados podemos llegar desde un estado dado basta con ver en que direcciones es posible mover los bloques y a qué posición llegarán.

Para optimizar la búsqueda podemos hacer dos observaciones. La primera es que con nuestra representación de los estados podríamos llegar dos veces al mismo estado, ya que los dos bloques de hielo son para nuestros fines iguales. En el código de abajo es por ello que al llegar a un estado nuevo se marcan dos valores en el arreglo de bools como verdaderos, pues ambos representan en realidad el mismo estado.

Otra observación es que para averiguar eficientemente a que estados se puede llegar desde un estado dado podemos precalcular, antes de realizar la búsqueda, para cada espacio vacío o con bloque de hielo, cuál es la posición del espacio bloqueado (con numeral # o con el botón A) más cercano en cada dirección. Así solo habrá que comparar esa posición con la del otro bloque de hielo para ver a dónde llegará el bloque tras su movimiento. Esto puede mejorar el tiempo de ejecución para un caso dado, aunque no siempre es así. En este problema para obtener los 100 puntos no hacen falta optimizaciones de este tipo, aunque es bueno tener este tipo de ideas en mente para problemas más complejos.

El siguiente código resuelve el problema:

{{< gist OlimpiadaMexicanadeInformatica 6559163 >}}