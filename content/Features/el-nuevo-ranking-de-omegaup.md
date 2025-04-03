---
title: 'El nuevo ranking de omegaUp'
author: 'joemmanuel'
author_email: 'joemmanuel@gmail.com'
date: Thu, 12 Jun 2014 14:42:18 +0000
draft: false
tags: ['Features', 'Ranking', 'Internals']
math: true
aliases: ['/el-nuevo-ranking-de-omegaup']
---

Con [este commit](https://github.com/omegaup/omegaup/commit/132e9c4614a7a4939156a942810559bf8c57f1a8) hemos introducido un cambio significativo en la forma de calcular el [ranking general](https://omegaup.com/rank.php) de omegaUp. Ahora no sólo es importante cuántos problemas ha resuelto un usuario sino que también estamos incluyendo la dificultad de cada uno de esos problemas. La dificultad es inversamente proporcional a la cantidad de soluciones completas (AC) que tiene ese problema.

Para ser más precisos, estamos definiendo los puntos que da un problema así: 

$latex P\_i = \\frac{100}{log\_2(N+1)}$, 

donde $latex N$ representa la cantidad de ACs que tiene un problema. 

[Entre más ACs tenga un problema, menos puntos va a valer](http://fooplot.com/#W3sidHlwZSI6MCwiZXEiOiIxMDAvKGxvZyh4KzEpL2xvZygyKSkiLCJjb2xvciI6IiMwMDAwMDAifSx7InR5cGUiOjEwMDAsIndpbmRvdyI6WyItOC4xNTk5OTk5OTk5OTk5ODIiLCIxOTkuODQiLCItOC43OTk5OTk5OTk5OTk5OTciLCIxMTkuMTk5OTk5OTk5OTk5OTkiXX1d). Sólo estamos contando a lo más 1 AC por usuario para evitar que las soluciones de una misma persona afecten artificialmente los puntos de score del problema.

[![](/images/Screen-Shot-2014-06-12-at-7.44.06-AM.png "Screen Shot 2014-06-12 at 7.44.06 AM")](/images/Screen-Shot-2014-06-12-at-7.44.06-AM.png)

El score que usamos en el ranking esta dado por la suma de los puntos de todos los problemas que un usuario ha resuelto con AC.

[![](/images/Screen-Shot-2014-06-12-at-7.18.16-AM.png "Scoreboard del 6-12")](/images/Screen-Shot-2014-06-12-at-7.18.16-AM.png)

Este nuevo sistema implica que los scores ahora son dinámicos: con cada problema que un usuario resuelva se va a afectar el score de otras personas que ya hayan resuelto el mismo problema anteriormente. La única manera de subir el score es resolviendo más problemas ya que, con el tiempo, el valor que otorga cada problema va a decaer.

También agregamos una columna en la [lista de problemas disponibles](https://omegaup.com/problem/), **Puntos para ranking**, que ayuda a los usuarios a saber qué problemas atacar y cuánto valen en este nuevo sistema. Es importante notar que el valor que se muestra es el actual: en el momento que resuelvas un problema, los puntos que otorga van a cambiar.

[![](/images/Screen-Shot-2014-06-12-at-7.36.05-AM.png "Screen Shot 2014-06-12 at 7.36.05 AM")](/images/Screen-Shot-2014-06-12-at-7.36.05-AM.png)

Qué te parece el nuevo sistema? Subiste o bajaste en el ranking? Déjanos tus dudas y sugerencias en los comentarios.