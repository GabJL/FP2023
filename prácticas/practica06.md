# Práctica 6

## p6e01.dni.py (★✰✰✰✰) 
*Desarrollar una función que devuelva la letra del DNI. Los números del DNI en España están compuestos de 8 dígitos y de una letra que sirve de comprobación. Para calcular la letra se obtiene el resto de dividir el número por 23; el número obtenido, entre 0 y 22, sirve entonces para seleccionar la letra de la siguiente lista de 23 letras: `TRWAGMYFPDXBNJZSQVHLCKE`. Podemos obtener directamente la letra usando la expresión `"TRWAGMYFPDXBNJZSQVHLCKE"[numDNI % 23]`. Pruébelo con su DNI.*

*__OBJETIVOS__: Función simple.*

```python
def letra_dni(dni: int) -> str:
    letra = "TRWAGMYFPDXBNJZSQVHLCKE"[dni % 23]
    return letra

# ------ PROGRAMA PRINCIPAL ------------------
dni: int = int(input("Introduce tu DNI (números): "))

print("Tu DNI completo es: ", dni, letra_dni(dni), sep="")
```

## p6e02.purga.py (★★✰✰✰) 
*Hacer una función que reciba una lista de valores, y devuelva la misma lista con los elementos en el mismo orden, pero sin repetir. Por ejemplo: `purga([3, 1, 3, 2, 2])` → `[3, 1, 2]`.*

*__NOTA__: Para hacerlo es muy útil (de nuevo) usar el operador `in`. En cierto sentido es parecido al anterior.*

*__OBJETIVOS__: Diseño de algoritmos.*

```python
def purga(l: list) -> list:
    res: list = []
    for v in l:
        if v not in res:
            res.append(v)
    return res

# Programa principal
print(purga([3, 1, 3, 2, 2]))
```

## p6e03.diferencia.py (★★★✰✰) 
*Recibiendo dos listas a y b, hacer una función que devuelva su diferencia. La diferencia de una lista respecto a otra son los elementos que hay en la primera pero que no están en la segunda. Si un elemento está más de una vez en la primera, pero también aparece al menos una vez en la segunda, se quitan todos. Por ejemplo: `dif([1,2,3,2,4], [2,4])` → `[1,3]`.*

*__NOTA__: Usar: `if not item in r:`*

*__OBJETIVOS__: Recorrido “anidado” de listas. Generación de nuevas listas.*

```python
def diferencia(a: list, b: list) -> list:
    l: list = []
    for v in a:
        if v not in b:
            l.append(v)
    return l


# Programa principal
print(diferencia([1, 2, 3, 4, 2, 8, 9], [1, 2, 9]))
```
## p6e04.moda.py (★★★★★) 

*Realizar una función que reciba una lista y nos devuelva la moda (el elemento más repetido de la lista). Si varios elementos aparecen la misma cantidad de veces devuelva el primero. Por ejemplo: `moda([1,2,3,2,3,2,4])` → `2` o `moda([1,1,2,2,3,4])` → `1`.*

*__NOTA__: Use la función `count` de las listas para sabes cuántas veces aparece un elemento de la lista.*

*__OBJETIVOS__: Uso de algoritmos ya conocidos adaptados a situaciones ligeramente diferentes.*

```python
def moda(l: list) -> float:
    mas_repetido: float = l[0]
    repeticiones_mas: int = l.count(l[0])
    
    for v in l[1:]: # Nos saltamos el primero porque ya lo hemos considerado
        rep_actual = l.count(v)
        if rep_actual > repeticiones_mas:
            repeticiones_mas = rep_actual
            mas_repetido = v
    return mas_repetido

# Programa principal

print(moda([1,2,3,2,3,2,4]))
print(moda([1,1,2,2,3,4]))
```

## p6e05.mediana.py] (★★★★✰) 
*Realizar una función que reciba una lista y nos devuelva la mediana. La mediana de una serie de números es aquel número que hace que la mitad de los números de la serie sea inferior a él y la otra mitad son superiores a él. Si ordenamos la lista, la mediana será el elemento central si la cantidad de elementos es impar o la media de los dos elementos centrales si el tamaño de la lista es par. Por ejemplo: `mediana([1,5,2,4,3])` → `3` o `mediana([1,6,5,2,3,4])` → `3.5`.*

*__NOTA__: Use la función `sort` de las listas para ordenar la lista.*

*__OBJETIVOS__: Entendimiento e implementación de algoritmos descritos textualmente.*

```python
def mediana(l: list) -> float:
    l.sort()
    mitad = len(l) // 2
    if len(l) % 2 == 0:
        m = (l[mitad] + l[mitad-1])/2
    else:
        m = l[mitad]
    return m

# Programa principal

print(mediana([1,5,2,4,3]))
print(mediana([1,6,5,2,3,4]))
```

## p6e06.intersección.py (★★★★✰) 

*Recibiendo dos listas a y b, hacer una función que devuelva su intersección. La intersección son los elementos que están en ambas. Si un elemento está más de una vez en la primera o en la segunda, ponerlo sólo una vez en la intersección. Por ejemplo: `intersección([1,2,3,2,4], [2,4,8])` → `[2,4]`.*

*__OBJETIVOS__: Diseño de algoritmos.*

```python
def intersección(l1: list, l2: list) -> list:
    res: list = []
    for v in l1:
        if v in l2 and v not in res:
            res.append(v)
    return res

# Programa principal
print(intersección([1, 2, 3, 2, 4], [2, 4, 8]))
```

