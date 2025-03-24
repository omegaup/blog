---
title: 'Solución a "Comesolo"'
author: 'lhchavez'
author_email: 'lhchavez@omegaup.com'
date: Sat, 14 Sep 2013 05:21:32 +0000
draft: false
tags: ['Solution', 'Etapa 1', 'Examen 5', 'felix', 'lhchavez', 'preselectivo', 'solución', 'Soluciones Preselectivo 2014']
math: true
aliases: ['/solucion-a-comesolo']
---

**Concurso:** [Preselectivo para la IOI 2014, Etapa 1, Problemset 8](https://omegaup.com/arena/problem/comesolo) **Autor:** [lhchavez](http://lhchavez.com) **Fuente**: Félix

Este problema es especial porque es el primero en omegaUp de solo salida! Usualmente lo que debes esperar cuando te enfrentes con uno de esos problemas es que sea un problema NP que no tiene una solución rápida, y usualmente te pedirán que te aproximes lo más posible a la solución óptima. Esto significa que te vas a tener que valer de técnicas ad-hoc y heurísticas para sacar puntos.

La solución del problema es bastante sencilla de explicar: haz una búsqueda en profundidad intentando todos los posibles movimientos por fuerza bruta hasta que te salga una solución aceptable e imprímela. El problema es que esta estrategia es $latex O(n!)$, y como $latex n$ puede valer hasta 30x30, puedes esperar que el programa corra varios milenios antes de encontrar la solución óptima. Hay tres trucos (en orden de importancia) para obtener una solución decente en un tiempo razonable:

*   No repetir estados.
*   No "clavarse" con soluciones que parece que son muy buenas, pero en realidad llevan a callejones sin salida.
*   Encontrar una manera de darle prioridad a los estados que tengan más probabilidad de llegar a una solución buena.

La estrategia que yo personalmente seguí fue que cada que encontraba un nuevo estado, obtenía su [hash](http://es.wikipedia.org/wiki/Funci%C3%B3n_hash) (que resultaba en un entero de 64 bits) y verificaba si no lo había visitado usando una tabla de hash[\*](#note). Si no la había visitado, encontraba todos los estados vecinos (todos los tableros que resultaban de hacer un movimiento válido) y los guardaba en una fila de acuerdo a la cantidad de puntos (entre más puntos, más adelante en la fila). Luego, elegía aleatoriamente un estado de la fila dándole prioridad a los que estaban más adelante (pues son los que tienen mayor probabilidad de llegar a una buena solución), lo cual también me evitaba seguir un único camino donde me podría atorar. Repetí eso hasta que se me terminó la memoria de la computadora e imprimí la mejor solución.

A continuación, el pseudocódigo de la solución:

```cpp
class Estado:
  int puntos = 0
  bool\[N\]\[N\] tablero
  Estado padre = null

  def \_\_init\_\_(Estado p):
    puntos = p.puntos
    tablero = p.tablero
    padre = p

  def hash():
    # Puedes usar cualquier algoritmo que genere un entero de 64 bits
    # a partir de tablero y puntos. Este es el más sencillo.
    hash = puntos
    for i in range(0, N):
      hash = ((hash << 7) | (hash >> 53)) ^ tablero\[i\]
    return hash

  def siguientes(queue\[300\] colas):
    # Para todas las celdas (i, j) del tablero...
    for i in range(0, N):
        for j in range(0, N):
          # Si la celda tiene una pieza...
          if tablero\[i\]\[j\]:
            # Para todos los vecinos contiguos (i+k, j+l)...
            for k in range(-1, 2):
              for l in range(-1, 2):
                # Asegúrate que se haya movido \_algo\_.
                if k == 0 && l == 0: continue
                # Y que pueda brincar dentro del tablero.
                if j + 2 \* l < 0 or j + 2 \* l >= N: continue
                # Y que haya brincado una pieza.
                if not tablero\[i + k\]\[j + l\]: continue
                # Y que el lugar a donde brinca esté desocupado.
                if tablero\[i + 2 \* k\]\[j + 2 \* l\]: continue
                
                hijo = new Estado(this)
                # Aumenta la puntuación del hijo
                hijo.puntos++
                # Borra la ficha original y la "comida".
                hijo.tablero\[i\]\[j\] = hijo.tablero\[i + k\]\[j + l\] = \\
                  False
                # Agrega la ficha en su posición final.
                hijo.tablero\[i + 2 \* k\]\[j + 2 \* l\] = True
                # Agrégala a la cola correspondiente.
                colas\[hijo.puntos\].push(hijo)

def elige\_estado():
  # Número aleatorio entre 0 y 1.
  r = (random() / (float)RAND\_MAX)
  # El índice de la última cola que estuvo llena.
  ultimolleno = -1
  # La cola que se está considerando.
  x = 0
  # Elige la cola con mayores puntos que no esté vacía como
  # primera opción.
  for i in range(0, N):
    if not colas\[i\].vacio():
      x = i
  # La primer cola tiene probabilidad de 31% de ser elegida.
  # La segunda cola tiene probabilidad de 21%, la tercera 14%,
  # la cuarta 10% y así sucesivamente.
  while x >= 0:
    if not colas\[x\].vacio():
      ultimolleno = x
    x--
    r \*= 1.45
    if r >= 1 and ultimolleno != -1 break
  if ultimolleno == -1: return Null
  return colas\[lastfull\].pop()

queue\[300\] colas
hashtable estados\_visitados

\# lee el estado original
colas\[0\].push(estado\_original)
Estado mejor = estado\_original

while no\_se\_haya\_terminado\_la\_memoria():
  Estado s = elige\_estado()
  # Si ya no hay más estados por visitar,
  # encontramos la respuesta óptima en algún punto.
  if s == Null: break
  # Actualiza |mejor| si hay una respuesta mejor.
  if mejor.puntos < s.puntos: mejor = s
  # Repetir estados es malo.
  if s.hash() in estados\_visitados: continue
  estados\_visitados.add(s.hash())
  # Agrega todos los vecinos.
  s.siguiente(colas)

\# A partir de este punto, |mejor| contiene la mejor solución. Podemos
# saber qué movimiento se hizo para llegar a él comparando las
# diferencias entre el tablero de |mejor.padre| y |mejor|. Ya solo es
# cuestión de imprimir el resultado y listo.
\* Aquí mucha gente se va a quejar porque solo guardar el hash abre la puerta a que haya dos estados que puede tener hasta 900 bits que tengan el mismo hash de 64 bits (por el [principio del palomar](http://es.wikipedia.org/wiki/Principio_del_palomar)) y esté considerando que ya se visitó un estado que en realidad es nuevo. Si haces las cuentas, la probabilidad de colisión es negligible: la cantidad de estados que podía visitar en mi computadora (27 millones) es significativamente más pequeña que el número de estados necesarios para que la probabilidad de colisión sea de 1% ($latex \\approx 10^{135}$, por la [paradoja del cumpleaños](http://es.wikipedia.org/wiki/Paradoja_del_cumplea%C3%B1os)).


```