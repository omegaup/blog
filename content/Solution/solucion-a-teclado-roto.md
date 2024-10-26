---
title: 'Solución a "Teclado Roto"'
author: 'Lira'
author_email: 'elira@elira.me'
date: Sun, 28 Oct 2012 01:31:45 +0000
draft: false
tags: ['Solution', 'Etapa 1', 'Examen 2', 'Soluciones Preselectivo 2013']
---

**Concurso:** [Preselectivo para la IOI 2013, Etapa 1, Examen 2](https://omegaup.com/arena/IOI2013E1P2)**[ ](https://omegaup.com/arena/IOI2013E1P2) Autor: **[Jorge Alberto González Martínez](#)

Los temas para el examen donde apareció este problema eran pilas, colas y búsqueda binaria. Después de haber estudiado los temas, es buena idea combinar la teoría aprendida.

El problema del teclado roto describe una serie de operaciones en las que es necesaria una estructura en la que sea posible agregar elementos por ambos lados (izquierda y derecha). La descripción del problema muestra las restricciones, que no superan los 100, 000 elementos, por lo que es posible hacer un arreglo estático de caracteres de ese tamaño.

En el caso de mi solución, para que sea más clara la inserción, también utilizo memoria auxiliar para guardar las palabras que se van a insertar en la estructura de datos.

En el código que se muestra abajo se describe la forma en la que se implementa y opera la estructura mencionada anteriormente:

{{< gist OlimpiadaMexicanadeInformatica 6559109 >}}