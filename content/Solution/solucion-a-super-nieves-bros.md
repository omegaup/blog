---
title: 'Solución a "Super Nieves Bros"'
author: 'joemmanuel'
author_email: 'joemmanuel@gmail.com'
date: Mon, 30 Sep 2013 15:54:06 +0000
draft: false
tags: ['Solution', 'Examen 6']
---

**Concurso: **[Preselectivo para la IOI 2014, Etapa 1, Problemset 6](https://omegaup.com/arena/IOI2014E1P6) **Fuente**: Topcoder

Este problema es una adaptación del problema [ArcadeManao](http://community.topcoder.com/stat?c=problem_statement&pm=12504&rd=15496) que apareció en el SRM 576 (Abril 2013) de Topcoder. Los detalles de la solución explicada la pueden en el respectivo [Match Summary](http://apps.topcoder.com/wiki/display/tc/SRM+576).

La idea general de este problema es muy sencilla: En base a los límites, la primera observación es que el mapa no es muy grande y en el peor caso, la escalera más alta es de tamaño 50. Hay que notar que no nos piden la ruta más corta para capturar la moneda, más bien cuál es el menor tamaño con el que podemos llegar.

La idea principal es ir probando los tamaños de escalera, empezando desde 0 hasta 50, y para cada tamaño probar si es posible llegar a la moneda o no. Si empezamos probando los tamaños de menor a mayor, la primer escalera que lo logré será el resultado.

Para probar que se puede llegar a la moneda, se puede usar búsqueda en amplitud o búsqueda en profundidad. Dado que el tamaño del mapa es relativamente pequeño, es posible usar búsqueda en profundidad y pararla en cuanto "pisemos" la moneda (de nuevo, no nos interesa saber si la ruta que la búsqueda siguió para dar con la moneda fue la menor de todas las posibles, con llegar a ella basta).

Este par de observaciones son suficiente para resolver el problema. Si el lector quiere más reto, hay otra observación que permitiría reducir el número de búsquedas que hay que hacer de 50 a 6...

Esta es la solución de [charlyhlms](https://omegaup.com/profile/charlyhlms) usando búsqueda en profundidad.

{{< gist joemmanuel 6765773 >}}

Esta es la solución de [spleensarethebest](https://omegaup.com/profile/spleensarethebest) usando búsqueda en amplitud y optimizando la cantidad de pruebas de tamaños de escaleras que hay que hacer.

{{< gist joemmanuel 6765853 >}}