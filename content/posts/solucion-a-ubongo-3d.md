---
title: 'Solución a "Ubongo 3D"'
author: 'Freddy'
author_email: 'me@freddy.mx'
date: Sat, 14 Sep 2013 05:04:59 +0000
draft: false
tags: ['Solution', 'Etapa 1', 'Examen 8', 'macs', 'preselectivo', 'solución', 'Soluciones Preselectivo 2014']
---

**Concurso:** [Preselectivo para la IOI 2014, Etapa 1, Problemset 8](https://omegaup.com/arena/problem/ubongo-3d) **Autor:** Miguel Covarrubias **Fuente:** Miguel Covarrubias

La solución pone piezas de manera recursiva mientras quepan en el tablero y no se empalmen.

```cpp
resuelve(pieza)
    si pieza > P
        regresa “Si”
    para cada rotación de la pieza
        para cada casilla g del tablero
            para cada cubo c de la pieza
                si al poner c sobre g, la pieza queda dentro de los primeros 2 niveles del tablero y no se empalma con otra pieza ya puesta entonces
                    marca las posiciones de los cubos de la pieza como ocupados
                    resuelve(pieza + 1)
                    desmarca los cubos de la pieza
```

Para rotar una pieza se puede rotar por $latex 0^o$, $latex 90^o$, $latex 180^o$ o $latex 270^o$ alrededor de cada eje. El número de operaciones es aproximadamente (número de rotaciones \* número de casillas del tablero \* número de cubos de una pieza)$latex ^3 \\le (24 \* 7 \* 5)^3 < 600,000,000$. En los casos de prueba y en el juego todas las soluciones tocan la base del tablero, si no fuera así, solo hay que duplicar el 7 a 14. Para checar si una pieza se puede poner en cierta posición se pueden usar mascaras de bits para los niveles del tablero y para las posiciones ocupadas. Para poner la última pieza se puede comparar todas las rotaciones de los cubos no ocupados contra la última pieza y la complejidad cubica de la solución se reduce a cuadrática.

{{< gist OlimpiadaMexicanadeInformatica 6558928 >}}