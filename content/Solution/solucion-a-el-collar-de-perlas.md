---
title: 'Solución a "El collar de perlas"'
author: 'Lira'
author_email: 'elira@elira.me'
date: Thu, 03 Jan 2013 16:01:37 +0000
draft: false
tags: ['Solution', 'Etapa 1', 'Examen 10', 'felix', 'preselectivo', 'solución', 'Soluciones Preselectivo 2013']
aliases: ['/solucion-a-el-collar-de-perlas']
---

**Concurso:** [Preselectivo para la IOI 2013, Etapa 1, Examen 10](https://omegaup.com/arena/IOI2013E1P10)**[ ](https://omegaup.com/arena/IOI2013E1P10) Autor: **[Félix Rafael Horta Cuadrilla](http://goldendarknut.blogspot.mx/)

En una bosque habitan dos clanes de enanos: los enanos rojos y los enanos verdes. Durante sus expediciones en las cuevas cercanas, un grupo de enanos rojos y verdes encontraron un collar formado por perlas blancas y negras que no tienen ningun valor, pero al final del collar hay un valioso diamante. Los dos clanes de enanos quieren apoderarse del diamante.  
  
Para resolver el problema de manera pacifica deciden jugar el siguiente juego: a cada uno de los N enanos se le asigna un numero del 1 al N (un numero diferente para cada enano) y dos listas de numeros, una negra y una blanca (las listas pueden ser diferentes entre si). Cada lista contiene una cantidad diferente de numeros, cada numero _i_ en cualquier lista representa al enano _i_.  
  
Durante el juego, el collar se pasa de un enano a otro de acuerdo con las siguientes reglas: cuando un enano recibe el collar, el quita la primer perla en el collar y si la perla es blanca, entonces pasa lo que quedo del collar a cualquier enano que este en su lista blanca (al que el quiera), pero si la piedra es negra, entonces pasa lo que quedo del collar a algun enano de su lista negra. Para empezar el juego, el collar se le da a un enano aleatoriamente.  
  
En algun momento el collar solamente va a tener el diamante, el enano que recibe el collar en este estado gana el diamante para su clan y el juego termina.  
  

<!--more-->

**Problema**  
  
Escribe un programa que ayude a los enanos verdes a obtener el diamante, sabiendo de antemano las listas de todos los enanos. Puedes asumir que los enanos rojos juegan de manera optima. Se garantiza que siempre habra una forma en la que los enanos verdes puedan ganar si juegan optimamente.  
  
**Entrada**  
  
La primer linea contiene la longitud **L** del collar, el numero **N** de enanos y el numero **F** que representa el enano que empieza con el collar.  
  
La segunda linea contiene **L** caracteres (seguidos, es decir, **NO** hay espacios entre ellos) que representan el collar, estos caracteres pueden ser una letra **B** que significa que es una perla blanca, una letra **N** que significa que es una perla negra o una **D** que indica que es el diamante. Solo habra un diamante y este siempre estara al final del collar.  
  
Las siguientes **N** lineas describen a los enanos y sus listas. Cada linea esta formada por un numero **C** que representa el color del enano (0 si es verde y 1 si es rojo) seguido por la longitud **LN** de la lista negra y de **LN** numeros, representando cada uno de los numeros en la lista negra del enano. Finalmente, en la misma linea, el numero **LB** que indica la longitud de la lista blanca del enano y de **LB** numeros indicando los elementos de dicha lista.  
  
**Límites**  
  
1 <= L <= 1000  
  
1 <= N <= 1000  
  
**Interacción**  
  
Este problema es interactivo y deberas escribir una funcion llamada _juega()_ que lea de pantalla el problema los datos de entrada y se cominique con tres funciones en una libreria.  
  
Las tres funciones con las que hay que interactuar son las siguientes:  
  
    void pasaCollar(int enano);  
  
Que sirve para que cuando uno de los enanos verdes posea el collar, tu programa mande el collar al enano especificado como parametro. Llamar a _pasaCollar_ cuando no le corresponde o pasar el collar a un enano que no este en la lista correspondiente resultara en 0 puntos en ese caso.  
  
    int recibeCollar();  
  
Que sirve para que cuando uno de los enanos rojos posea el collar, tu programa llame a esta funcion para saber a que enano paso el collar el evaluador. Llamar a esta funcion cuando no le corresponde el turno a un enano rojo resultara en 0 puntos en ese caso.  
  
void termina();  
  
Debe ser llamada una vez cuando en el collar solo quede el diamante. Si se llama en otro momento o si se llama y el collar esta en posesion de un enano rojo obtendras cero puntos en ese caso. Solo recibiras puntos si llamas a la funcion _termina()_ cuando el collar este en posesion de un enano verde y el collar solo posea al diamante.  
  
**Ejemplo**  
  
Entrada  
  
6 4 2  
NBBNND  
0 1 2 1 4  
0 2 1 3 1 1  
1 1 4 1 4  
1 2 2 3 1 1  
  
Salida  
  
pasaCollar(1)  
pasaCollar(4)  
recibeCollar() -> 1  
pasaCollar(2)  
pasaCollar(1)  
termina()  
  
**Compilación**  
  
Se proporcionan plantillas para facilitar la codificación del problema, de esa forma sólo necesitas codificar el archivo perlas.c/perlas.cpp/perlas.pas. Las plantillas son solo para facilitar la codificación y las pruebas, **no se garantiza que se evaluará con las mismas**.  
  
Utilizando la plantilla proporcionada, puedes compilar este programa correctamente en C++ de la siguiente forma:  
  
    g++ main.cpp perlas.cpp -o perlas  
  
En C, se hace de la siguiente forma:  
  
    g++ main.c perlas.c -o perlas  
  
Mientras que para Pascal:  
  
fpc main.pas  
  
De la misma forma, las opciones de compilación pueden ser diferentes en la evaluación, sin embargo, si tu programa compila con las plantillas, también debería de hacerlo en el evaluador.  

  
**Descarga las plantillas [aquí](https://www.dropbox.com/sh/nux63uknmdyzgej/sfqTP9Tng8/plantillas.rar) .**  
  
  
  
**Solución**  
  
Una manera sencilla de tratar de ganar en este juego, es hacer una búsqueda sobre las listas de los enanos verdes y siempre pasar el collar sobre los enanos verdes, lo cual resolvería un par de casos. Sin embargo, en la mayor parte de los casos, es necesario pasar el collar a un enano rojo que eventualmente lo regresará a un enano verde. Y este es precisamente el problema, saber cuándo pasar a un enano rojo y a qué enano rojo, y como se necesita de la interacción de los enanos rojos para llegar a la solución, un gran problema se presenta.  
  
Aunque este problema podría resolverse fácilmente con una búsqueda memorizada haciendo las llamadas a las funciones durante la búsqueda, no puede hacerse de esta forma porque cuando se hace una búsqueda se requiere poder ir hacia adelante y hacia atrás en el árbol de búsqueda, y como se necesita de la interacción de los enanos rojos, se tiene que lograr la solución en la primera pasada.  
  
Por lo tanto hay que calcular todas las posibles tiradas antes de jugar, considerando las mejores tiradas de los enanos rojos. De esta forma, una vez que se tiene  una jugada para ganar el juego para **cualquier estado posible**, se puede jugar teniendo seguro el triunfo.  
  
Ahora, aunque sabemos que no se puede resolver con una búsqueda, sí podemos utilizar un árbol de búsqueda para resolver el problema, pero ¿cómo tomar en cuenta las elecciones de los enanos rojos?, la respuesta a esto es jugar para ambos equipos y usar el mismo cósigo para ello, eligendo siempre la mejor opción para **el color de enano** en cada turno, es decir, cuando la búsqueda esté sobre un enano rojo, hay que elegir la opción que haga que los enanos rojos ganen, y cuando la búsqueda esté sobre un enano verde, hay que elegir la opción que haga ganar a los enanos verdes.  
  
Es evidente que cuando las hojas del árbol terminan en un enano verde, se gana el juego (esos estados son estados ganadores), y cuando termina en un enano rojo el juego se pierde (esos estados son estados perdedores), eso es fácil, lo difícil son los siguientes niveles.  
  
Tomando en cuenta esto necesitamos etiquetar todos los estados como estados ganadores o estados perdedores, debido a que ya sabemos qué son los estados hojas, podemos deducir qué son los estados anteriores a las hojas de la siguiente forma: Si el estado pertenece a un enano verde, nos basta con que UN y solo UN enano en su lista lleve a un estado ganador, ya que como enanos verdes podemos controlar a quien le pasamos el collar, por lo que basta con que el estado pueda llevar a un estado ganador para que también sea un estado ganador. Si el enano verde NO lleva a ningún estado ganador, entonces ese estado NO es un estado ganador, por que no importa a quien se lo pases, siempre perderás.  
  
Pensando de esta misma forma, si el estado pertenece a un enano rojo, necesitamos que TODOS los estados a los que conduzca sean estados ganadores, por que si hay solo un estado perdedor, los enanos rojos, que juegan con la mejor estrategia, siempre eligirán ese estado.  
  
De esta forma, es posible que haya enanos verdes a los que quieras evitar, y enanos rojos a los que quieras pasarle el collar.  
  
Entonces, para resolver el problema, hay que pasar por todos los estados y marcarlos como estados ganadores o estados perdedores con la técnica que más te guste, ya sea programación dinámica o búsqueda memorizada, pero hay que hacerlo antes de jugar. Una vez teniendo precalculado cuáles son los estados ganadores y perdedores, solo hay que hacer las llamadas de los enanos verdes siempre hacia estados ganadores.

[DESCARGAR ARCHIVOS Y SOLUCIÓN](http://elira.operamail.com/files/perlas.rar)