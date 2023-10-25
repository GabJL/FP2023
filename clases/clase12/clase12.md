# Clase 12 (25/10/2023)

En esta clase terminamos el tema 4 y se hicieron algunos ejercicios de parciales de años previos.

## Divisón Entera

*Realice una función que recibidendo 2 valores enteros, devuelva el cociente y resto de la división entera. El programa principal debe leer los valores y escribir los resultados*

```python
# Funciones
def division_entera(a: int, b: int) -> (int, int):
  cociente: int = a // b
  resto: int = a % b
  return cociente, resto

# Programación Principal
n1: int = int(input("Dime un número: "))
n2: int = int(input("Dime otri número: "))

c, r = division_entera(n1, n2)

print("Cociente: ", c)
print("Resto", r)
```

## Ejercicio Primos en un Rango

*Lea un número natural (n1) entre 1 y 20 (si no está en el rango volverá a pedirlo). Luego vuelva a leer otro número natural (n2) entre n1 y 100. A continuación, escribirá todos los primos entre n1 y n2*

*a) ¿Qué funciones identifica en este ejercicio?*

*b) ¿Cuál sería la cabecera de cada uno de ellos?*

*c) Realice el programa principal usando esas funciones*

*d) Implemente ahora las funciones*

```python
# Funciones
def leer_en_range(minimo: int, maximo:int) -> int:
  x: int = int(input("Dime un número entre " + str(minimo) + " y " + str(maximo) + ": "))
  while x < minimo or n > maximo:
    print("El número no está en el rango.")
    x = int(input("Dime un número entre " + str(minimo) + " y " + str(maximo) + ": "))
  return x


def es_primo(num: int) -> bool:
  div: int = 2
  while num % div != 0:
      div += 1
  return div >= num

def escribir_primos(a. int, b: int) -> None:
  print("Los primos en el rango", a, "-", b,"son: ", end="")
  for n in range(a, b+1):
    if es_primo(n):
      print(n, end=" ")


# Programa principal
n1: int = leer_en_range(1, 20)
n2: int = leer_en_range(n1, 100)

escribir_primos(n1, n2)
```

## Ejercicio 2 de Parcial 2016
*Hacer un programa que pida números enteros al usuario hasta 0. Después de esto, el programa debe escribir el mayor y menor número de todos ellos. Los números introducidos pueden ser negativos*

```python
n: int = int(input()) # Lectura adelantada
mayor: int = n
menor: int = n
while n != 0:
    if n > mayor:
        mayor = n
    if n < menor:
        menor = n    
    n = int(input())
    
print(mayor, menor)
```

## Ejercicio 4 de Parcial 2016
*Hacer un programa que pinte un triángulo de altura h como el ejemplo que sigue, que tiene en el ejemplo altura 6*

```
*.*.*.*.*.*.
.*.*.*.*.*.
..*.*.*.*.
...*.*.*.
....*.*.
.....*.
```

```python
altura: int = int(input("Altura: "))
num_lineas: int = altura
# Primera línea
num_puntos: int = 0
num_asteriscos: int = altura

for l in range(num_lineas):
    # Dibujar una línea
    # Dibujar muchos puntos
    for e in range(num_puntos):
        print(".", end="")
    # dibujar muchos *.
    for a in range(num_asteriscos):
        print("*.", end= "")
    # Salto de linea
    print()
    # Cómo cambia al resto de líneas
    num_asteriscos -= 1
    num_puntos += 1
```

## Ejercicio 5 del parcial de 2016
*Hacer un programa que pida números enteros hasta el 0. El programa luego debe indicar si todos los números estaban en orden creciente*

```python
n: int = int(input())
es_creciente: bool = True
anterior: int = n
while n != 0:
    if anterior > n:
        es_creciente = False
    
    anterior = n
    n = int(input())
    
if es_creciente:
    print("La serie es creciente")
else:
    print("Hay algún valor que baja")
```

## Ejercicio 3 de parcial del 2022
*Realice un programa que lea un valor (la altura) y dibuje la siguiente figura. El punto representa un espacio por hacer que sea más sencillo de visualizar. No se permite el uso del operador * para textos.*

```
Altura: 4
...*..****
..***..***
.*****..**
*******..*
```

```python
altura: int = int(input("Altura: "))
num_lineas: int = altura
# Primera línea
num_puntos: int = altura -1
num_asteriscos: int = 1
num_asteriscos2: int = altura

for l in range(num_lineas):
    # Dibujo una línea
    # muchos puntos
    for p in range(num_puntos):
        print(".", end="")
    # muchos asteriscos
    for a in range(num_asteriscos):
        print("*", end= "")
    # Dos puntos
    print("..", end="")
    # muchos asteriscos
    for a in range(num_asteriscos2):
        print("*", end="")
    # Salto de línea
    print()
    # Cómo cambiamos al ir a la línea siguiente
    num_puntos -= 1
    num_asteriscos += 2
    num_asteriscos2 -= 1
```

## Ejercicio 5 de parcial de 2021
*Realice un programa que lea un número entero positivo, n, y nos devuelva el menor número que sea múltiplo de 13 pero que sea mayor de n. Por ejemplo, para un n = 7 nos devolvería 13, para n = 100 devolvería 104 o para n = 39 nos devolvería 52.*

```python
n: int = int(input())

n += 1

while n%13 != 0:
    n += 1
    
print(n)
```

## Ejercicio 2 de parcial 2020
*Hacer un programa 02.mayormult5.py que pida números enteros al usuario hasta leer el 0. Después de esto, el programa debe escribir cuál de ellos es el mayor divisible por 5. Por ejemplo: Con 1 12 2 3 4 0 sería 0; con 1 5 10 3 15 0 sería 15; con 0 sería 0.*

```python
n: int = int(input())
contador: int = 0
menor: int = n

while n != 0:
    if n % 5 == 0:
        contador += 1
        if menor > n or menor%5 != 0:
            menor = n
    n = int(input())
print(menor)
print(contador)
```
