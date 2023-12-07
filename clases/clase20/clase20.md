# Clase 20: 28 de noviembre de 2022

En este clase vimos cómo calcular el mínimo valor (o clave) de un diccionario. También vimos como trabajar cuando un campo de un diccionario almacena una lista. Finalmente, vimos de manera informal cómo leer un fichero y seguimos repasando cómo trabajar con una lista de diccionarios.

## Ejercicio 1: Máximo en un diccionario: 
*Dado un diccionario (con el del ejemplo) donde tenemos para una serie de meses su temperatura media, calcule cuál es la mayor temperatura media.*

```python
Málaga: dict = {"enero": 12, "febrero": 12, "marzo": 14, "abril": 16, "mayo": 19, "junio": 23, "julio": 26, "agosto": 26,"septiembre": 23, "octubre": 19, "noviembre": 15, "diciembre": 13}
Yakustk: dict = {"enero": -38, "febrero": -34, "marzo": -20, "abril": -5, "mayo": 8, "junio": 16, "julio": 20, "agosto": 15, "septiembre": 6, "octubre": -8, "noviembre": -27, "diciembre": -37}
```

```python
# Posibilidad 1: Como lista
def max_list(l: list) -> int:
    maximo: int = l[0]
    for v in l[1:]:
        if v > maximo:
            maximo = v
    return maximo


# Posibildiad 2: Como diccionario
def max_dict(d: dict) -> int:
    clave: str = list(d)[0]
    maximo: int = d[clave]
    for k in d:
        if d[k] > maximo:
            maximo = d[k]
    return maximo


# Programa principal
Málaga: dict = {"enero": 12, "febrero": 12, "marzo": 14, "abril": 16, "mayo": 19, "junio": 23, "julio": 26, "agosto": 26,"septiembre": 23, "octubre": 19, "noviembre": 15, "diciembre": 13}
Yakustk: dict = {"enero": -38, "febrero": -34, "marzo": -20, "abril": -5, "mayo": 8, "junio": 16, "julio": 20, "agosto": 15, "septiembre": 6, "octubre": -8, "noviembre": -27, "diciembre": -37}

# Posibilidad 1: Como lista
l_málaga: list = list(Málaga.values())
l_yakustk: list = list(Yakustk.values())
print("Málaga:", max_list(l_málaga))
print("Yakustk:", max_list(l_yakustk))

# Posibildiad 2: Como diccionario
print("Málaga:", max_dict(Málaga))
print("Yakustk:", max_dict(Yakustk))
```

## Ejercicio 2: Valor del máximo: 
*Modifique el anterior para obtener el nombre del mes que tiene la temperatura máxima.*

```python
def max_key_dict(d: dict) -> str:
    maximo: str = list(d)[0]
    for k in d:
        if d[k] > d[maximo]:
            maximo = k
    return maximo


# Programa principal
Málaga: dict = {"enero": 12, "febrero": 12, "marzo": 14, "abril": 16, "mayo": 19, "junio": 23, "julio": 26, "agosto": 26,"septiembre": 23, "octubre": 19, "noviembre": 15, "diciembre": 13}
Yakustk: dict = {"enero": -38, "febrero": -34, "marzo": -20, "abril": -5, "mayo": 8, "junio": 16, "julio": 20, "agosto": 15, "septiembre": 6, "octubre": -8, "noviembre": -27, "diciembre": -37}

print("Málaga:", max_key_dict(Málaga))
print("Yakustk:", max_key_dict(Yakustk))
```

## Ejercicio 3: Diccionarios de listas: 
*La tasa de éxito de una asignatura mide el número de alumnos que superan una asignatura respecto al número de alumnos que se presentan a la asignatura. Dado un diccionario con las asignaturas como claves y que tienen como valor la tasa de éxito de los últimos años, realice un programa que escriba para cada asignatura la tasa de éxito media de esos años. Ejemplos (datos oficiales extraídos de la página de calidad de la UMA).*

```python
Salud: dict = {
  "Bioquímica estructural": [0.66, 0.61, 0.47, 0.64, 0.92, 0.92, 0.75, 0.56], 
  "Cálculo": [0.55, 0.52, 0.48, 0.29, 0.29, 0.06, 0.17, 0.53], 
  "Fundamentos de la programación": [0.58, 0.66, 0.53, 0.76, 0.7, 0.6, 0.49, 0.68], 
  "Física I": [0.23, 0.41, 0.38, 0.45, 0.37, 0.4, 0.56, 0.35], 
  "Álgebra lineal": [0.48, 0.44, 0.46, 0.54, 0.61, 0.41, 0.51, 0.61]
}
```

