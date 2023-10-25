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
+++ 
