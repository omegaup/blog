---
title: 'Solución a "El Artista Lento"'
author: 'Lira'
author_email: 'elira@elira.me'
date: Fri, 19 Oct 2012 17:09:21 +0000
draft: false
tags: ['Solution', 'Etapa 1', 'Examen 2', 'Soluciones Preselectivo 2013']
aliases: ['/solucion-a-el-artista-lento']
---

**Concurso:** [Preselectivo para la IOI 2013, Etapa 1, Examen 2](https://omegaup.com/arena/IOI2013E1P2)**[ ](https://omegaup.com/arena/IOI2013E1P2) Autor: **[Christian Hernández](#)

Lo primero de lo que debemos darnos cuenta es de que como los pedazos son de dimensiones enteras y se colocan en dimensiones enteras, podemos "pensar" el problema de manera que en lugar de pegar rectángulos de **Mi** x **Ni**, estamos pegando **Mi** x **Ni** de 1 x 1 (Ejemplo: Si tuvieramos que pegar un rectángulo de 4 x 3, podemos pensarlo como pegar 12 rectangulos de 1 x 1). Podemos pensar lo mismo de los rectángulos adhesivos.

Si pensamos el problema sin rectángulos adhesivos, podríamos resolverlo teniendo en un arreglo matricial el color que se encuentra hasta arriba de cada rectángulo de 1 x 1 que tiene la cartulina.

Si tomamos la misma idea pero ahora teniendo en cuenta que existen rectángulos adhesivos, nos encontramos con el problema de que si rasgamos un cuadro necesitamos recordar el color la capa de papel que se encontraba debajo de la capa "visible", y además podemos rasgar tantas veces como capas de papel hemos puesto. Con esto tenemos que necesitamos guardar un número de valores igual al número de capas que hemos puesto. Además tenemos que tener en cuenta el orden en el que fuimos poniendo las capas; esto es la última capa que pusimos debe de recordarse primero que la primera que pusimos, o en otras palabras: El primero que entras es el último que sale, así como el el último que entra es el primero que sale. Ese comportamiento lo encontramos en la estructura de datos Pila (Si no conoces la estructura de datos, puedes consultarla [acá](http://es.wikipedia.org/wiki/Pila_(informática))).

A continuación se encuentra la implementación de una estrúctura Pila que nos serviría para este problema:  

```cpp
struct Pila{
		char arreglo[2002];
		short int posActual;
		
		//Devuelve si la pila esta vacia
		bool estaVacia(){
				return posActual == 0;
		}
		
		//inserta un elemento en cima de la pila
		void push(char valor){
				posActual++;
				arreglo[posActual] = valor; 
		}

		//quita el elemento de la cima de la pila y lo devuelve
		char pop(){
				char valor = 0;
				if(!estaVacia()){
						valor = arreglo[posActual];
						posActual--;
				}
				return valor;
		}

		//devuelve el valor del elemento de la cima de la pila
		char top(){
				return arreglo[posActual];
		}
}; 
```

  
Es importante notar que esta es una implementación estática de una Pila (Siempre ocupa el mismo espacio en memoria sin importar el número de elementos, además de que el número de elementos máximo ya está definido). Como se ve, se han utilizado char para guardar los valores, ya que el valor de los colores llega hasta 100, por lo que un char es más que suficiente.

Entonces teniendo pilas para recordar todas nuestras capas de papel en orden, lo que podemos hacer es hacer un arreglo matricial de pilas para resolver nuestro problema.

Básicamente, cada que agreguemos un rectágulo de papel a nuestra cartulina lo que tenemos que hacer es, para cada rectángulo de 1 x 1 que abarca, agregar el color a la pila en su posición en la matriz. Si se trata de un rectángulo adhesivo, hacemos justo lo contrario, sacamos un valor de la pilas correspondientes.

Sólo nos queda resolver el problema del grosor de la cartulina. Debido a que necesitamos desgarrala G veces con un rectángulo adhesivo, podemos pensar que se tratan de G capas de papel del color de la cartulina. Entonces, se reduce a inicializar nuestro arreglo pilas agregando G capas del color de la cartulina.

La complejidad de agregar una capa de papel a la cartulina es de **O(M x N)** (ya que una sola capa puede abarcar toda la cartulina), la misma aplica para usar un rectángulo adhesivo. Entonces la complejidad de agregar todas las capas quedaría **O(M x N x K)** donde **K** es el número de rectángulos por pegar. Inicializar la cartulina tendría una complejidad **O(M x N x G)** donde **G** es el grosor. Dejándonos con una complejidad final de **O(M x N x (K + G))** que es suficientemente buena como para funcionar con los límites de tiempo establecidos.

La complejidad en memoria es igual de **O(M x N x (K + G))**, ya que se tienen que guardar las **(K + G)** capas de papel en la matriz de **M** x **N**.

{{< gist OlimpiadaMexicanadeInformatica 6559074 >}}