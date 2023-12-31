# Clase 13: 06 de noviembre de 2023

En esta clase se introdujo el concepto de lista: conjunto de valores accesibles por índice.

Se vio cómo se creaba y principalmente cómo acceder a los diferentes valores y hemos visto cómo recorrer sus valores (tanto completamente como parcialmente).

## Ejercicio de acceso (transparencia 5)

Se ofrecen múltiples formas de acceder a diferentes valores:

```python
lista:list = [10, 6, 8, -5, 3, 2, 24, -12, 10, 1]

print("1) lista[3]:", lista[3])
print("2) lista[9]:", lista[9])
print("3) lista[99]: Error: IndexError: list index out of range")
print("4) lista[-1]:", lista[-1])
print("5) lista[-7]:", lista[-7])
print("6) lista[0:2]:", lista[0:2])
print("7) lista[2:5]:", lista[2:5])
print("8) lista[2:]:", lista[2:])
print("9) lista[:5]:", lista[:5])
print("10) lista[:]:", lista[:])
print("11) lista[0:5:1]:", lista[0:5:1])
print("12) lista[0:6:2]:", lista[0:6:2])
print("13) lista[1:7:2]:", lista[1:7:2])
print("14) lista[0:5:3]:", lista[0:5:3])
print("15) lista[1:6:2]:", lista[1:6:2])
print("16) lista[3::2]:", lista[3::2])
print("17) lista[:3:2]:", lista[:3:2])
print("18) lista[::2]:", lista[::2])
print("19) lista[1:5:]:", lista[1:5:])
print("20) lista[::-1]:", lista[::-1])
print("21) lista[7:5:-1]:", lista[7:5:-1])
print("22) lista[6:0:-2]:", lista[6:0:-2])
print("23) lista[7::-3]:", lista[7::-3])
print("24) lista[::]:", lista[::])
print("25) lista[-3::1]:", lista[-3::1])
print("26) lista[-5:8:-2]:", lista[-5:8:-2])
print("27) lista[-7:-3:2]:", lista[-7:-3:2])
print("28) lista[-5:-5]:", lista[-5:-5])
print("29) lista[-3:2:3]:", lista[-3:2:3])
print("30) lista[-1:-5:1]:", lista[-1:-5:1])
print("31) lista[:3:-1]:", lista[:3:-1])
print("32) lista[-3::-3]:", lista[-3::-3])
```

## Ejemplos iniciales de recorridos completos
*Escribir solo los valores positivos de una lista y sumar todos sus valores*

```python
def escribir_positivos(l: list) -> None:
  for v in l:
    if v > 0:
      print(v, end=" ")

def suma_lista(l: list) -> int:
  res = 0
  for v in l:
    res += v
  return res

def escribir_pos_positivos(l: list) -> None:
  for pos in range(len(l)):
    if l[pos] > 0:
      print(pos)

# --------------- PRINCIPAL ---------------
lista:list = [10, 6, 8, -5, 3, 2, 24, -12, 10, 1]

print(suma_lista(lista))

escribir_positivos(lista)
```

## Función esta
*Mira si un valor está en una lista o no*

En este caso se ofrecen varias alternativas:
* Con recorrido completo (función `esta`). Es poco recomendable ya que miras valores sin necesidad
* Recorrido incompleto con un booleano (función `esta2`). Está bien, pero realmente el valor lógico no es ncesario
* Recorrido incompleto sin booleano (función `esta3`). Mejor alternativa.

```python
# Diferentes versiones (la correcta es la última: esta3)

def esta(l: list, x: int) -> bool:
  encontrado: bool = False
  for v in l:
    if v == x :
      encontrado = True
  return encontrado

def esta2(l: list, x: int) -> bool:
  encontrado: bool = False
  i: int = 0
  while i < len(l) and not encontrado:
    if l[i] == x:
      encontrado = True
    i += 1
  return encontrado

def esta3(l: list, x: int) -> bool:
  i: int = 0
  while i < len(l) and l[i] != x:
    i += 1
  return i < len(l)

# --------------- PRINCIPAL ---------------
lista: list = [10, 6, 8, -5, 3, 2, 24, -12, 10, 1]

n: int = int(input("Dime un valor: "))

if esta3(lista, n):
  print(f"El valor {n} está en la lista")
else:
  print(f"No se encontró a {n} en la lista")
```

## Ejercicio de recorridos (I): Exite negativo
*Realice una función que compruebe si en una lista hay números negativos*

```python
def hay_negativos(l: int) -> bool:
  i: int = 0
  while i < len(l) and l[i] >= 0:
    i += 1
  return i < len(l)

# --------------- PRINCIPAL ---------------
lista: list = [10, 6, 8, -5, 3, 2, 24, -12, 10, 1]

if hay_negativos(lista):
  print(f"En la lista hay valores negativos")
else:
  print(f"La lista solo tiene valores positivos")
```
