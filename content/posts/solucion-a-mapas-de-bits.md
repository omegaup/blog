---
title: 'Solución a "Mapas de bits"'
author: 'Freddy'
author_email: 'me@freddy.mx'
date: Sun, 06 Oct 2013 22:56:54 +0000
draft: false
tags: ['Solution', 'Etapa 1', 'Examen 12', 'jorge', 'preselectivo', 'solución', 'Soluciones Preselectivo 2013', 'yorch']
---

**Concurso:** [Preselectivo para la IOI 2014, Etapa 1, Problemset 12](https://omegaup.com/arena/IOI2014E1P12/#problems/Mapas-de-bits) **Autor:** Jorge Alberto González Martínez **Fuente**: Jorge Alberto González Martínez

En el problema se describen dos formas de representar un mapa de bits.

La forma bidimensional es simplemente utilizar una matriz para representar los bits. La forma por descomposición consiste en agrupar los bits similares y solo escribir el valor de los bits similares. En caso de que no sean similares todos los bits en un mapa de bits dado, se procede a dividir en cuatro secciones, imprimir la letra D y procesar cada uno de los cuartos de la misma manera, tal como se lee en la descripción del problema.

La solución a este problema consistía en programar el método descrito. Este método inherentemente está basado en la técnica de divide y vencerás.

A continuación, un pseudo-código que muestra la forma de llevar a cabo la transformación de un mapa de bits bidimensional a la forma reducida:

```cpp
 ReduceMapa(mapaDeBits)
Si todos los elementos en mapaDeBits son iguales
    Imprime el valor y termina
Si no
    Imprime D
    ReduceMapa(mapaDeBits.superiorIzquierdo)
    ReduceMapa(mapaDeBits.superiorDerecho)
    ReduceMapa(mapaDeBits.inferiorIzquierdo)
    ReduceMapa(mapaDeBits.inferiorDerecho) 
```

El método para hacer la transformación inversa es muy parecido, sólo que para imprimir la equivalencia hay que comenzar con un mapa de bits bidimensional que nos sirva de variable auxiliar para hacer la conversión. Esta variable auxiliar se puede declarar de manera global y, cuando el método recursivo termine, simplemente imprimir su contenido:

```cpp
 AmplificaMapa(mapaDeBits, sección)
Si mapaDeBits comienza con un valor
    Rellenar sección del mapa bidimensional con el valor
Si no
    AmplificaMapa(mapaDeBits.removerPrimerElemento, sección.superiorIzquierda)
    AmplificaMapa(mapaDeBits.removerPrimerElemento, sección.superiorDerecha)
    AmplificaMapa(mapaDeBits.removerPrimerElemento, sección.inferiorIzquierda)
    AmplificaMapa(mapaDeBits.removerPrimerElemento, sección.inferiorDerecha) 
```

La primera vez que se llama a la función AmplificaMapa se debe entregar la representación de la forma por descomposición del mapa de bits en la variable mapaDeBits y la sección que se entrega inicialmente es todo el mapa de bits. Esto puede ser manejado por filas y columnas.

A continuación se muestra una implementación en C++ que resuelve el problema. Nótese cómo se maneja la sección sobre la que se está trabajando con cuatro variables: `tl_row`, `tl_col`, `br_row`, `br_col`. El nombre de las variables proviene de top-left row, top-left colum, bottom-right row y bottom-right colum respectivamente. Representan los índices (fila,columa) de las esquinas superior izquierda e inferior derecha.

{{< gist OlimpiadaMexicanadeInformatica 6860210 >}}