```python
def max_key_dict(d: dict) -> str:
    maximo: str = list(d)[0]
    for k in d:
        if d[k] > d[maximo]:
            maximo = k
    return maximo


# Programa principal
Málaga: dict = {"enero": 12, "febrero": 12, "marzo": 14, "abril": 16, "mayo": 19, "junio": 23, "julio": 26, "agosto": 26,"septiembre": 23, "octubre": 19, "noviembre": 15, "diciembre": 13}
Yakustk: dict = {"enero": -38, "febrero": -34, "marzo": -20, "abril": -5, "mayo": 8, "junio": 16, "julio": 20, "agosto": 15, "septiembre": 6, "octubre": -8, "noviembre": -27, "diciembre": -37}

print("Málaga:", max_key_dict(Málaga))
print("Yakustk:", max_key_dict(Yakustk))
```

# Ejercicio 4 (Películas): Pasar texto a diccionario: 
*Realice una función que reciba un texto que tiene información de una película a un diccionario con esa información. El formato del texto es:*

```
título#director1, director2, …#actor1, actor2, … #género1, género2, …#año puntuación duración recaudación#descripción
```
Por ejemplo: 
```
peli = "Puss in Boots#Chris Miller#Antonio Banderas, Salma Hayek, Zach Galifianakis, Billy Bob Thornton#Animation, Adventure, Comedy#2011 6.6 90 149260000.0#An outlaw cat, his childhood egg-friend, and a seductive thief kitty set out in search for the eggs of the fabled Golden Goose to clear his name, restore his lost honor, and regain the trust of his mother and town."
```
debería devolver:
```python
{
  'título': 'Puss in Boots',
  'directores': ['Chris Miller'],
  'actores': ['Antonio Banderas', 'Salma Hayek', 'Zach Galifianakis', 'Billy Bob Thornton'],
  'géneros': ['Animation', 'Adventure', 'Comedy'],
  'año': 2011,
  'puntuación': 6.6,
  'duración': 90,
  'recaudación': 149260000.0,
  'descripción': 'An outlaw cat, his childhood egg-friend, and a seductive thief kitty set
  out in search for the eggs of the fabled Golden Goose to clear his name, restore his lost
  honor, and regain the trust of his mother and town.'}
}
```

```python
def pasar_a_lista(texto: str) -> list:
    l: list = texto.split(",")
    l_limpia: list = []
    for elemento in l:
        l_limpia.append(elemento.strip())
    return l_limpia

def decodificar_linea(peli):
    título, directores, actores, generos, resto, descripción = peli.split("#")
    año, punt_imdb, duración, recaudado = resto.split()
    d = {
        "título": título.strip(),
        "directores": pasar_a_lista(directores),
        "actores": pasar_a_lista(actores),
        "géneros": pasr_a_lista(generos),
        "año": int(año),
        "puntuación": float(punt_imdb),
        "duración": int(duración),
        "recaudación": float(recaudado),
        "descripción": descripción.strip()
    }
    return d
```

# Ejercicio 5 (Películas): Leer fichero a lista de diccionario: 
*Lea el contenido de ["pelis.txt"](pelis.txt) y guárdelas en una lista. El esquema que usaremos es:*

```python
fichero = open(“nombre_fichero”)
lista = []
for línea in fichero:
	diccionario = decodificar_linea(línea)
	lista.append(diccionario)
fichero.close()
```

```python
def leer_fichero(filename):
    fichero = open(filename)
    lista = []
    for línea in fichero:
        diccionario = decodificar_linea(línea)
        lista.append(diccionario)
    fichero.close()
    return lista
```

# Ejercicio 6: Películas: 
*Cree un grupo de 2 o 3 personas y conéctese a SOCRATIVE para validar sus respuestas a las siguientes preguntas:*

*1.- ¿Cuántas películas hay en el fichero?*

*2.- ¿Cuál es el último género de la sexta película en la lista? (Recuerde las listas empiezan en 0)*

*3.- ¿Cuáles son los primeros 3 actores de la sexta película en la lista? (El formato debe ser actor1, actor2, actor3)*

*4.- ¿Cuántas películas hay posterior al 2000?*

*5.- ¿Cuántas películas hay que tengan el género "Drama" entre sus géneros?*

*6.- ¿Cuál es la duración de la más larga?*

*7.- ¿Y cuál es su título?*

*8.- ¿Cuál es el título de la peli más valorada según la puntuación de IMDB?*

*9.- Según la puntuación de IMDB, ¿qué puesto ocuparía la película "Avengers: Endgame"? (Busque primero la película y obtenga su puntuación, luego mire cuántas películas hay por delante suya (tiene más puntuación)) (Tenga en cuenta que si ninguna película la superara estaría en la posición 1)*

*10.- ¿Cuántos géneros diferentes hay? (Se recomienda hacer una lista donde meta los géneros sin repetirlos).*

*11.- ¿Qué actor que ha participado en más películas? ¿y en cuantas? (La respuesta sería actor – num_pelis) (Se recomienda generar un diccionario con pares: actor:num_pelis y luego obtener el máximo).*

*Extra:*

*12.- ¿Qué actor es el más rentable?  Para esto se recomienda el siguiente proceso:*

