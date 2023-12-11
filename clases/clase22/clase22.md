# Clase 22: 11 de diciembre de 2021

En esta clase seguimos repasando ficheros y hacemos ejercicios de examen:

## Ejercicio 1: 
*Hacer una función (`def esc(l1: list, l2: list) -> float`) que devuelva el producto escalar de los dos vectores recibidos como parámetros, esto es: suma de los productos de los correspondientes componentes. Suponer que siempre los vectores recibidos tienen ambos la misma longitud. Probar:*

```python
print(esc([1.0, 2, 3], [3, 2, 1])) # 10.0
print(esc([0, 1.1, 0, 2], [-1, 10, 0, 2])) # 15.0
```

```python
# Funciones
def esc(l1: list, l2: list) -> float:
    producto_escalar: float = 0
    for pos in range(len(l1)):
        producto_escalar += l1[pos]*l2[pos]
    return producto_escalar

# Programa principal
print(esc([1.0 , 2 , 3] , [3 , 2 , 1])) # 10.0
print(esc([0 , 1.1 , 0 , 2] , [ -1 , 10 , 0 , 2])) # 15.0
```

## Ejercicio 2:

*Hacer una función `sumaDiv(n: int) -> int` que devuelva la suma de los divisores del número entero n recibido como parámetro. Hacer otra función que nos diga si su parámetro entero es perfecto. Un número entero es perfecto cuando coincide con la suma de sus divisores. Probar:*

```python
print(esPerf(6)) # True
print(esPerf(28)) # True
print(esPerf(29)) # False
print(esPerf(496)) # True
```

```python
def sumaDiv(n: int) -> int:
    suma: int = 0
    for div in range(1, n):
        if n % div == 0:
            suma += div    
    return suma
    
    
def esPerf(n: int) -> bool:
    es_perfecto: bool = False
    if sumaDiv(n) == n:
        es_perfecto = True
    else:
        es_perfecto = False
    
    return es_perfecto
    # return sumaDiv(n) == n

# Programa principal
print(esPerf(6)) # True
print(esPerf(28)) # True
print(esPerf(29)) # False
print(esPerf(496)) # True
```

## Ejercicio 3:

*Realice una función que realice una intersección de bolsas (las bolsas es un tipo parecido al conjunto, pero cada elemento puede estar varias veces). La intersección ofrece como resultado una lista donde aparezca los elementos que aparezcan en ambas listas sobre las que se aplica. Si hay repetidos, en el resultado estarán repetidos (la menor cantidad que hay en ambas listas). Probar:*

```python
print(intersección([1,2], [2,4])) # [2]
print(intersección([1,4,2], [2,4])) # [4,2]
print(intersección([1,2,2,3,5], [5,2,2,2,4])) # [2,2,5]
print(intersección([1,2], [3,4])) # []
```

```python
def intersección(l1: list, l2: list) -> list:
    comunes: list = []
    for v in l1:
        if comunes.count(v) < l1.count(v) and comunes.count(v) < l2.count(v):#v in l2 and v not in comunes:
            comunes.append(v)    
    return comunes
    
    
print(intersección([1,2], [2,4])) # [2]
print(intersección([1,4,2], [2,4])) # [4,2]
print(intersección([1,2,2,3,5], [5,2,2,2,4])) # [2,2,5]
print(intersección([5,2,2,2,4], [1,2,2,3,5])) # [2,2,5]
print(intersección([1,2], [3,4])) # []
```


## Ejercicio 4:

*Suponer que tenemos un fichero con los nombres de estudiantes y una serie de calificaciones en una cantidad dada, para todos igual, de asignaturas. Hacer una función `lee_notas(nombre_fichero: str) -> dict` que recibe el nombre de ese fichero y devuelve un diccionario del tipo: `{'Pedro Perez': [2.0, 6.0, 3.0, 8.1], 'Maria ... ': [1.0, 7.0, ...], ...}` Imprimir este diccionario para comprobar su contenido. Luego, realice otra función que nos devuelva el alumno con nota media más alta (todas las notas tienen el mismo peso). Usar como ejemplo el fichero [`notas.txt`](notas.txt) al final*

