---
title: 'Resolviendo problemas con un límite bajo de memoria'
author: 'Sergio Márquez'
author_email: 'sergio@omegaup.com'
date: Sun, 05 Dec 2021 05:03:04 +0000
draft: false
tags: ['Study material', 'Material de estudio', 'omegaUp']
---

Gracias @Rodrigo-RCC por este aporte!

El límite de memoria de un problema puede cambiar drásticamente la forma en la que podemos resolverlo. Por ejemplo, el problema https://omegaup.com/arena/problem/La-especie-dominante-en-marte nos pide encontrar el número que más se repite en una secuencia, si además sabemos que ese número aparece al menos más de la mitad de las veces. Si estamos usando C++ y conocemos relativamente bien la biblioteca estándar del lenguaje, nuestro primer intento sería algo así:

```cpp
#include <iostream>
#include <map>

int main( ) {
 std::map<int, int> frecuencias;
 for (int n; std::cin >> n;) {
    frecuencias\[n\] += 1;
 }
 // revisar qué valor apareció más e imprimirlo
}
Si enviamos el código anterior, nos llevaremos la desagradable sorpresa de obtener \`MLE\` (memoria límite excedida). Aunque esta publicación no tiene por objetivo explicar cómo se resuelve el problema, sí podemos mencionar que lo adecuado es un \*algoritmo de streaming\* que surgió en el área de lo que ahora se conoce como \*Big Data\*. Entonces, el límite bajo de memoria es un intento de obligar al usuario a deducir dicho algoritmo, el cual usa únicamente tres variables enteras. Desafortunadamente, incluso el siguiente código...

```cpp
#include <iostream>

int main( ) {
 // leer la entrada y no hacer nada con ella
 // no nos sabemos el algoritmo y tenemos poca memoria :(
 for (int n; std::cin >> n;) {
    continue;
 }
}
¡También supera la memoria límite del problema!

Un usuario podría pensar (equivocadamente) que entonces el problema es imposible de resolver. Para evitar esta confusión, los usuarios de la plataforma deben tomar en cuenta lo siguiente:

\- Existe un único límite de memoria por problema, el cual es independiente del lenguaje de programación usado. En el problema descrito previamente, el autor no quiso aumentar artificialmente el límite de memoria sólo para aceptar envíos en todos los lenguajes, porque eso implicaría que alguien que use un lenguaje eficiente podría idear un algoritmo que no era el que el autor quería permitir. Entonces, es verdad que algunos problemas no se pueden resolver en ciertos lenguajes de programación, pero el autor debería garantizar que el problema se puede resolver de forma razonable en por lo menos un lenguaje de programación (de preferencia C y C++).
- La biblioteca \`<iostream>\` de C++ consume mucha más memoria de la que uno podría imaginar inicialmente. Esto se puede verificar resolviendo un problema de "Hola Mundo" usando \`<iostream>\` y luego comparándolo con uno que sólo usa \`<stdio.h>\`. Peor aún, basta incluir \`<iostream>\` para que el consumo de memoria del programa aumente, ya que la inclusión de ese archivo al menos provoca que los objetos globales \`std::cin\` y \`std::cout\` se inicialicen.

El siguiente código no calcula la respuesta correcta, pero al menos al menos no superará el límite de memoria :)

```cpp
#include <stdio.h>

int main( ) {
 // leer la entrada y no hacer nada con ella
 // no nos sabemos el algoritmo :(
 for (int n; scanf("%d", &n) == 1;) {
    continue;
 }
}
Esperamos que esta publicación les haya ayudado a tener una idea más cercana de cómo atacar cierto tipo de problemas inusuales y los invitamos a resolver el problema mencionado en el juez en línea.


```


```


```