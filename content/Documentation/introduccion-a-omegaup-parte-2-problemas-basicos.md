---
title: 'Introducción a omegaUp, parte 1'
author: 'joemmanuel'
author_email: 'joemmanuel@gmail.com'
date: Wed, 09 Oct 2013 16:39:54 +0000
draft: false
tags: ['Documentation', 'Problemas', 'Introducción a omegaUp']
math: true
---

Estamos iniciando una serie de 10 posts para ayudar a nuestros nuevos usuarios a navegar con facilidad entre la gran cantidad de problemas de omegaUp, en forma de mini-tutoriales con los conceptos básicos, temas y fuentes. Esta colección de tutoriales y ligas te ayudarán a resolver muchos de los problemas de omegaUp y aumentar tu nivel de programación.

<!--more-->

En este post inicial voy a cubrir los aspectos más básicos de la resolución de problemas. Vamos a tomar como base el problema clásico [sumas](https://omegaup.com/arena/problem/sumas2#).

**Enunciado del problema**

Nos piden leer 2 números enteros y escribir la suma de ambos. Dónde los leo y cómo los escribo? Todos los problemas de omegaUp (con excepción de los problemas de Karel) usan la entrada estándar (stdin) y la salida estandar (stdout) para comunicarse. omegaUp prohibe abrir archivos por seguridad.

Cómo sabe omegaUp que mi solución está bien o mal? Los problemas de omegaUp tienen un conjunto de "casos de prueba" predeterminados que se usan para revisar tu solución. Cada caso de prueba consta de una entrada (por ejemplo _1 1_) y su solución previamente calculada (_2_ en este caso).

Tu programa es compilado y ejecutado contra cada uno de los casos de prueba: se le da la entrada a tu programa y se compara tu salida con la salida oficial. Si tu programa imprime _2_, entonces se considera el caso como correctamente resuelto.

Tu puntaje final se calcula en base al porcentaje de casos que tu solución resuelve correctamente. El número de casos de prueba predeterminados que tiene un problema es variable (pueden tener desde 1 hasta cientos distintos). Si tu solución obtiene **AC** (accepted), quiere decir que has resuelto todos los casos correctamente.

Con esta información en mente, la solución suena bastante trivial. He aquí un ejemplo en C:

{{< gist joemmanuel 6595935 >}}

y uno en Java: 

{{< gist lhchavez 7710659 >}}

Enviamos esta solución... y nos encontramos que no resuelve todos los casos (obtiene **WA**, wrong answer). Por qué? (Recomiendo al lector que haga una pausa aquí y trate de entender por qué no funciona).

**Límites**

Hay datos que no hemos considerado en la descripción del problema: los límites. Existen 3 tipos de límites comunes en omegaUp:

*   **Límite de tiempo**: Tu solución no puede tardar más del tiempo indicado para resolver un caso. Para nuestro problema Sumas, tenemos 1 segundo para producir una solución. Para entender por qué el tiempo es un factor limitante, te recomiendo leer [The Importance of Algorithms](http://community.topcoder.com/tc?module=Static&d1=tutorials&d2=importance_of_algorithms) en los tutoriales de Topcoder.
*   **Límite de memoria**: Tu solución no puede usar más megabytes de los permitidos por el límite para producir la respuesta.
*   **Límites en las variables de entrada: **No todos los problemas tienen una sección específica donde se indice cuáles son los valores mínimos y máximos de una variable, por lo que necesitamos leer con atención el problema para obtenerlos.

En nuestra solución anterior, hay un dato que no consideramos: La suma de ambos números cabe en un entero de 64 bits. En nuestra solución anterior estábamos usando el tipo de datos int, los cuales tienen un límite de 32 bits (Un int en C puede guardar números entre $latex -2^{31}$ hasta $latex 2^{31}-1$, es decir, de -2147483648 hasta 2147483648 ). Para satisfacer el límite de 64 bits, necesitamos usar variables que puedan soportarlo: long long (en C)

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