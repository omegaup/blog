---
title: 'Trucos para ser más cool'
author: 'erosethan'
author_email: 'erosethanjv@gmail.com'
date: Mon, 07 Jul 2014 05:37:40 +0000
draft: false
tags: ['Study material', 'c++', 'cin', 'Concursos', 'cool', 'cout', 'librerias', 'Material de estudio', 'trucos', 'yolo']
---

Después de un rato de investigación y experimentación, por fin me tomo el tiempo para escribir este post y presentarles algunos trucos que, considero, podrían ayudarles a simplificarse la vida cuando programen y, obviamente, a ser mucho más cool.

**_¿Cansado de importar librerías como asíatico en TopCoder? ¡Aquí está la solución!_**

Muchas veces es nefasto encontrar varios (sino es que miles) errores al compilar a causa de librerías que hemos olvidado incluir. Existe una librería que, al incluirla, agrega todas las librerías estándar de C++ a nuestro código, ¡incluso las de la STL!

_¿Que clase de brujería es esta?_ Seguramente se estarán preguntando. Muy sencillo, solo necesitan escribir la siguiente línea de codigo: `#include <bits/stdc++.h>`

_(Actualización) _Gracias a el comentario de lhchavez por remarcar el hecho de que esta línea funciona únicamente con el compilador _gcc_. Pese a esto, gran parte de los evaluadores actualmente usan _gcc,_ por lo que podemos confiar en su uso, al menos en omegaUp. En caso de que la librería anterior no siga siendo soportada por omegaUp, les informaremos oportunamente.

_**¡Mi mami dice que cin/cout es malo y no debo juntarme con ellos!**_

Si no me equivoco, durante mucho tiempo se ha tratado a scanf y printf como el pan de cada día para la entrada y salida en los concursos de programación, al menos en México. Mientras tanto, se satanizó a cin y cout por ser lentos (o especiales, como dice mi mami) para realizar entrada y salida eficiente.

Sin embargo esto siempre fue un mito, los métodos cin/cout son incluso más eficientes que scanf/printf, solo había que descubrir el por que no lo notamos.

Resulta que cin/cout son muy buenos amigos de scanf/printf. Como son tan buenos amigos, al realizar la lectura y salida no querían alejarse demasiado, por lo que cin/cout tenía que sincronizarse para estar siempre a la par de scanf/printf.

Para no hacer el cuento largo, hay una forma de desactivar la opción de sincronización entre cin/cout y scanf/printf, solo es necesario incluir al inicio del main:

```c++
std::cin.tie(nullptr);
std::ios_base::sync_with_stdio(false);
```

Con esto podemos usar cin y cout sin temor a obtener TLE por lectura lenta, ¡Yaaay!

_**¿Y eso es todo? ¿Ya puedo disfrutar de cin y cout?**_

Casi. Antes de cantar victoria hay un último detalle para evitar los TLE. Gracias a un último experimento, encontramos que cuando se presentaban outputs muy grandes, cin/cout optimizado seguía lanzando TLE cuando scanf/printf no.

¡Tranquilos! También es posible evitar este error. El problema se presentaba porque comúnmente usaríamos lo siguiente: `cout << numero << endl`. Sucede que _endl_, además de imprimir un salto de línea, hace _flush_ en el flujo de salida, lo cual es considerablemente costoso al imprimir muchas líneas y entorpece el rendimiento.

Para que la salida sea eficiente, recomendamos que uses el salto de línea literal `"\n"`.

Con los dos trucos anteriores, la eficiencia de cin/cout mejora generalmente un _**5-10%**_ los resultados obtenidos por scanf/printf. Bastante cool, ¿no?

Aunque el objetivo original no es ganar unas cuantas centésimas de segundo en eficiencia, sino dar la oportunidad a aquellos olímpicos que no manejan scanf/printf para seguir usando cin/cout sin enfrentarse a más complicaciones.

Finalmente les dejó un ejemplo de cómo usar todo lo anterior en un código de C++. Espero que algo de esto les pueda ayudar en el futuro. Les deseo lo mejor :)

```c++
#include <bits/stdc++.h>
#define optimizar_io do { std::ios_base::sync_with_stdio(false); std::cin.tie(nullptr); } while(false)`

int main(){
  optimizar_io;
  int a, b;
  std::cin >> a >> b;
  std::cout << a + b << "\n";
  return 0;
}
```
