---
title: 'Solución a "Mario Reloaded"'
author: 'Lira'
author_email: 'elira@elira.me'
date: Mon, 07 Jan 2013 16:08:32 +0000
draft: false
tags: ['Solution', 'Etapa 1', 'Examen 8', 'Pavel Herrera', 'preselectivo', 'Soluciones Preselectivo 2013']
---

**Concurso:** [Preselectivo para la IOI 2013, Etapa 1, Examen 8](https://omegaup.com/arena/IOI2013E1P8) **Autor: **[Pavel Herrera Dominguez](mailto:paspartu@gmail.com))

Observaciones
-------------

Lo primero es ver como se modelan los estados del problema sin pensar en que Mario puede tomar los atajos, únicamente pensar en las llaves, claramente existen $latex n\\times2^m$ estados, pues no importa el orden en que se toman las llaves solo las llaves que se tienen al llegar a cada puerta. A partir de aquí nos referiremos como estado a la puerta y las llaves que trae Mario.

La segunda observación es ver como afecta llegar a una puerta con cierto juego de llaves, osea a cada estado. Cada vez que visitamos un estado todos los estados ya visitados que tienen el mismo juego de llaves se actualiza instantáneamente. Esto se puede entender como si únicamente el juego de llaves definiera el estado, lo que nos lleva a pensar que el problema es saber que puertas pertenecen a qué juego de llaves.

De la observación anterior podemos pensar que si mantenemos una lista de puertas ya visitadas para cada juego de llaves, cuando algún estado (puerta, juego de llaves) se visita con un menor tiempo, todas las puertas alcanzadas con ese juego de llaves deben ser actualizadas y sus respectivos vecinos.

Idea
----

La idea es hacer una especie de búsqueda en amplitud la cual tome en cuenta las observaciones anteriores. Esto es una búsqueda que visite los estados (puerta, llave) y conserve una lista de las puertas alcanzables con cada juego de llaves.

Implementacion
--------------

{{< gist OlimpiadaMexicanadeInformatica 6559138 >}}

Tarea
-----

Pensar si es posible hacer la búsqueda sin usar los estados (puerta, juego de llaves).