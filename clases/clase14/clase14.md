# Clase 14 (7 de noviembre de 2023)

En esta clase nos hemos centrado en las operaciones para crear/modificar listas y repasar algunos recorridos vistos el día anterior:

## Ejercicio de recorridos (II): Menor
*Realice otra función que calcule el menor valor de una lista*

```python
def menor(l: list) -> int:
    m: int = l[0]
    for v in l:
        if v < m:
            m = v
    return m

# --------------- PRINCIPAL ---------------
lista: list = [10, 6, 8, -5, 3, 2, 24, -12, 10, 1]

print("El menor de la lista es", menor(lista))
```

## Ejercicio de recorridos (III): Posición del mayor
*Codifique una función que devuelva la posición que ocupa el menor valor de una lista*

```python
def pos_mayor(l: list) -> int:
    max=mayor(l)
    for indice in range(len(l)):
        if l[indice]==max:
            posicion_mayor = indice
    return posicion_mayor

def pos_mayor2(l: list) -> int:
    mayor:int = l[0]
    posicion = 0
    pos_final = 0
    for valor in l[1:]:
        posicion += 1
        if valor>mayor:
            mayor = valor
            pos_final = posicion
    
    return pos_final

def pos_mayor3(l: list) -> int:
    mayor: int = l[0]
    pos_mayor: int = 0
    for posicion in range(1, len(l)):
        if l[posicion] > mayor:
            mayor = l[posicion]
            pos_mayor = posicion
    return pos_mayor

def pos_mayor4(l: list) -> int:
    pos_mayor: int = 0
    for posicion in range(1, len(l)):
        if l[posicion] > l[pos_mayor]:
            pos_mayor = posicion
    return pos_mayor


# --------------- PRINCIPAL ---------------
lista: list = [10, 6, 8, -5, 3, 2, 24, -12, 10, 1]

m = pos_mayor4(lista)
print("El menor de la lista es", lista[m], "y está en la posicion", m)
```

## Ejercicio recorridos (IV): Buscar

*Dada una lista y un valor, realice una función que nos diga la posición donde está ese valor en la lista y si no está devuelva -1*

```python
# --------- FUNCIONES -------------
def buscar(l: list, x: int) -> int:
    pos = -1
    buscador = 0
    while pos == -1 and buscador < len(l):
        if l[buscador] == x:
            pos = buscador
        buscador += 1
    return pos
    
def buscar2(l: list, x: int) -> int:
    posicion = 0
    while posicion < len(l) and not (l[posicion] == x):
        posicion += 1
        
    if posicion < len(l):
        return posicion
    else:
        return -1  

# --------- PROGRAMA PRINCIAL -------------

l1: list = [1, 2, 3, 4]
l2: list = [5, 3, -1, 0]
l3: list = [5, 7, 3, -1, 8, 3, 4]
l4: list = [-3]

print(buscar(l3, 5))
print(buscar(l3, 4))
print(buscar(l3, -1))
print(buscar(l3, 10))
print(buscar(l3, -7))
```
## Ejercicio corto (I): Leer

*Función que lea 10 valores y los meta en una lista*

```python
# --------- FUNCIONES -------------
def leer_lista(n: int) -> list:
    l: list = []
    for i in range(n):
        valor = int(input("Dime un valor: "))
        l.append(valor) # También vale l = l +[valor]
    return l


# --------- PROGRAMA PRINCIAL -------------
MAX_VALORES: int = 10
lista: list = leer_lista(MAX_VALORES)
print("La lista leída es:", lista)
```

## Ejercicio corto (II): Suma de elementos

*Función que sume todos los valores de una lista*

```python
# --------- FUNCIONES -------------
def sumar_elementos(l: list) -> int:
    suma: int = 0
    for v in l:
        suma += v
    return suma


# --------- PROGRAMA PRINCIAL -------------
lista: list = [1, 3, 5, 8, 1, 2]
sum: int = sumar_elementos(lista)
print("La suma de los elementos de la lista", lista, "es", sum)
```

## Ejercicio corto (III): Estadísticas

*Función que nos devuelva el mayor, menor y media de una lista*

```python
def estadísticas(l: list) -> (float, int, int):
    suma: int = 0
    menor: int = l[0]
    mayor: int = l[0]
    for v in l:
        suma += v
        if menor > v:
            menor = v
        if mayor < v:
            mayor = v
    return suma/len(l), menor, mayor


# --------- PROGRAMA PRINCIAL -------------
lista: list = [1, 3, 5, 8, 1, 2]
media, men, may = estadísticas(lista)
print("Con la lista", lista, "su media es", media, "el mayor valor es", may,"y el menor es", men)
```