```text
Pedro Pérez: 2, 6, 3 ,8.1
María Rodríguez: 1, 7,7, 4
Ana Gómez: 5, 5,6, 5
```
```python
# Funciones
def analizar_linea(l: str) -> (str, list):
    nombre: str = ""
    notas: list = []
    
    nom, calificaciones = l.split(":")
    nombre = nom.strip()
    lista: list = calificaciones.split(",")
    for nota in lista:
        notas.append(float(nota))
    
    return nombre, notas
    
def leernotas(nombre_fichero: str) -> dict:
    notas: dict = {}
    # Abrir fichero
    f = open(nombre_fichero, encoding="utf-8")
    # Leer el fichero:
    for linea in f:
        # Analizar línea
        nombre, calificaciones = analizar_linea(linea)
        # Tratar los datos
        notas[nombre] = calificaciones
    # Cerrar el fichero
    f.close()
    return notas

def nota_media(l: list) -> float:
    media: float = 0
    suma: float = 0
    for n in l:
        suma += n
    media = suma / len(l)
    return media

def alumno_mejor_media(notas: dict) -> str:
    claves: list = list(notas.keys())
    alumno: str = claves[0]
    for estudiante in notas:
        if nota_media(notas[estudiante]) > nota_media(notas[alumno]):
            alumno = estudiante    
    return alumno
    
    
# Programa principal
print(alumno_mejor_media(leernotas("notas.txt")))
```

## Ejercicio 5:

*Usaremos los diccionarios que se proporciona en el fichero [poblaciones.txt](poblaciones.txt). Se pide definir una función `def pobComunidad(comunidad)` que devuelva la población total de una comunidad autónoma, por ejemplo: `pobComunidad("Andalucía")` devolvería: `2394851`. Probar la función con esa comunidad e imprimir el número resultante. No se requiere `input()`.*

