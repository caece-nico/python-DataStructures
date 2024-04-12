# DataStructures & Algorithms

1. [Introduccion](#1.-Introduccion)
    - [Big 0 - 0(n)]()
    - [Big 0 - 0(n^2)]()
    - [Big 0 - 0(1)]()
    - [Big 0 - 0(log n)]()


## 1. Introduccion

__Big 0__ Es una forma de comparar dos codigos, para determinar que tan eficientes son al momento de ejecutar.


Por ejemplo. Si tenemos __codigo 1__ y __codigo 2__. El primero ejecuta en 15'' y el segundo en 4'. Podemos decir que el primero es mas eficiente en tiempo. A esto se llama __time complexity__. 

### Time Complexity.

Lo interesante de _time complexity_ es que no se mide en tiempo porque si el codigo 1 ejecuta en una computadora 4 veces más rápida que el codigo 2, la métrica estaría distorsionada.
Se mide en el _numero de operaciones_ que necesita para completar algo.
__La mayor parte del tiempo vamos a usar time complexity__

### Space Complexity


Otra medida es __Space Complexity__, Si lo que nos interesa es el __correcto uso de la memoria__ entonces nos fijamos que algoritmo hace menos uso de la misma sin importar el tiempo que demora.
Quizás el codigo 1 demora 15'' pero usa el 75% de la memoria mientras que el codigo 2 demora 4' pero usa el 1%. Si lo que buscamos es __Space complexity__ gana el codigo 2.


### El peor escenario.

Ejemplo

|letra|letra griega|uso|ascii|
|-----|------------|---|-----|
|omega|h|Es para representar el mejor caso posible|alt + 937|
|theta|h|Es para representar el caso que no es ni el mejor ni el peor.|alt + 920|
|omicron|h|Es el peor caso de todos - es el llamado big 0|alt + 927|

__uso__

Tenemos una lista con 7 elementos y hacemos un algoritmo de búsqueda.


|1|2|3|4|5|6|7|
|-|-|-|-|-|-|-|

En el mejor escenario buscamos el número 1, que es el primer elemento y lo encontramos en __una operacion__ en cambio el peor escenario es buscar el numero 7 que lo encontramos en __7 operaciones__

|letra|numero|
|-----|------|
|omega|1|
|theta|4|
|omicron|7|

__Cuando hablamos de Big 0 no existe un mejor caso o caso intermedio, siempre estamos hablando del peor caso__

### big 0 - 0(n)

Es el caso mas sencillo. Tenemos 0(n) cuando tenemos una funcion que ejecuta n operaciones. POr ejemplo un __for loop__.

```python
def ejecuta_funcion(n):
    for i in range(n):
        print(n)
```

En este ejemplo pasamos n que será el numero de iteraciones para mostrar el __print()__

Graficamente es una linea recta o __porporcional__ donde la cantidad de operaciones aumenta proporcionalmente al numero __n__

![](./img/0(n).png)

### ¿Cómo podemos simplicar nuestra big 0?

1. El primer método se llama __drop constants__

Tenemos el mismo ejemplo anterior pero esta vez con dos __for loop__

```python
def ejecuta_funcion(n):
    for i in range(n):
        print(i)

    for j in range(n):
        print(j)
```

Estas operaciones se van a ejecutar 20 veces y por intuicion podemos escribir

__0(2n)__ porque tenemos dos __for loop__ para simplificarlo __eliminamos la constante__ y queda __0(n)__.

### Big 0 - 0(n^2)

Tenemos un __for loop anidado__. 

Ejemplo:

A la funcion anterior le pasamos __n__ pero los __for loops__ estarán uno dentro del otro.

```python
def ejecuta_funcion(n):
    for i in range(i):
        for j in range(j):
            print(i,j)
```

Este código se __ejecuta 100 veces si n = 100__ ya que una fila (i) queda fija mientras que la otra (j) itera de 0 a n.
Podemos deducir que es __n * n__ o __n^2__

En el gráfico vemos que es __menos eficiente que 0(n)__ porque para menos valores realiza mas operaciones.

![](./img/0(n-times-2).png)


### ¿Cómo podemos simplificar big 0?

2. Otro ejemplo para simplificar Big 0 es con la técnica __drop Non-Dominants__.

Ejemplo, Siguiente la funcion anterior, agregamos un __for loop__ por fuera del __loop anidado__

```python
def ejecuta_funcion(n):
    for i in range(n):
        for j in range(n)
        print(i,j)

    ##luego

    for z in range(n):
        print(z)        
```

En el caso que __n=10__, primero realiza 100 operaciones para mostrar la combinacion __(i,j)__ y luego otras 10 para mostrar __(z)__ entonces podemos deducir que __big 0__ quedaria así:

__0(n^2 + n)__ pero si lo pensamos bien, no importa que tan grande sea __n__ siempre será __muy inferior__ a __n^2__ por lo que no afectaría al resultado.
Entonces como __n__ no es el termino dominante, __lo sacamos__ y la notación queda:

__0(n^2)__

### Big 0 - 0(1)

Es la más eficiente big 0. A medida que incrementamos __n__ aumenta el número de operaciones.

Por ejemplo:

```python
def ejecuta_funcion(n):
    return n + n
```

En este ejemplo no importa que tan grande sea __n__ siempre será una única operación la que se ejecute haciendo que __big 0__ sea __0(1)__

Aún sin hacemos:

```python
return n + n +n
```
podemos suponer que __Big 0__ sería __0(2)__ pero por simplificación queda __0(1)__

Graficamente vemos que:

![](./img/0(1).png)

A medida que aumentamos __n__ la cantidad de operaciones permanece __lineal__.


### Big 0 - 0(log n)

Es el segundo tipo de algoritmos más eficiente. Casi tanto como el __lineal 0(1)__.

Ejemplo:

Tenemos una una lista con 8 elementos y buscamos el valor 1.

|1|2|3|4|5|6|7|8|
|-|-|-|-|-|-|-|-|

Recordando que __big 0__ es el peor de los casos posibles si hacemos una búsqueda lineal necesitariamos __8 operaciones__ o __o(n)__ pero podemos aplicar un algoritmo de busqueda y partir a la mitad la lista.

1. Primera iteracion. Partimos a la mitad

|1|2|3|4|
|-|-|-|-|

2. Segunda iteracion. Patrimos a la mitad

|1|2|
|-|-|

3. Tercer iteracion. Partimos a la mitar

|1|
|-|

Despues de tres iteraciones partiendo a la mitad la lista encontramos el valor 1.

__Explicacion__

Dijimos que partimos a la mitad __dividimos por 2__ y el total de elementos en la lista es __8__, entonces:

__2^x=8__ ¿Qué valor puede ser __x__?

__x = 3__ entonces tenemos

__2^3 = 8__ lo que es lo mismo a tener __log (en base 2) de 8 = 3__

En este ejemplo vemos que para encontrar un número __x__ en una lista de __8 elementos__ necesitamos 3 operaciones, pero si tuvieramos una lista de __1073741824 elementos, mas de un billón__ si la búsqueda fuera lineas necesitariamos la misma cantidad de operaciones que elementos __en el peor de los casos__ pero si usamos el algoritmo de buscar dividiendo por dos seria:

__2^x=1073741824__ esto es igual a 31. 

Solo necesitariamos 31 operaciones para encontrar un numero x.

Graficamente se ve así.

![](./img/0(log%20n).png)

Bastante parecido y eficiente a 0(1) para valores muy grandes.