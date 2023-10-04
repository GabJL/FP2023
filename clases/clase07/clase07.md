# Clase 7 (4 de octubre de 2023)

En esta clase repasamos el bucle `while` (rehicimos varios ejercicios de la [clase anterior](../clase06/clase06.md)). De hecho, en la actividad hemos resuelto resuelto variantes de los planteados

## Ejercicios cortos

### Ejercicio 1
*Lee 20 números y nos diga cuántos 0s hay*

Un elemento importante a destacar en este ejercicio, es que realmente no nos interesan los números concretos que hemos leído hasta el momento si no hay variable que nos almacene un resumen (de la parte que nos interese) de todos esos valores. Es decir, no nos interesa saber si el usuario ha metido 0 1 3 5 0 2 sino que hemos leído 2 ceros. Por ello, tendremos una variable `contador_de_0s` que nos almacene ese valor mientras que los números leídos los podemos ir machacando. Este tipo de variable que resumen los datos contando los valores que cumplen cierta propiedad se denominan **contadores**.

```python
MAX: int = 20 # Valores a leer para las pruebas se puede bajar a algo más manejable (3 o 4)

contador_de_0s: int = 0 # No hemos leído ningún 0
num_veces: int = 0 # Número de números leídos

while num_veces < MAX:
  num: int = int(input("Dime un número: ")) # Valor actual
  if num == 0:
    contador_de_0s += 1
  num_veces += 1

print("Se han leído", contador_de_0s, "0s")
```

### Ejercicio 2
*Lee 10 números y nos diga su suma*

Similar al ejercicio anterior pero en este caso no nos interesa contar, sino sumar (acumular) todos los valores. Estas variables se denominan **acumuladores**.

```python
MAX: int = 10 # Valores a leer para las pruebas se puede bajar a algo más manejable (3 o 4)

suma: int = 0 # No hemos leído ningún valor por lo tanto la suma actual es 0
num_veces: int = 0 # Número de valores leídos

while num_veces < MAX:
  num: int = int(input("Dime un número: ")) # Valor actual
  suma += num
  num_veces += 1

print("La suma vale", suma)
```

### Ejercicio 3
*Modifique el anterior para calcular la media de los números leídos*

Sabiendo la suma de los valores, calcular la media es bastante sencillo, ya que solo hay que dividir esa suma entre el número de valores (10).

```python
MAX: int = 10 # Valores a leer para las pruebas se puede bajar a algo más manejable (3 o 4)

suma: int = 0 # No hemos leído ningún 0

num_veces: int = 0

while num_veces < MAX:
  num = int(input("Dime un número: "))
  suma += num
  num_veces += 1

print("La media vale", suma/10)
```

### Ejercicio 4
*Lee 30 números y nos muestre cuántos números pares y cuántos impares hay*

Similar al primero de los cortos, pero ahora con dos contadores (uno para pares y otro para impares). Realmente el de impares podría deducirse del de pares.

```python
MAX: int = 20 # Valores a leer para las pruebas se puede bajar a algo más manejable (3 o 4)

pares: int = 0
impares: int = 0

num_veces: int = 0

while num_veces < MAX:
  num = int(input("Dime un número: "))
  if num%2 ==  0:
    pares += 1
  else:
    impares += 1
  num_veces += 1

# Se podría evitar contar los impares y calcularlo como num_veces - pares

print("Se han leído", pares, "números pares y", impares, "números impares")
```

### Ejercicio 5
*Modifique el anterior ejercicio para que en vez de leer 30 números, lea hasta que el número sea negativo.*

Este ejemplo es importante ya que añade el concepto de **lectura adelantada**. Esto ocurre cuando la condición del bucle depende de lo que leemos y entonces hay que leer un valor previo al bucle y nos obliga a un esquema similar al siguiente:

```python
x = input(...) # Leemos
while condicion_que_depende_de_x: # Evaluar la condición 
  Código # Cálculos 
  x = input(...) # Leemos de nuevo
```

