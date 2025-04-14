---
title: 'Solución a "Bloqueo"'
author: 'Freddy'
author_email: 'me@freddy.mx'
date: Tue, 10 Sep 2013 19:35:59 +0000
draft: false
tags: ['Solution', 'Bloqueo', 'Etapa 1', 'Examen 8', 'Khayyam', 'preselectivo', 'solución', 'Soluciones Preselectivo 2014']
aliases: ['/solucion-a-bloqueo']
---

**Concurso:** [Preselectivo para la IOI 2014, Etapa 1, Problemset 8](https://omegaup.com/arena/problem/bloqueo) **Autor:** [Khayyam](http://www.cimat.mx/~omar) **Fuente**: Khayyam

La primera observación que hay que hacer es que si todas las carreteras son bidireccionales y entre cada par de ciudades existe exactamente un camino que las conecta (usando una o mas carreteras) entonces la representación gráfica del problema es un árbol: los nodos representan las ciudades y las aristas representan las carreteras. La siguiente figura, muestra el árbol que representa el caso de prueba dado como ejemplo. Los nodos rojos representan las ciudades ocupadas, el esfuerzo necesario para destruir cada carretera se muestra junto a la arista correspondiente. Entonces queremos eliminar un subconjunto de aristas de peso total mínimo de tal forma que los nodos rojos queden separados.

Caso de ejemplo

Solución

![](/images/example.png)

![](/images/example_solution.png)

En problemas relacionados con árboles, es muy natural tratar de dividir el problema en problemas más pequeños que están dados por los sub-árboles del árbol original. Esto además sugiere usar recursión: "para resolver un árbol, primero resolvemos recursivamente sus sub-árboles y luego combinamos las sub-soluciones".

Comencemos con los casos sencillos. Si hay solamente un nodo (el árbol tiene altura 0), entonces no habrá aristas y el esfuerzo total necesario es cero.

Consideremos ahora un árbol de altura 1 como el de la siguiente figura. Como la raiz no es roja, basta con eliminar una de las dos aristas: elegimos la que requiera menos esfuerzo.

Caso sencillo: altura 1

Solución (suponemos que la arista izquierda requiere menos esfuerzo)

![](/images/simple0.jpg)

![](/images/simple1.jpg)

Si la raiz fuera roja, entonces tendríamos que eliminar ambas aristas. Con lo anterior nos damos cuenta de que hay dos casos que debemos considerar:

1.  Si la raiz es roja, entonces **debemos** eliminar **todas** las aristas que la conectan con nodos rojos
2.  Si la raiz no es roja, entonces no es necesario desconectar la raíz de todos los nodos rojos: la solución óptima es dejar conectado el nodo rojo asociado a la arista mas costosa.

Lo anterior se ilustra en la siguiente figura (aquí suponemos que la arista de la derecha es la mas costosa de todas):

Si la raiz es roja, entonces **debemos** eliminar **todas** las aristas que la conectan con nodos rojos

Si la raiz no es roja, entonces no es necesario desconectar la raíz de todos los nodos rojos

![](/images/redRootAllRed.png)

![](/images/whiteRootAllRed.png)

Ahora que tenemos la solución para los casos pequeños, veamos si podemos usar estas soluciones para construir la solución del problema general, como en la siguiente figura.

Si la raiz es roja y el nodo blanco está conectado  
a algun descendiente rojo, la solución ya no es correcta

Aún si la raiz es blanca, no podemos dejar conectado el nodo blanco  
ya que si está conectado con un descendiente rojo, la solución sería incorrecta

![](/images/redRootAllRed_cloud.png)

![](/images/whiteRootAllRed_cloud.png)

Supongamos que ya tenemos la solución para todos los hijos directos de la raíz, es decir, que ya cortamos de manera óptima las aristas de todos los subárboles, de modo que ningún par de nodos rojos se conectan en el sub-árbol. Usando sólo esta información, ¿podemos construir la solución del problema general?. Desafortunadamente, esto no es suficiente: nos gustaría dejar conectados a los hijos blancos, pero si existe un nodo rojo debajo de ellos, entonces tendríamos que desconectarlo también. Lo que necesitamos saber es precisamente si un hijo blanco está conectado con uno de sus descendientes rojos, de ser así diremos que el nodo blanco es "peligroso". Si el nodo blanco está desconectado de todos sus descendientes rojos, entonces diremos que es "seguro". Entonces tenemos tres tipos de nodos: ocupados, peligrosos y seguros, que representamos como nodos rojos, amarillos y verdes, respectivamente.Con este nuevo concepto, vemos que tenemos dos tipos de soluciones distintas para una raíz blanca: tenemos soluciones peligrosas y soluciones seguras. Es fácil ver que no existen "hojas peligrosas", ya que las hojas están ocupadas (rojas) o son seguras (verdes).

![](/images/redRootOneGreen.png)

![](/images/yellowRootAllRed.png)

![](/images/greenRootAllRed.png)

Reformulemos nuestra solución con este concepto. Si la raíz es roja, entonces debemos desconectarla de todos sus hijos rojos y de todos sus hijos peligrosos. Esto significa que para cada hijo blanco tenemos dos opciones:

*   Hacer que el hijo sea seguro (verde) y no cortar la arista que lo une con la raíz (puede ser costoso hacerlo seguro, pero con eso nos ahorramos el costo de separarlo de la raíz)
*   Hacer que el hijo sea peligroso (amarillo) y cortar la arista que lo une con la raíz (puede ser barato dejarlo inseguro, pero pagamos al separarlo de la raíz)

Lo anterior resuelve el caso en que la raíz es roja.

Ahora, si la raíz no es roja, debemos calcular dos soluciones: la solución segura (dejar la raíz verde) y la solución peligrosa (dejar la raíz amarilla). Notemos que la solución segura es exactamente igual al caso anterior. Por otro lado, para la solución peligrosa, debemos dejar la raíz conectada a exactamente un hijo que sea rojo o peligroso. Para elegir cuál de todos los hijos rojos o peligrosos dejaremos conectado, basta iterar sobre todos los hijos y elegir la mejor opción. El código queda como sigue:

{{< gist OlimpiadaMexicanadeInformatica 6559253 >}}