# Clase 19: 28 de noviembre de 2023

En esta clase hemos revisado el concepto y uso de diccionario y hemos practicado sobretodo el tema de lista de diccionarios.

# Ejercicio 1: Pagos
*Dados las líneas de texto del lateral. Realice las siguientes funciones:*
```python
pagos = [
"pepe: 20",
"lola: 30",
"pepe: 10",
"juan: 40",
"lola: 20",
"luis: 20",
"ana: 30",
"eva: 34"]
```
* *Recibiendo las líneas del lateral devuelva un diccionario que tenga como clave los nombres y valor, lo pagado en total.*
* *Otra que calcule el gasto medio.*
* *Finalmente, otra que imprima para cada uno si está a la par o si debe pagar/recibir y la cuánto.*

```python
# Funciones
def pago(lista: list) -> dict:
    dic: dict = {}
    for i in lista:
        nombre, dinero = i.split(": ")
        dinero: float = float(dinero)
        if nombre in dic:
            dic[nombre] += dinero
        else:
            dic[nombre] = dinero
    return dic


def gasto_medio(gastos: dict) -> float:
    suma = 0
    for k in gastos:
        suma += gastos[k]
    return suma/len(gastos)


# Programa principal
pagos: list = ["pepe: 20", "lola: 30", "pepe: 10", "juan: 40", "lola: 20", "luis: 20", "ana: 30","eva: 34"]

g: dict = pago(pagos)
m: float = gasto_medio(g)
print(m)
for nombre in g:
    if g[nombre] > m:
        print(f"{nombre} debe recibir {g[nombre] - m}")
    elif g[nombre] == m:
        print(f"{nombre} está a la par")
    else:
        print(f"{nombre} debe pagar {m - g[nombre]}")
```

## Ejercicio 3: Spotify

*En el fichero `songs.txt` tiene datos de las canciones más escuchadas de Spotify durante este año. De cada canción tenemos la siguiente información:*

* `'track_name'`: nombre de la canción (str)
* `'artist_names'`: lista con los cantantes de la canción (list(str))
* `'released_year'`: año en el que se lanzó el tema (int)
* `'released_month'`: mes en el que se lanzó el tema (int)
* `'released_day'`: día en el que se lanzó el tema (int)
* `'streams'`: número de veces que se ha escuchado el tema (int)
* `'danceability'`: bailabilidad (0-100) (int)
* `'energy'`: energía (0-100) (int)
* `'speechiness'`: cuánto se canta (cuanto más alto más palabras se dicen) (0-100) (int)
* `'liveness'`: ¿en vivo? (cuanto más alto más probabilidad hay) (0-100) (int)

En la misma carpeta `songs.txt` cree un nuevo fichero llamado `info_spotify.py` y añada al inicio:

```python
from json import load

f = open("songs.txt", encoding="utf-8")
SONGS = load(f)
f.close()
```

*Ese código carga en la variable `SONGS` todas las canciones (es una lista de canciones (diccionarios con la información indicada previamente)). Ahora en este fichero puede usar los datos y, por ejemplo: `print(SONGS[0]["track_name"])`) escribirá `'Seven (feat. Latto) (Explicit Ver.)'` (que es el nombre de la primera canción).

Usando ese fichero, realice el código para contestar a las siguientes preguntas. Vaya copiando las respuestas en el SOCRATIVE de la clase para validar las respuestas. Si en el apartado hay varias preguntas copie las respuestas separadas con un espacio.*

1.	*¿Cuál es el título de la canción 79 del listado? (recuerde que las posiciones empiezan en 0)*
2.	*¿Cuántas reproducciones tiene la última canción?*
3.	*3.	¿Cuál es el segundo cantante de la sexta canción del listado?*
4.	*¿Cuántas canciones hay en el listado?*
5.	*¿Cuántos millones (sin decimales) de veces se han escuchado en total todas las canciones?*
6.	*¿Cuántas canciones hay en vivo? (para considerarlas en vivo su liveness debe ser mayor de 60)*
7.	*¿Cuál es la energía media (con 2 decimales) de las canciones en las que participa ROSALÍA?*
8.	*¿Cuál es el título de la canción con más cantantes? ¿Cuántos cantantes participan? (En caso de que haya varias de igual número de cantantes elija la que esté antes)* 
9.	*¿Cuál es el título de la canción más antigua? ¿De qué año es?* 

