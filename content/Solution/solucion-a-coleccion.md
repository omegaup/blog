---
title: 'Solución a "Colección"'
author: 'Freddy'
author_email: 'me@freddy.mx'
date: Sat, 14 Sep 2013 05:16:07 +0000
draft: false
tags: ['Solution', 'Alexis', 'César', 'Etapa 1', 'Examen 5', 'preselectivo', 'solución', 'Soluciones Preselectivo 2014']
aliases: ['/solucion-a-coleccion']
---

**Concurso:** [Preselectivo para la IOI 2014, Etapa 1, Problemset 5](https://omegaup.com/arena/problem/coleccion) **Autor:** Alexis Cervantes / César Cepeda **Fuente:** Alexis Cervantes / César Cepeda

**_Estructura de la solución: _**¿Qué nos están pidiendo? El problema nos esta pidiendo que encontremos un subconjunto de las tarjetas tal que la suma de todos los puntajes de las tarjetas de ese subconjunto sea la maxima posible, y la suma de sus precios sea menor o igual al dinero con el que cuentas.  En otras palabras lo que se esta buscando es que:

la suma {{< video autoplay="true" loop="true" muted="true" src="http://www.olimpiadadeinformatica.org.mx/archivos/apuntes/imagenes/Eje_Bu_51.webm" type="video/mp4" >}}sea maxima siempre y cuando {{< video autoplay="true" loop="true" muted="true" src="http://www.olimpiadadeinformatica.org.mx/archivos/apuntes/imagenes/Eje_Bu_52.webm" type="video/mp4" >}}

donde _Xi_** = **{1 si se compró la tarjeta _i**, **_y 0 si no se compró}

**_Modelo del espacio de búsqueda como árbol: _**Al final de cuentas, incluso el nombre lo indica, este problema se puede reducir a asignarle a cada tarjeta un 0 ó un 1 dependiendo de si la vamos a comprar o no, por lo que una forma de modelar el espacio de búsqueda sería formar un número binario de **_N_** dígitosy crear todos los valores posibles para dicho número.

Para formar todos los números, podemos pensar que en el nivel **_j_** del árbol vamos a decidir si compramos la tarjeta **_j_**, por lo tanto todos los nodos del nivel **_j_** tendrán dos hijos, uno de ellos indicando que si compramos la tarjeta y el otro indicando que no la compramos.  El árbol de búsqueda queda como se muestra a continuación.

{{< video autoplay="true" loop="true" muted="true" src="http://www.olimpiadadeinformatica.org.mx/archivos/apuntes/imagenes/Eje_Bu_53.webm" type="video/mp4" >}}

_**Técnica de búsquda a utilizar: **_Dado que tenemos que entregar como resultado el camino con el mayor puntaje de todos , es preciso que revisemos el 100% de los caminos.  

Una forma de resolver el problema es utilizar búsqued en profundidad, sin embargo el espacio de búsqueda es un árbol binario con **_N_** niveles por tanto de _**2N **_estados.  Para nuestro problema **_N=500_** por lo que el espacio de búsqueda es indescriptiblemente grande, aunque claro que se pueden podar las ramas en las que el precio ya superó a la cantidad de dinero que tenemos, el aplicar la técnica de búsqueda en profundidad en este problema dificilmente alcanzaría para una **_N _**mayor que 24 ó 25.

Necesitamos por tanto encontrar una poda mucho más agresiva.

Anteriormente, en el ejemplo de los Tanques, utilizamos la búsqueda en profundidad para encontrar un camino mínimo, por lo tanto, debido a que cada nivel que descendemos el coste aumenta, se podía aplicar la poda de que si obteniamos algún mínimo se podían cortar todas las ramas cuyo coste fuera mayor o igual que el mínimo actual.  Sin embargo al querer encontrar un máximo, esto no es posible, ya que el coste por rama siempre aumenta y lo que queremos es es encontrar el máximo, así que no sabemos si el camino nos va a llevar a algo mejor a menos que lo recorramos todo!

Pero que pasaría si tuvieramos una función tal que nos permitiera saber cual es el máximo posible que podemos obtener por una cierta rama?  En ese caso, podríamos cortar cualquier rama si supieramos que por ese camino es imposible lograr algo mejor que lo que ya tenemos.

Esta técnica se conoce como de "acotamiento y poda".  La idea es buscar una función que para cada estado del espacio de búsqueda nos de cotas del máximo posible al que se puede llegar por dicho camino y de mínimo seguro que podemos obtener también por ese camino.

Esta técnica es increíblemente poderosa y conviene que mediten un momento sobre la misma.  Vale la pena hacer notar que no siempre es sencillo encontrar la función de acotamiento correcta.  Ya que una función que de una cota muy alta no nos sirve de mucho, ya que las podas serian pocas, pero una cota incorrecta nos puede hacer que entreguemos resultados incorrectos.  Por lo tanto al utilizar esta técnica, siempre debemos buscar la función que acote lo más posible pero estando siempre 100% seguros de que el resultado que obtuvimos es efectivamente mayor o igual al máximo posible.

Para este problema voy a definir las dos funciones de acotamiento, llamemos **_a(c)_** a la función que nos da el máximo posible que se puede obtener estando en el nodo **_c_**y _**b(c)**_ a la función que nos da el mínimo asegurado que tenemos también al estar en el nodo **_c_**.  El demostrar que ambas funciones son válidas queda como tarea para el alumno.

Lo primero que tenemos que hacer es ordenar las tarjetas de acuerdo a la relación **_U/P_**, es decir, cuantos puntos nos dan por cada peso gastado.  Como queremos obtener el máximo puntaje por nuestro dinero obviamente son mejores las tarjetas que nos dan muchos puntos por peso comparadas con las tarjetas que nos dan pocos puntos por cada peso gastado. _**OJO: esto no implica que la solución correcta deba tomar siempre las mejores tarjetas, únicamente quiere decir que comparadas individualmente, para nuestro objetivo son mejores las tarjetas que dan más puntos por peso.**_

Una vez que tengamos todas las tarjetas ordenadas en base a este criterio, iremos decidiendo si las tomamos o no, en ese respectivo orden.  Para cada nodo, nuestras funciones de acotamiento estarán definidas de la siguiente manera:

_**b(c):**_  Para calcular la cota mínima asegurada del nodo **_c_** vamos tomando las tarjetas que aún no hemos utilizado según el ordenamiento mientras aún tengamos dinero, en el momento en el que no tengamos más dinero para comprar ahi nos detenemos.  Ese es el mínimo que seguro podemos obtener.

_**a(c):  **_Para calcular la cota alta, hacemos el mismo procedimiento que en **_b_** (o mejor tomamos el resultado de **_b_** para no recalcular) y con la primera tarjeta que no pudimos tomamos su relacion **_U/P_** y la multiplicamos por el dinero que aún tenemos disponible y lo sumamos a **_b_**.  Así obtenemos el máximo posible que se puede lograr en el subárbol del nodo **_c_**.  La operación que efectuamos al final fue la de utilizar el dinero que aún tenemos disponible para comprar un "pedazo" de la mejor tarjeta aún queda, obviamente esto no es posible ya que no podemos comprar pedazos de tarjeta, sin embargo nos sirve para calcular el máximo posible.  

Demostrar que **_b_** es válida es trivial, sin embargo queda para el lector demostrar que **_a_** es una cota que siempre dará un número mayor o igual al máximo posible que se puede obtener por ese camino.

Obviamente una vez que tengamos las funciones de acotamiento, podemos hacer nuestra búsqueda almacenando cual es el mejor mínimo asegurado que hemos obtenido hasta el momento y eliminando todas las ramas cuyo máximo asegurado es menor o igual que éste.

**_Detalles de implementación: _**Para la implementación queda un último detalle que resolver, y este es como vamos a buscar?  Como casi siempre tenemos dos opciones, la primera es la de la búsqueda en profundidad, para la cual se implementa una rutina recursiva y no se requiere de mantener arreglos de memoria externos.  Y la segunda es una búsqueda por amplitud, para la cual requieres de una cola que te permita almacenar los estados proximos a ser evaluados.

Si optamos por la búsqueda en profundidad, hay un detalle de implementación muy sútil que puede ser de gran ayuda.  Supongan que modelamos el árbol de búsqueda como el que se muestra en la figura de arriba.  Y supongan que nuestro algoritmo de búsqueda revisa primero la rama izquierda, de ser asi, la cota mínima asegurada y la cota máxima del hijo de la izquierda es exactamente igual a la de su padre, por lo que bajariamos un nivel en la búsqueda sin obtener ninguna información nueva, si, en cambio, revisamos primero el hijo de la derecha, entonces estaríamos obteniendo nuevas cotas con información probablemente últil.

Si se opta por la búsqueda en amplitud, se tiene una ventaja, y esta es que la cola se puede sustituir por un monticulo de modo que se priorice la búsqueda según el nodo que tiene el mejor mínimo asegurado.  Sin embargo aunque esto podría efectivamente reducir la búsqueda bastante no estamos seguros del tamaño que puede llegar a tener la cola y requeririamos que al llenarse la cola el programa pudiera cambiar a una técnica de búsqueda en profundidad, lo cual haría el código más enredado.  Sin embargo si se desea llegar a límites aún mas grandes, esta sería la opción a seguir.  

**_Implementación:_**  

{{< gist OlimpiadaMexicanadeInformatica 6558998 >}}