```python
pares: int = 0
impares: int = 0


num: int = int(input("Dime un número: "))
while num >= 0:
  if num%2 ==  0:
    pares += 1
  else:
    impares += 1
  num = int(input("Dime un número: "))

print("Se han leído", pares, "números pares y", impares, "números impares")
```

### Ejercicio 6
*Modifique el 3 (media) para que acabe cuando leamos un 0*

En este caso como en el ejercicio anterior hay que emplear lectura adelantada. Además, como dividimos entre la cantidad de veces que leemos, hay que controlar si no se ha leído ningún valor correcto:

```python
suma: int = 0 # No hemos leído ningún 0

num_veces: int = 0

num: int = int(input("Dime un número: "))
while num != 0:
  suma += num
  num_veces += 1
  num = int(input("Dime un número: "))

if num_veces > 0:
  print("La media vale", suma/num_veces)
else:
  print("No se leyeron números")
```

### Ejercicio 7
*Lee un texto de 20 letras (una a una) e indique si aparece una vocal o no.*

En este ejercicio necesitamos una variable de las llamada centinelas (o `flags`) que solo tiene dos valores, `True` si ha ocurrido un evento o `False` si no. Inicialmente la ponemos a falso ya que no se ha leído nada y cuando se detecte el evento (lectura de una vocal) la ponemos a cierto.

```python
MAX: int = 20

hay_vocales: bool = False # Aún no hemos encontrado ninguna vocal

num_veces: int = 0

while num_veces < MAX:
  letra = input("Dime una letra: ")
  if letra == "a" or letra == "e" or letra == "i" or letra == "o" or letra == "u":
    hay_vocales = True
  num_veces += 1

if hay_vocales:
  print("Se ha leído alguna vocal")
else:
  print("No había vocales en el texto")
```


### Ejercicio 8
*Modifique el 7 para que lea a lo sumo 20 letras (cuanto sepa si hay debe parar).*

Una forma sencilla de resolver este ejercicio es añadiendo la condición de que no se haya leído ninguna vocal al bucle (ese valor está almacenado en la variable centinela `hay_vocales`).

```python
MAX: int = 20

hay_vocales: bool = False # Aún no hemos encontrado ninguna vocal

num_veces: int = 0

while num_veces < MAX and not hay_vocales:
  letra = input("Dime una letra: ")
  if letra == "a" or letra == "e" or letra == "i" or letra == "o" or letra == "u":
    hay_vocales = True
  num_veces += 1

if hay_vocales:
  print("Se ha leído alguna vocal")
else:
  print("No había vocales en el texto")
```

### Ejercicio 9
*Hacer un programa que lea dos números pero deben ser diferentes. Si se leen dos números iguales se debe repetir la petición de valores tantas veces como sea
necesaria hasta que consigamos que sean diferentes.*

Este ejemplo es peculiar ya que la condición del bucle depende de los valores leídos y habría que hacer lectura adelantada, pero lo que ponemos como lectura adelantada y el contenido del bucle completo es igual. Para estos casos nos podemos ahorrar la lectura adelantada e inicializar las variables de forma que al inicio entre la primera vez.

```python
# Vale cualquier par de valores siempre que sean los mismos para forzar que entre en el bucle.
n1: int = 0
n2: int = 0
while n1 == n2:
  primt("Los números deben ser diferentes")
  n1 = int(input("Dime un número: "))
  n2 = int(input("Dime otro número: "))
```

### Ejercicio 10
*Lea número hasta encontrar uno positivo y muestre el mayor.*

Este ejercicio quizás es uno de los más complejos de estos cortos:
* Necesitamos lectura adelantada (hay que leer mientras el valor sea negativo).
* Necesitamos una variable para almacenar el mayor leído hasta el momento (variable `mayor`).
* Esta variable se actualiza si leemos una mayor (`if mayor < n: mayor = n`).
* El valor inicial de la variable debe ser el primer valor leido (la lectura adelantada).

```python
n: int = int(input("Dime un número: "))
mayor: int = n

while n < 0:
  if n > mayor:
    mayor = n
  n = int(input("Dime un número: "))

if mayor >= 0:
  print("No se leyeron números válidos")
else:
  print("El mayor valor leído fue", mayor)
```

