---
title: 'Solución a Las Cartas del Dr. Lira'
author: 'joemmanuel'
author_email: 'joemmanuel@gmail.com'
date: Mon, 29 Jul 2013 15:26:08 +0000
draft: false
tags: ['Solution', 'Etapa 1', 'Examen 1', 'Soluciones Preselectivo 2014']
aliases: ['/solucion-a-las-cartas-del-dr-lira']
---

**Concurso:** [Preselectivo para la IOI 2014, Etapa 1, Problemset 1](https://omegaup.com/arena/IOI2014E1P1#problems/CartasDrLira) **Autor:** [Joemmanuel Ponce Galindo](http://www.linkedin.com/in/joemmanuel/)  **Fuente**: Topcoder

Básicamente lo que nos pide el problema es encontrar el número de cartas que son distintas entre la configuración que es dada como entrada y una configuración donde las cartas estén alternadas.

Cómo se explica en el problema, sólo hay 2 estados posibles en los que una carta puede estar: negro (B) y blanco (W). En otras palabras, la observación clave para resolver el problema es darse cuenta que sólo existen 2 configuraciones que cumplen con las reglas que necesita Dr. Lira: Una configuración donde la primer carta es W, la siguiente B, la siguiente W y así sucesivamente. La otra configuración posible es donde las cartas empiezan con B, forzando la siguiente carta a ser W y esta a su vez forzando la siguiente carta a ser B.

Contar el número de caracteres diferentes entre una cadena y otra sólo requiere de un ciclo, por lo que la complejidad es lineal con respecto al tamaño de la cadena. Lo único que tenemos que hacer es entonces comparar la cadena dada como entrada con las configuraciones BWBW.. y WBWB..., contar el número de diferencias y dar como salida el mínimo de estos números.

{{< gist OlimpiadaMexicanadeInformatica 6559228 >}}