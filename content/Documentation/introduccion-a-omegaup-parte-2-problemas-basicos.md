---
title: 'Introducción a Omegaup, parte 2 - Problemas básicos'
weight: 3
author: 'joemmanuel'
author_email: 'joemmanuel@gmail.com'
date: Tue, 08 Oct 2013 14:48:09 +0000
draft: false
tags: ['Study material', 'Introducción a omegaUp']
aliases: ['/introduccion-a-omegaup-parte-2-problemas-basicos']
---

Hola de nuevo. Continuando con la serie Introducción a Omegaup, esta vez vamos a hacer referencia a los problemas más sencillos de la plataforma a la fecha. [Aquí se encuentra la parte 1](http://blog.omegaup.com/2013/09/introduccion-a-omegaup/#more-406) de esta serie.

Para estos problemas, no se requiere conocer una técnica o un algoritmo en específico: simplemente requieren implementar (o simular) lo que se describe en el problema o hacer una o dos observaciones relativamente sencillas que permiten simplificar la implementación o acortar el número de operaciones que tu programa tendría que hacer y con ello poder resolver el problema dentro de los límites.

**Material de estudio**

Antes de pasar a la lista de problemas, quiero empezar con las lecturas recomendadas para empezar a resolver problemas en omegaUp:

*   [El Libro de Luis Vargas sobre Algoritmos.](https://omegaup.com/img/libropre3.pdf) Este es el libro que usamos para preparar a los preseleccionados de México para la Olimpiada Internacional de Informática. Su lectura completa es recomendada, sin embargo las secciones VII y II son fundamentales.
*   Los temas 1, 2, 4 y 5 [del blog de Pier Paolo](http://pier.guillen.com.mx/) sobre algoritmos.
*   [The Importance of Algorithms](http://community.topcoder.com/tc?module=Static&d1=tutorials&d2=importance_of_algorithms) (Topcoder Algorithm tutorials)
*   [Mathematics for Topcoders](http://community.topcoder.com/tc?module=Static&d1=tutorials&d2=math_for_topcoders) (Topcoder Algorithm tutorials)

**Problemas directos**

Estos concursos fueron diseñados para familiarizarse con la programación competitiva en general. Son excelentes para empezar y su solución generalmente no requiere dominar una técnica en específico, más bien requieren saber usar las construcciones (ciclos, condiciones, etc...) del lenguaje correctamente:

*   [Código Rush 2013 (Taller)](https://omegaup.com/arena/CR41Taller/practice)
*   [Código Rush Otoño 2013](https://omegaup.com/arena/CR41/practice)
*   [CUPA 2012 Warmup](https://omegaup.com/arena/CUPA2012warmup/practice)

**Problemas no-tan-directos**

*   [Engranes ](https://omegaup.com/arena/problem/engranes)([solución](http://blog.omegaup.com/category/soluciones-preselectivo/etapa-1/examen-1/))
*   [Lento](https://omegaup.com/arena/problem/lento) ([solución](http://blog.omegaup.com/2012/10/juego-lento-ethan-jimenez/))
*   [Subprimos](https://omegaup.com/arena/problem/subprimos) ([solución](https://gist.github.com/joemmanuel/6885731) de [diego\_futbolm](https://omegaup.com/profile/diego_futbolm))
*   [La venganza de Silvio](https://omegaup.com/arena/problem/VenganzaDeSilvio) ([solución](http://blog.omegaup.com/2013/08/solucion-a-la-venganza-de-silvio/))
*   [Las cartas del Dr. Lira](https://omegaup.com/arena/problem/CartasDrLira) ([solución](http://blog.omegaup.com/2013/07/solucion-a-las-cartas-del-dr-lira/))
*   [El tablero de Bety](https://omegaup.com/arena/problem/EltableroBety) ([solución](https://gist.github.com/joemmanuel/6885843) de [spleensarethebest](https://omegaup.com/profile/spleensarethebest))
*   [Triángulos](https://omegaup.com/arena/problem/triangulos) ([solución TriangleConstruction en Topcoder](http://community.topcoder.com/tc?module=Static&d1=hs&d2=match_editorials&d3=tchs07Rd1Gamma))

y uno en Java: 

{{< gist lhchavez 7710659 >}}

Enviamos esta solución... y nos encontramos que no resuelve todos los casos (obtiene **WA**, wrong answer). Por qué? (Recomiendo al lector que haga una pausa aquí y trate de entender por qué no funciona).

**Límites**

Hay datos que no hemos considerado en la descripción del problema: los límites. Existen 3 tipos de límites comunes en omegaUp:

*   **Límite de tiempo**: Tu solución no puede tardar más del tiempo indicado para resolver un caso. Para nuestro problema Sumas, tenemos 1 segundo para producir una solución. Para entender por qué el tiempo es un factor limitante, te recomiendo leer [The Importance of Algorithms](http://community.topcoder.com/tc?module=Static&d1=tutorials&d2=importance_of_algorithms) en los tutoriales de Topcoder.
*   **Límite de memoria**: Tu solución no puede usar más megabytes de los permitidos por el límite para producir la respuesta.
*   **Límites en las variables de entrada: **No todos los problemas tienen una sección específica donde se indice cuáles son los valores mínimos y máximos de una variable, por lo que necesitamos leer con atención el problema para obtenerlos.

En nuestra solución anterior, hay un dato que no consideramos: La suma de ambos números cabe en un entero de 64 bits. En nuestra solución anterior estábamos usando el tipo de datos int, los cuales tienen un límite de 32 bits (Un int en C puede guardar números entre $ -2^{31}$ hasta $ 2^{31}-1$, es decir, de -2147483648 hasta 2147483648 ). Para satisfacer el límite de 64 bits, necesitamos usar variables que puedan soportarlo: long long (en C)

{{< gist joemmanuel 6596436 >}}

Nota como tuvimos que cambiar el %d del printf/scanf por %lld para leer y escribir correctamente el entero long long. omegaUp evalúa las soluciones en Linux y para C/C++ usa el compilador g++.

La misma solución en Java:

Si quieres saber más sobre los tipos de variables y sus límites, te recomiendo leer: [Representation of integers and reals](http://community.topcoder.com/tc?module=Static&d1=tutorials&d2=integersReals) en Topcoder.com .

**Para saber más...**

Aquí enlisto varias fuentes de muy buena información sobre cómo resolver problemas y diseñar algoritmos para concursos de programación en general.  Los siguientes tutoriales estarán basados en estas fuentes, les recomiendo mucho darles una revisada:

*   [Problemas y Algoritmos, Luis Vargas.](https://omegaup.com/img/libropre3.pdf)
*   [El blog de Pier Paolo sobre Algoritmos](http://pier.guillen.com.mx/)
*   [TopCoder tutorials](http://community.topcoder.com/tc?module=Static&d1=tutorials&d2=alg_index). En particular les recomiendo empezar por [The Importance of Algorithms](http://community.topcoder.com/tc?module=Static&d1=tutorials&d2=importance_of_algorithms) y [How to find a solution.](http://community.topcoder.com/tc?module=Static&d1=tutorials&d2=findSolution)
*   [El blog de Rodrigo Burgos (nivel avanzado)](http://algorithmmx.blogspot.com/)

**Con qué otros problemas puedo practicar?**

Aquí hay algunos otros problemas con los que puedes practicar para iniciarte en omegaUp. Incluyo un link al código de la solución, pero mi recomendación es que trates de hacerlos por tí mismo. Ve la solución sólo en caso de que estes completamente bloqueado:

1.  [aMAYUSCULAS](https://omegaup.com/arena/problem/aMAYUSCULAS). [Solución](https://gist.github.com/joemmanuel/6596774).
2.  [Bisiesto](https://omegaup.com/arena/problem/bisiesto). [Solución](https://gist.github.com/joemmanuel/6596821).
3.  [Patos](https://omegaup.com/arena/problem/patos). [Solución](https://gist.github.com/joemmanuel/6596898).

Tienes otros tips o algunos tutoriales/soluciones que quieras compartir? Escríbelos en los comentarios.