*a)	Modifique el anterior para que en vez de ser actor: num_pelis se guarde una lista de 2 posiciones con la siguiente forma: actor: [num_pelis, recaudación_total]. Note que hay pelis que no se sabe la recaudación (aparecen con -1), ignórelas para los cálculos (no deben modificar ni num_pelis ni recaudación_total).*

*b)	Busque el que tiene una ratio recaudación/num_pelis más alto (pero habiendo actuado en más de 5 películas).*

*13.- ¿Qué palabra (de más de 5 letras) es la más repetida en las descripciones?*

```python
def pasar_a_lista(texto: str) -> list:
    l: list = texto.split(",")
    l_limpia: list = []
    for elemento in l:
        l_limpia.append(elemento.strip())
    return l_limpia

def decodificar_linea(peli):
    título, directores, actores, generos, resto, descripción = peli.split("#")
    año, punt_imdb, duración, recaudado = resto.split()
    d = {
        "título": título.strip(),
        "directores": pasar_a_lista(directores),
        "actores": pasar_a_lista(actores),
        "géneros": pasr_a_lista(generos),
        "año": int(año),
        "puntuación": float(punt_imdb),
        "duración": int(duración),
        "recaudación": float(recaudado),
        "descripción": descripción.strip()
    }
    return d

def leer_fichero(filename):
    fichero = open(filename)
    lista = []
    for línea in fichero:
        diccionario = decodificar_linea(línea)
        lista.append(diccionario)
    fichero.close()
    return lista


# Programa principal
l = leer_fichero("pelis.txt")
print(l[0])
# 1.- Cantidad de películas
print("1.- En el fichero hay", len(l), "películas")
# 2.- Último genero de la película en la posición 6
print("2.- El último género de la película es", l[5]["géneros"][-1])

# 3.- Tres actores película en la posición 6
print("3.- Los tres actores de la película son", ", ".join(l[5]["actores"][:3]))

# 4.- ¿Cuántas películas hay posterior al 2000?
despues_2000 = 0
for p in l:
    if p["año"] > 2000:
        despues_2000 += 1
print("4.- Hay", despues_2000, "películas posterior a 2000")
# 5.- Cantidad de pelis con el género drama
pelis_drama = 0
for p in l:
    if "Drama" in p["géneros"]:
        pelis_drama += 1
print("5.- Hay", pelis_drama, "películas dramáticas")
# 6.- Duración de la más larga
mas_larga = l[0]
for p in l:
    if p["duración"] > mas_larga["duración"]:
        mas_larga = p
print("6.- La peli más larga dura", mas_larga["duración"])
# 7.- Título de la más larga
print("7.- La peli más larga es", mas_larga["título"])
# 8.- Más valorada según metascore
mejor = l[0]
for p in l:
    if p["puntuación"] > mejor["puntuación"]:
        mejor = p
print("8.- La mejor peli es", mejor["título"])
# 9.- Posición de Avengers: Endgame
peli = "Avengers: Endgame"
i = 0
while i < len(l) and l[i]["título"] != peli: i += 1
posicion = 1
for p in l:
    if p["puntuación"] > l[i]["puntuación"]:
        posicion += 1
print("9.- La posición de Avengers: Endgame es", posicion)
# 10.- Número de generos
géneros = []
for p in l:
    for g in p["géneros"]:
        if g not in géneros:
            géneros.append(g)
print("10.- Hay", len(géneros), "géneros")
# 11.- Más activo
actores = {}
for p in l:
    for a in p["actores"]:
        if a in actores:
            actores[a] += 1
        else:
            actores[a] = 1
actor = list(actores)[0]
for a in actores:
    if actores[a] > actores[actor]:
        actor = a
print("11.- El actor más activo es:", actor,"-", actores[actor])
# 12.- Más rentable
actores = {}
for p in l:
    if p["recaudación"] > 0:
        for a in p["actores"]:
            if a in actores:
                actores[a][0] += 1
                actores[a][1] += p["recaudación"]
            else:
                actores[a] = [1, p["recaudación"]]
actor = list(actores)[0]
rentabilidad = actores[actor][1]/actores[actor][0]
for a in actores:
    rentabilidad2 = actores[a][1]/actores[a][0]
    if rentabilidad2 > rentabilidad and actores[a][0] > 5:
        actor = a
        rentabilidad = rentabilidad2
print("12.- El actor más rentable es:", actor,"-", round(actores[actor][1]/1000000, 2))
palabras: dict = {}
for p in l:
    for pal in p["descripción"].split():
        if pal in palabras:
            palabras[pal] += 1
        else:
            palabras[pal] = 1

palabra: str = list(palabras.keys())[0]
for p in palabras:
    if len(palabra) <= 5 or (palabras[palabra] < palabras[p] and len(p) > 5):
        palabra = p
print("13.- La palabra más usada es:", palabra,"con", palabras[palabra],"apariciones")
```
