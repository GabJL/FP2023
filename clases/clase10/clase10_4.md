# Clase 10: 18 de octubre de 2022

En esta clase se introdujo la necesidad de dividir el código en pequeños trozos para facilitar su escritura y su reutilización. También vimos cómo se hacen y se usan funciones en python. Como ejemplo para ilustrar todo esto vimos el cálculo de un número combinatorio

## Ejemplo: Números combinatorios

La idea es hacer el cálculo de un número combinatorio que es la división entre m! y n!\*(m-n)! Como se observa se necesitan calcular 3 veces el factorial de diferentes valores y entonces crear una trozo de código que lo calcule y lo podamos reutilizar facilita mucho realizar el programa.

```python
m: int = int(input("Dime el valor de m: "))
n: int = int(input("Dime el valor de n: "))

factorial_m: int = 1
for i in range(2, m+1):
    factorial_m *= i

factorial_n: int = 1
for i in range(2, n+1):
    factorial_n *= i

factorial_m_n: int = 1
for i in range(2, m-n+1):
    factorial_m_n *= i

combinatorio: int = factorial_m / (factorial_n * factorial_m_n)

print("El resultado es", combinatorio)
```

```python
#Funciones
def factorial(N: int) -> int:
    res: int = 1
    for i in range(2, N+1):
        res *= i
    return res


# Programa principal
m: int = int(input("Dime el valor de m: "))
n: int = int(input("Dime el valor de n: "))
factorial_m: int = factorial(m)
factorial_n: int = factorial(n)
factorial_m_n: int = factorial(m-n)

combinatorio: int = factorial_m / (factorial_n * factorial_m_n)

print("El resultado es", combinatorio)
```

## Primos en un rango

Para mostrar las ventajas del uso funciones a la hora de simplificar el código, se hizo el ejercicio 3 de la práctica 4 donde se pide mostrar los números primos en un rango.

```python
n1: int = int(input("Dime un valor: "))
n2: int = int(input("Dime otro valor: "))

if n1 < n2:
    mayor = n2
    menor = n1
else:
    mayor = n1
    menor = n2

print("Los números primos entre", menor, "y", mayor, "son:", end=" ")
for numero in range(menor, mayor+1):
    divisores = 0
    for i in range(1, numero+1):
        if numero%i == 0:
            divisores += 1
    if divisores <= 2:
        print(numero, end= " ")
```

```python
# Funciones
def cantidad_divisores(n: int) -> int:
    # Generamos todos los valores entre 1 y n
    # Contamos los números que dividen a n
    contador: int = 0
    for i in range(1, n+1):
        # para cada valor, mirar si es divisor y contarlo en caso afirmativo
        if n%i == 0:
            contador += 1
    return contador


def es_primo(n: int) -> bool:
    # un número es primo si tiene 1 o 2 divisores únicamente
    if cantidad_divisores(n) <= 2:
        primo = True
    else:
        primo = False
    return primo


# Programa principal
# Leer 2 números
número1: int = int(input("Dime un número: "))
número2: int = int(input("Dime otro número: "))

# Calcular cuál es el mayor y menor de esos números
menor: int = min(número1, número2)
mayor: int = max(número1, número2)

# Mostrar los primos entre menor y mayor:
# 1.- Generar todos los valores entre menor y mayor
# 2.- Para cada valor mirar si es primo (si es primo lo mostramos)
print("Los números primos entre", menor, "y", mayor, "son:", end=" ")
for número in range(menor, mayor+1):
    if es_primo(número):
        print(número, end=" ")
```

## Cilindro 

*Realice dos funciones, una que calcule el área a partir del radio del círculo y otra que calcule su longitud.*

*Realice una función que calcule el área de un rectángulo.*

*Realice otra función que calcule el área del cilindro a partir de su radio y su altura. El área de un cilindro es la suma de sus componentes, es decir, es 2 veces área de la base (círculo) más el área del rectángulo.*

*Realice el programa principal que lea el radio y la altura del cilindro y nos muestre su área.*

```python
# import
import math


# Funciones
def área_círculo(radio: float) -> float:
    resultado = math.pi * radio * radio
    return resultado


def longitud_círculo(radio: float) -> float:
    return 2 * math.pi * radio


def área_rectángulo(base: float, altura: float) -> float:
    return base * altura


def área_cilindro(radio: float, altura: float) -> float:
    return 2 * área_círculo(radio) + área_rectángulo(longitud_círculo(radio), altura)


# Programa principal
r: float = float(input("Indique el radio: "))
h: float = float(input("Indique la altura: "))

print("El área del cilindro es", área_cilindro(r,h))
```
