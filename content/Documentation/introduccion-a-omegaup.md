---
title: 'Introducción a omegaUp, parte 0'
weight: 2
author: 'lhchavez'
author_email: 'lhchavez@omegaup.com'
date: Fri, 29 Nov 2013 20:35:09 +0000
draft: false
tags: ['Documentation', 'Problemas', 'Introducción a omegaUp']
aliases: ['/introduccion-a-omegaup']
---

{{< youtube NgaYc9eYBbo >}}

Hola!

Hemos recibido varias preguntas sobre cómo se envían soluciones a omegaUp. Decidí escribir una introducción a omegaUp, antes de empezar a aprender a resolver problemas. En resumen:

*   El objetivo de los concursos es acumular más puntos que todos los demás participantes. En caso de empate, se toma en cuenta la suma de los penalties (dependiendo del concurso puede no haber penalties, ser el tiempo desde que inició el concurso hasta que enviaste la solución o el tiempo desde que abriste el problema por primera vez hasta que lo resolviste).
*   Jamás se te quitarán puntos por intentar resolver un problema: si ya habías enviado una solución con _x_ puntos, únicamente se cambiará tu puntuación y penalty si obtienes más de _x_ puntos.
*   Toda la entrada y salida se hace mediante entrada estándar ("teclado" y "consola"), y no debes imprimir nada que no indique el problema: no debes poner cosas como "Dame un número". omegaUp te proporcionará la entrada tal y como viene descrita en el problema.
*   Todos los problemas de Java **deben** tener Main como nombre de clase. Si usas cualquier otro nombre, te regresará un Runtime error.
*   cin (en C++) y Scanner (en Java) son relativamente lentos. En problemas donde haya mucha entrada, se recomienda usar scanf (en C/C++) y BufferedReader (en Java).
*   Toda la entrada y salida está en formato Unix: las líneas terminan con "\\n", no con "\\r\\n".

Primero veamos cómo luce la arena durante un concurso:

![](http://i.imgur.com/Px5IgWo.png?7695)

El reloj de arriba, si es negativo, te dice cuánto tiempo falta para que inicie el concurso. Cuando es positivo, te dice cuánto tiempo falta para que termine el concurso. Una vez que llega a cero, el concurso se cierra y ya no puedes enviar problemas. Hay tres pestañas en esta vista:

*   **Problemas**: la que está mostrada arriba
*   **Ranking**: te muestra con una gráfica el progreso del top 10 del concurso con respecto al tiempo y también muestra el ranking general para el concurso. Esta información se actualiza casi en tiempo real, así que si no ves un cambio en el scoreboard, ten paciencia y en un par de minutos se reflejará. Ten en cuenta que en algunos concursos, faltando poco tiempo para el final (puede ser una hora o media hora), el ranking deja de actualizarse para meter más emoción =)
*   **Clarificaciones**: aquí puedes pedir clarificaciones específicas a la _redacción_ de un problema, si algo no es suficientemente claro. Este no es el lugar para preguntar por qué cierto código no funciona (ese es el chiste del concurso! que tú sepas), así que evítate la molestia porque los jueces no te responderán. A los jueces les toma un poco de tiempo leer todas las clarificaciones y responderlas adecuadamente, así que ten paciencia. Ponte a resolver otro problema mientras. **Nota**: a veces verás que hay una nueva clarificación sin que tú hayas pedido una. Léela, porque es una clarificación global, o los jueces están intentando avisarte de algo.

En la sección de Problemas es donde pasarás la mayor parte del concurso. En la parte de la izquierda está la lista de problemas junto con dos números (como 0 / 100). Estos números indican cuántos puntos has acumulado en ese problema y cuántos puntos vale el problema en total. A menos que los casos estén mal y los jueces hayan decidido re-juecear todos los envíos de un problema, esos puntos no pueden bajar si haces más envíos a un problema. Abajo de la lista de problemas, hay un miniranking con los mejores 10 participantes. Faltando poco tiempo antes del concurso, esta tabla dejará de actualizarse, no te apaniques.

Cuando selecciones un problema, verás la descripción de ese problema. En la mayoría de los concursos, se te agregará un penalty entre más te tardes en resolver un problema desde que inicia el concurso o lo abres por primera vez, así que trata de resolverlo lo más rápido posible. Este penalty **NO** te quita puntos, y solo se utiliza en caso de empates.

