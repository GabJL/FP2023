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

## Ejercicio de recorridos (III): Posición del menor
*Codifique una función que devuelva la posición que ocupa el menor valor de una lista*

```python
def posición_menor(l: list):
    pos_menor: int = 0
    for i in range(len(l)):
        if l[i] < l[pos_menor]:
            pos_menor = i
    return pos_menor

# --------------- PRINCIPAL ---------------
lista: list = [10, 6, 8, -5, 3, 2, 24, -12, 10, 1]

m = posición_menor(lista)
print("El menor de la lista es", lista[m], "y está en la posicion", m)
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