*Genere una lista de nombres de cantantes sin que haya repetidos.*

10.	*¿Cuántos artistas diferentes hay?*
11.	*¿Cuáles son los 5 últimos cantantes de esa lista? (genere un texto con sus nombres separados por ":-:").*

*Partiendo del listado previo, genere un diccionario donde para cada cantante (clave) indique cuántas canciones tiene (valor):*

12.	*¿Cuántas canciones hay de Imagine Dragons?*
13.	*¿Qué cantante tiene más canciones? ¿Cuántas tiene?* 

[[Ver canciones](songs.txt)]

```python
from json import load

f = open("songs.txt", encoding="utf-8")
SONGS = load(f)
f.close()
print(SONGS[0])
# 1
print("1.- Título de la canción 79:", SONGS[78]["track_name"])
# 2
print("2.- Reproduciones de la última canción:", SONGS[-1]["streams"])
# 3
print("3.- Segundo cantante de la sexta canción:", SONGS[5]["artist_names"][1])
# 4
print("4.- Cantidad de canciones:", len(SONGS))
# 5
reproducciones: int = 0
for s in SONGS:
    reproducciones += s["streams"]
reproducciones = reproducciones // 1000000
print("5.- Cantidad de reproducciones total (millones):", reproducciones)
# 6
canciones_vivo: int = 0
for s in SONGS:
    if s["liveness"] > 60:
        canciones_vivo += 1
print("6.- Cantidad de canciones en vivo: ", canciones_vivo)
# 7 
energia: float = 0
cantidad: int = 0
for s in SONGS:
    if "ROSALÍA" in s["artist_names"]:
        cantidad += 1
        energia += s["energy"]
print(f"7.- Energía media de las canciones de ROSALIA: {energia/cantidad:.2f}")
# 8
mas_cantantes: dict = SONGS[0]
for s in SONGS:
    if len(s["artist_names"]) > len(mas_cantantes["artist_names"]):
        mas_cantantes = s
print("8.- La que tiene más cantantes:", mas_cantantes["track_name"],len(mas_cantantes["artist_names"]))
# 9
antigua = SONGS[0]
for s in SONGS:
    if s["released_year"] < antigua["released_year"]:
        antigua = s
    elif s["released_year"] == antigua["released_year"]:
        if s["released_month"] < antigua["released_month"]:
            antigua = s
        elif s["released_month"] < antigua["released_month"]:
            if s["released_day"] < antigua["released_day"]:
                antigua = s
        
print("9.- La mas antigua:", antigua["track_name"], antigua['released_year'])
# 10
artistas = []
for s in SONGS:
    for cantante in s["artist_names"]:
        if cantante not in artistas:
            artistas.append(cantante)
print("10.- Cantidad de artistas:", len(artistas))
# 11
print("11.- 5 últimos artistas:", ":-:".join(artistas[-5:]))
# 12
canciones_por_cantante = {}
for cantante in artistas:
    canciones_por_cantante[cantante] = 0
    for s in SONGS:
        if cantante in s["artist_names"]:
            canciones_por_cantante[cantante] += 1
print("12.- Cantidad de canciones de Imagine Dragons:", canciones_por_cantante["Imagine Dragons"])
# 13
cantante_max = artistas[0]
canciones = canciones_por_cantante[cantante_max]
for gen, can in canciones_por_cantante.items():
    if can > canciones:
        cantante_max = gen
        canciones = can
print("13.- El cantante con más canciones:", cantante_max, canciones)
```
