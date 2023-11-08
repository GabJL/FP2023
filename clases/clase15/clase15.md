# Clase 15 (8 de noviembre de 2023)

En esta clase nos hemos centrado en las operaciones para crear/modificar listas y ejercicios avanzados sobre listas

## Ejercicio corto (IV): Primera y última

*Función que nos devuelva la primera y última aparición de un valor en la lista. Si no existe debe devolver -1 y -1*

```python
# --------- FUNCIONES -------------
def primero_y_último(l: list, valor: int) -> (int, int):
    first: int = -1
    last : int= -1
    for pos in range(len(l)):
        if l[pos] == valor:
            last = pos # Siempre actualizamos el último
            if first == -1: # Si el primero no lo hemos cambiado (vale -1) pues lo cambiamos solo esta vez
                first = pos
    return first, last


# --------- PROGRAMA PRINCIAL -------------
lista = [1, 3, 5, 8, 1, 2]
v = int(input("Dime un valor: "))
primer, último = primero_y_último(lista, v)
print("Con la lista", lista, "el valor", v, "aparece por primera vez en", primer,"y como última vez en", último)
```

## Ejercicio corto (V): Suma de vectores

*Función que sume dos vectores devolviendo el vector resultante*

```python
# --------- FUNCIONES -------------
def sumar_vectores(l1: list, l2: list) -> list:
    l3: list =[]
    for pos in range(len(l1)): # Ambas listas deben tener la misma longitud
        l3.append(l1[pos] + l2[pos])
    return l3


# --------- PROGRAMA PRINCIAL -------------
lista = [1, 3, 5, 8, 1, 2]
otra_lista = [9, 3, 4, -1, 0, -5]
lista_suma = sumar_vectores(lista, otra_lista)
print(lista, "+", otra_lista, "=", lista_suma)
```

## Ejercicio corto (VI): Lista de positivos

*Función que dado un vector nos devuelva otro solo con los valores positivos.*

```python
# --------- FUNCIONES -------------
def filtrar_positivos(l: list) -> list:
    res =[]
    for v in l:
        if v > 0:
            res.append(v)
    return res


# --------- PROGRAMA PRINCIAL -------------
lista = [9, 3, 4, -1, 0, -5]
filtrada = filtrar_positivos(lista)
print(lista, "filtrada a solo positivos", filtrada)
```

## Ejecicio complejo (I): ordenada?

*Realice una función que nos diga si una lista está ordenada o no*

```python
# --------- FUNCIONES -------------
def está_ordenada(l: list) -> bool:
    pos = 1
    while pos < len(l) and l[pos-1] <= l[pos]:
        pos += 1
    return pos >= len(l)


# --------- PROGRAMA PRINCIAL -------------
lista = [1, 3, 4, -1, 0, 5]
lista2 = [1, 5, 5, 8, 9]
if está_ordenada(lista):
    print("La lista", lista, "está ordenada")
else:
    print("La lista", lista, "NO está ordenada")

if está_ordenada(lista2):
    print("La lista", lista2, "está ordenada")
else:
    print("La lista", lista2, "NO está ordenada")
```

## Ejecicio complejo (II): Unir comunes sin repeticiones

*Realice una función que reciba dos listas y nos devuelva otra con los valores comunes y sin repetir*

```python
# --------- FUNCIONES -------------
def comunes_sin_repeticiones(l1: list, l2: list) -> list:
    res = []
    for v in l1:
        if v in l2 and v not in res:
            res.append(v)
    return res


# --------- PROGRAMA PRINCIAL -------------
lista = [1, 3, 1, 4, -1, 0, 5]
lista2 = [1, 5, 5, 1, 8, 9]
inter = comunes_sin_repeticiones(lista, lista2)
print(lista, "interseccion", lista2, "=", inter)
```

## Ejercicio complejo (III): Frecuencia notas

*Realice un programa que lea un número indeterminado y desconocido de notas (valores natural entre 0 y 10). Puede suponer que todas las notas son correctas y acaban con un -1. Como resultado debe escribir por pantalla la cantidad de notas de cada tipo (cuántos 0 hubo, cuántos 1, cuántos 2, …, cuántos 10).*

Solución sin lista de frecuencias (un tanto ineficiente=

```python
def leer_notas() -> list:
    nota: int = int(input())
    l: list = []
    while nota != -1:
        l.append(nota)
        nota = int(input())
    return l
    
def contar(l: list, valor: int) -> int:
    #return l.count(valor)
    contador: int = 0
    for v in l:
        if v == valor:
            contador += 1
    return contador

# Programa principal
l: list = leer_notas()

for nota in range(11):
    cantidad = contar(l, nota)
    print(nota, ":", cantidad)
```

Solución con lista de frecuencias:

```python
# --------- FUNCIONES -------------
def crear_frecuencias() -> list:
    f: list = []
    for i in range(11):
        f.append(0)
    return f
    # También podría simplificarse como return [0]*11


def escribir_frecuencias(f: list) -> None:
    for i in range(11):
        print(i, "->", f[i])


# --------- PROGRAMA PRINCIAL -------------
nota: int = int(input("Dime una nota: "))
frecuencias: list = crear_frecuencias()

while nota != -1:
    frecuencias[nota] += 1
    nota: int = int(input("Dime otra nota: "))

escribir_frecuencias(frecuencias)
```