## p6e07.normalizar.py (★★★★✰) 
*Realizar una función que reciba una lista y nos devuelva otra normalizada entre 0 y 1. Para normalizar una lista l debe aplicar a cada elemento la siguiente ecuación:*

`nuevo_valor = (valor – mínimo_de_l) / (máximo_de_l – mínimo_de_l)`

*Por ejemplo: `normalizar([1, 4, 0, 5])` → `[0.2, 0.8, 0.0, 1.0]`*

*__OBJETIVOS__: Entendimiento e implementación de algoritmos descritos textualmente. Uso de mecanismos ya vistos en clase.*

```python
def minimo(l: list) -> float:
    mini: float = l[0]
    for v in l[1:]:
        if v < mini:
            mini = v
    return mini

def maximo(l: list) -> float:
    maxi: float = l[0]
    for v in l[1:]:
        if v > maxi:
            maxi = v
    return maxi

def normalizar(l: list) -> list:
    mini: float = minimo(l)
    maxi: float = maximo(l)
    
    res: list = []
    for v in l:
        res.append( (v - mini) / (maxi - mini) )
    return res

# Programa principal
print(normalizar([1, 4, 0, 5]))
```

## p6e08.nombres.py (★★★★★) 
*Dado el siguiente listado de nombres:*
```python
alumnos = ["Carlos", "Carmen del Pilar", "Achraf", "Adrián", "Safa", "Estela del Carmen", "Yussef", "María", "Laura", "Julia", "Africa", "Sabrina", "Johana", "Pedro", "Antonio", "María de los Ángeles", "Rosalia", "Irene María", "Ana", "Iván Gaston", "Carlos", "Marina", "Javier", "Javier", "María Victoria", "Guillermo", "Aixa", "Aitana", "Rocío", "Lucía", "Claudia", "José", "Nicolás Iñaki", "María del Carmen", "Juan Fernando", "Candela", "Ignacio Jesús", "Miguel", "Elena Mercedes", "Miguel", "Javier", "Ana María", "Natalia", "Jaime", "Julian", "Juan Manuel", "Nicolás", "Lucía", "José Carlos"]
```
*Desarrolle las siguientes funciones:*
* *La función `limpiar(nombres)` que nos devuelva un listado de nombres ordenado y sin repeticiones. Use las funciones `purga()` desarrollada previamente y el método `sort()` de las listas.*
* *La función `longitud_más_largo(nombres)` que nos devuelva la longitud del nombre más largo del listado.*
* *La función `nombres_con_longitud(nombres, x)` que nos devuelva un listado con los nombres que tengan exactamente x letras (considerando espacios).*

*Usando esas funciones, haga un programa que nos ponga para cada longitud de nombres que nombres hay, como muestra el siguiente ejemplo (si hay longitudes que no tienen nombres no debe escribirse el número):*
```
3 -> ['Ana']
4 -> ['Aixa', 'José', 'Safa']
5 -> ['Jaime', 'Julia', 'Laura', 'Lucía', 'María', 'Pedro', 'Rocío']
6 -> ['Achraf', 'Adrián', 'Africa', 'Aitana', 'Carlos', 'Javier', 'Johana', 'Julian', 'Marina', 'Miguel', 'Yussef']
7 -> ['Antonio', 'Candela', 'Claudia', 'Natalia', 'Nicolás', 'Rosalia', 'Sabrina']
9 -> ['Ana María', 'Guillermo']
11 -> ['Irene María', 'Iván Gaston', 'José Carlos', 'Juan Manuel']
13 -> ['Ignacio Jesús', 'Juan Fernando', 'Nicolás Iñaki']
14 -> ['Elena Mercedes', 'María Victoria']
16 -> ['Carmen del Pilar', 'María del Carmen']
17 -> ['Estela del Carmen']
20 -> ['María de los Ángeles']
```
*__OBJETIVOS__: Desarrollo de programa completo largo y con uso de funciones.*

```python
def purga(l: list) -> list:
    res: list = []
    for v in l:
        if v not in res:
            res.append(v)
    return res

def limpiar(nombres: list) -> list:
    res: list = purga(nombres)
    res.sort()
    return res

def longitud_más_largo(nombres: list) -> int:
    max_long: int = len(nombres[0])
    for nombre in nombres:
        if len(nombre) > max_long:
            max_long = len(nombre)
    return max_long

def nombres_con_longitud(nombres: list, x: int) -> list:
    l: list = []
    for nombre in nombres:
        if len(nombre) == x:
            l.append(nombre)
    return l

# Programa principal
alumnos = ["Carlos", "Carmen del Pilar", "Achraf", "Adrián", "Safa", "Estela del Carmen", "Yussef", "María", "Laura", "Julia", "Africa", "Sabrina", "Johana", "Pedro", "Antonio", "María de los Ángeles", "Rosalia", "Irene María", "Ana", "Iván Gaston", "Carlos", "Marina", "Javier", "Javier", "María Victoria", "Guillermo", "Aixa", "Aitana", "Rocío", "Lucía", "Claudia", "José", "Nicolás Iñaki", "María del Carmen", "Juan Fernando", "Candela", "Ignacio Jesús", "Miguel", "Elena Mercedes", "Miguel", "Javier", "Ana María", "Natalia", "Jaime", "Julian", "Juan Manuel", "Nicolás", "Lucía", "José Carlos"]

alumnos = limpiar(alumnos)

for i in range(longitud_más_largo(alumnos) + 1):
    l = nombres_con_longitud(alumnos, i)
    if l != []:  # len(l) > 0
        print(i, "->", l)
```