![](http://i.imgur.com/jbEGHWK.png)

Hasta arriba viene una tablita con varias cosas útiles, como la cantidad de puntos máximos que te dará ese problema cuando lo resuelvas, el límite de tiempo que tienes para resolver _cada caso_ y el límite de memoria que tienes para resolverlo. Después viene la descripción del problema (que usualmente es una pequeña historia) y le descripción formal del problema, la descripción formal del formato de la entrada, la salida y algunos ejemplos que confirman la explicación. Algunos problemas también incluyen una sección con todos los límites de las variables expuestas en la descripción del problema. Si no entiendes algo del problema, siéntete libre de escribir una clarificación. Por último, encontrarás una pequeña tablita con todos los envíos que has realizado para ese problema

![](http://i.imgur.com/vAXlkP7.png)

Puedes ignorar el ID, se utiliza únicamente por si algún juez te lo pregunta en caso de que haya problemas con el problema y haya necesidad de rejuecear envíos. Lo importante son las columnas de Puntos y Penalty. La información que aparece en el ranking toma en cuenta el envío que hayas hecho que tenga más puntos (y en caso de empate, el que tenga menos penalty). La columna de status son dos letras que te dan una pequeña pista de qué pasó con tu envío en general:

*   AC - Accepted. Tu envío resolvió correctamente todos los casos de prueba y obtuviste la máxima cantidad de puntos. Felicidades!
*   PA - Partially Accepted. Tu envío resolvió al menos un caso de prueba, pero hay al menos un caso que no resolviste correctamente. Intenta arreglar tu programa y vuélvelo a intentar.
*   WA - Wrong Answer. Tu programa no resolvió ningún caso correctamente.
*   TLE - Time Limit Exceeded. Al menos en uno de los casos, tu programa excedió el límite de tiempo. Intenta pensar en una solución más eficiente o busca en tu código si hay algún ciclo infinito.
*   MLE - Memory Limit Exceeded. El menos en uno de los casos, tu programa excedió el límite de memoria. Intenta pensar en una solución que utilice menos memoria. En C y C++, algunos MLE se pueden reportar como RTE, sobre todo si declaraste arreglos gigantes.
*   RTE - Runtime error. En al menos uno de los casos, tu programa tuvo un error fatal: puede ser una excepción en Java, no utilizaste "Main" como nombre de clase en Java, divisiones entre cero, desbordaste el stack, te saliste de los límites de un arreglo, etc. Vuelve a leer el problema y piensa qué casos se te olvió considerar y qué entrada puede hacer que tu programa se comporte de esta manera.
*   RFE - Restricted function. En al menos uno de los casos, tu programa intentó realizar una operación prohibida. En general, no puedes abrir ningún archivo, no puedes conectarte a internet, no puedes ejecutar otros programas y no puedes comunicarte con nada del sistema fuera del problema. Limítate a resolver el problema usando algoritmos.
*   CE - Compilation error. Tu programa no pudo ser compilado. omegaUp utiliza gcc y g++ en Linux, y usamos Java 1.6, así que podrían haber incompatibilidades entre tu ambiente de desarrollo y el que usamos nosotros. Si haces click en el botón de "Ver" el código, verás tu código seguido del error del compilador.
*   JE - Judge error. Un error interno de omegaUp. Esto no debería pasar nunca, pero si te sale, alguno de los jueces ya lo vio y lo resolverá lo más rápido posible, así que no es necesario que lo reportes. Intenta otro problema mientras tanto, y ten por seguro que no serás penalizado por ese envío, porque no fue tu culpa.

Como puedes darte cuenta, varios de los status no son mutuamente exclusivos. Siempre intentaremos el error más severo (los errores más severos están en la parte de abajo de esta lista), así que por ejemplo, si un envío te marca TLE y tienes algunos puntos, en ninguno de los casos detectamos un MLE ni un RFE, tuviste algunos casos bien, pero pudiste haber tenido otros casos mal y en al menos un caso excediste el límite de tiempo.

Si crees que tu programa está resolviendo bien el problema, deténte a pensar por qué podría estar mal. El 99% de las veces, el problema está bien (sobre todo si hay alguien más que ya lo logró resolver), pero si tienes evidencia que hay algún error en el problema (por ejemplo, si dice la descripción que no habrán números mayores a 1000, y en tu programa validas esto y haces que te devuelva un veredicto como MLE), por favor pide una clarificación con esta información y tu ID de envío para que los jueces lo revisen.

Ahora sí, estás listo para continuar con la [parte 1](http://blog.omegaup.com/2013/10/introduccion-a-omegaup/ "parte 1") del tutorial de omegaUp.