```python
# Funciones
def pobComunidad(comunidad: str, provCom: dict, pobProv: dict) -> float:
    población_total: float = 0
    for ciudad in provCom:
        if provCom[ciudad] == comunidad:
            población_total += pobProv[ciudad]
    
    return población_total


# Programa principal
provComunidad = {
    "Madrid"                     : "Comunidad de Madrid",
    "Barcelona"                  : "Cataluña",
    "Valencia"                   : "Comunidad Valenciana",
    "Sevilla"                    : "Andalucía",
    "Zaragoza"                   : "Aragón",
    "Málaga"                     : "Andalucía",
    "Murcia"                     : "Región de Murcia",
    "Palma de Mallorca"          : "Islas Baleares",
    "Las Palmas de Gran Canaria" : "Canarias",
    "Bilbao"                     : "País Vasco",
    "Alicante"                   : "Comunidad Valenciana",
    "Córdoba"                    : "Andalucía",
    "Valladolid"                 : "Castilla y León",
    "Vitoria"                    : "País Vasco",
    "La Coruña"                  : "Galicia",
    "Granada"                    : "Andalucía",
    "Oviedo"                     : "Principado de Asturias",
    "Santa Cruz de Tenerife"     : "Canarias",
    "Pamplona"                   : "Comunidad Foral de Navarra",
    "Almería"                    : "Andalucía",
    "San Sebastián"              : "País Vasco",
    "Burgos"                     : "Castilla y León",
    "Albacete"                   : "Castilla-La Mancha",
    "Santander"                  : "Cantabria",
    "Castellón de la Plana"      : "Comunidad Valenciana",
    "Logroño"                    : "La Rioja",
    "Badajoz"                    : "Extremadura",
    "Salamanca"                  : "Castilla y León",
    "Huelva"                     : "Andalucía",
    "Lérida"                     : "Cataluña",
    "Tarragona"                  : "Cataluña",
    "León"                       : "Castilla y León",
    "Cádiz"                      : "Andalucía",
    "Jaén"                       : "Andalucía",
    "Orense"                     : "Galicia",
    "Gerona"                     : "Cataluña",
    "Lugo"                       : "Galicia",
    "Cáceres"                    : "Extremadura",
    "Melilla"                    : "Melilla",
    "Guadalajara"                : "Castilla-La Mancha",
    "Toledo"                     : "Castilla-La Mancha",
    "Ceuta"                      : "Ceuta",
    "Pontevedra"                 : "Galicia",
    "Palencia"                   : "Castilla y León",
    "Ciudad Real"                : "Castilla-La Mancha",
    "Zamora"                     : "Castilla y León",
    "Ávila"                      : "Castilla y León",
    "Cuenca"                     : "Castilla-La Mancha",
    "Huesca"                     : "Aragón",
    "Segovia"                    : "Castilla y León",
    "Soria"                      : "Castilla y León",
    "Teruel"                     : "Aragón",
}


provPobla = {
    "Madrid"                     : 3266126,
    "Barcelona"                  : 1636762,
    "Valencia"                   : 794288,
    "Sevilla"                    : 688592,
    "Zaragoza"                   : 681877,
    "Málaga"                     : 574654,
    "Murcia"                     : 459403,
    "Palma de Mallorca"          : 416065,
    "Las Palmas de Gran Canaria" : 379925,
    "Bilbao"                     : 346843,
    "Alicante"                   : 334887,
    "Córdoba"                    : 325701,
    "Valladolid"                 : 298412,
    "Vitoria"                    : 251774,
    "La Coruña"                  : 245711,
    "Granada"                    : 232462,
    "Oviedo"                     : 219686,
    "Santa Cruz de Tenerife"     : 207312,
    "Pamplona"                   : 201653,
    "Almería"                    : 200753,
    "San Sebastián"              : 187415,
    "Burgos"                     : 175821,
    "Albacete"                   : 173329,
    "Santander"                  : 172539,
    "Castellón de la Plana"      : 171728,
    "Logroño"                    : 151136,
    "Badajoz"                    : 150702,
    "Salamanca"                  : 144228,
    "Huelva"                     : 143663,
    "Lérida"                     : 138956,
    "Tarragona"                  : 134515,
    "León"                       : 124303,
    "Cádiz"                      : 116027,
    "Jaén"                       : 112999,
    "Orense"                     : 105233,
    "Gerona"                     : 101852,
    "Lugo"                       : 98276,
    "Cáceres"                    : 96126,
    "Melilla"                    : 86487,
    "Guadalajara"                : 87064,
    "Toledo"                     : 85449,
    "Ceuta"                      : 84777,
    "Pontevedra"                 : 83029,
    "Palencia"                   : 77090,
    "Ciudad Real"                : 75504,
    "Zamora"                     : 60988,
    "Ávila"                      : 58369,
    "Cuenca"                     : 53988,
    "Huesca"                     : 53429,
    "Segovia"                    : 52057,
    "Soria"                      : 39821,
    "Teruel"                     : 36240,
}

print(pobComunidad("Andalucía", provComunidad, provPobla))
```

## Ejercicio 6:
*En el fichero [series.txt](series.txt), se muestra la información (nombre y descripción) de las series más populares de 2021 (según IMDB). Realice una función `def leeSeries(nombFich)` que nos devuelva un diccionario con el contenido del fichero. Como clave tendremos el nombre de la serie y como valor su descripción.*

*También desarrolle otra función `def buscarSerie(series, palabra)` que nos devuelva una lista con los títulos de las series donde en su descripción aparece la palabra. En el programa principal escriba el contenido de esa lista. Por ejemplo, con `buscarSerie(series, "Avengers")` escribiría `["Loki", "The Falcon and the Winter Soldier"]`.*

```python
# Funciones
def leerSeries(nombre_fichero: str) -> dict:
    series: dict = {}
    f = open(nombre_fichero, encoding="utf-8")
    for linea in f:
        linea = linea.strip()
        if linea[0:3] == "-- ":
            nombre_serie = linea[3:]
            series[nombre_serie] = ""
        else:
            descripcion = linea
            series[nombre_serie] += descripcion
    f.close()
    return series

def buscarSerie(series: dict, palabra: str) -> list:
    lista: list = []
    for serie in series:
        if palabra in series[serie]:
            lista.append(serie)
    
    return lista

# Programa principal
s: dict = leerSeries("series.txt")
print(buscarSerie(s, "Avengers"))
```
