# Clase 21: 5 de diciembre de 2023

Aunque ya en clases previas vimos cómo utilizar los ficheros, aquí lo vemos más formalmente y que alternativas tenemos para leer los ficheros.

## Ejercicio 1: Ficheros de números:
*Usando un editor de texto simple (tipo Notepad o incluso Thonny) cree un fichero con un número en cada línea. Realice un programa que lea el fichero e indique su suma.*

*Modifique el programa anterior para que nos indique su media.*

*Cree un fichero de texto donde hay muchas líneas y cada línea puede contener 1 o muchos números (separados por espacios). Realice un programa que lee el fichero y nos indique la media.*

__Un número por línea__
```python
def ejercicio_con_read(filename: str) -> float:
    f = open(filename)
    todo: str = f.read()
    f.close()
    valores: list = todo.split()
    suma: float = 0
    for v in valores:
        suma += float(v)
    return suma


def ejercicio_con_readlines(filename: str) -> float:
    f = open(filename)
    lineas: list = f.readlines()
    f.close()
    suma: float = 0
    for v in lineas:
        suma += float(v)
    return suma


def ejercicio_con_readline(filename: str) -> float:
    f = open(filename)
    suma: float = 0
    linea: list = f.readline()
    while linea != "":
        suma += float(linea)
        linea = f.readline()
    f.close()
    return suma


def ejercicio_con_for(filename: str) -> float:
    f = open(filename)
    suma: float = 0
    for l in f:
        suma += float(l)
    f.close()
    return suma


nombre: str = input("Dime el nombre del fichero: ")
print("La suma (usando read) es", ejercicio_con_read(nombre))
print("La suma (usando for) es", ejercicio_con_for(nombre))
print("La suma (usando readlines) es", ejercicio_con_readlines(nombre))
print("La suma (usando readline) es", ejercicio_con_readline(nombre))
```

__Múltiples números por línea__
```python
def ejercicio_con_read(filename: str) -> float:
    f = open(filename)
    todo: list = f.read()
    f.close()
    valores = todo.split()
    suma: float = 0
    for v in valores:
        suma += float(v)
    return suma


def ejercicio_con_for(filename: str) -> float:
    f = open(filename)
    suma: float = 0
    for l in f:
        valores: list = l.split()
        for v in valores:
            suma += float(v)
    f.close()
    return suma


nombre: str = input("Dime el nombre del fichero: ")
print("La suma (usando read) es", ejercicio_con_read(nombre))
print("La suma (usando for) es", ejercicio_con_for(nombre))
```

## Ejercicio 2: Fichero de datos de series:

*Hacer un programa con una función que lea un fichero que tiene el siguiente formato:*
```
	Breaking Bad, 62, 50, Netflix
	Andor, 12, 45, Disney+
	La Casa del Dragón, 10, 55, HBOMax
	1899, 8, 50, Netflix
	The Boys, 24, 50, AmazonPrime
```
*La función debe devolverlo como lista de listas: `[ ["Breaking Bad", 62, 50, "Netflix"], ["Hawkeye", 6, 45, “Disney+"], …]`*
*La función debe devolver como lista de diccionarios: `[{"serie": "Breaking Bad", "episodios": 62, "duración": 50, "plataforma": "Netflix"}, …]`*
*En ambos casos añada un nuevo valor a cada una con la duración total. Luego, muestre el título de la más larga.*

__Listas:__
```python
def obtener_serie(l: str) -> list:
    serie: list = l.split(",")
    serie[1] = int(serie[1])
    serie[2] = int(serie[2])
    serie[3] = serie[3].strip()
    return serie


def leer() -> list:
    f = open("series.txt")
    lista: list = []
    for l in f:
        serie = obtener_serie(l)
        lista.append(serie)

    f.close()
    return lista


def añadir_duración(series: list) -> None:
    for serie in series:
        duración = serie[1] * serie[2]
        serie.append(duración)


def serie_más_larga(series: list) -> list:
    mas_larga: list = series[0]
    for serie in series:
        if serie[4] > mas_larga[4]:
            mas_larga = serie
    return mas_larga


s: list = leer()
añadir_duración(s)
print(serie_más_larga(s))
```

__Diccionarios:__
```python
def obtener_serie(l: str) -> dict:
    serie: list = l.split(",")
    serie_dict: dict = {
        "serie": serie[0].strip(),
        "episodios": int(serie[1]),
        "duración": int(serie[2]),
        "plataforma": serie[3].strip()
    }
    return serie_dict


def leer() -> list:
    f = open("series.txt")
    lista: list = []
    for l in f:
        serie: dict = obtener_serie(l)
        lista.append(serie)

    f.close()
    return lista


def añadir_duración(series: list) -> None:
    for serie in series:
        duración: int = serie["episodios"] * serie["duración"]
        serie["duración_total"] = duración


def serie_más_larga(series: list) -> dict:
    mas_larga: dict = series[0]
    for serie in series:
        if serie["duración_total"] > mas_larga["duración_total"]:
            mas_larga = serie
    return mas_larga


s: list = leer()
añadir_duración(s)
print(serie_más_larga(s))
```

## Ejercicio 3:

*Podemos definir un fichero multifasta como aquel que puede contener varias secuencias en formato fasta dentro. Ver ejemplo al final. Hacer una función que recibiendo el nombre de un fichero multifasta, guarde dentro de un diccionario de claves los identificadores y valores las secuencias. El diccionario del ejemplo sería: `{'Laurencia': 'TATGGTTGACATTGACCCCT', 'Glaucocystis': '…', …}` Hacer una función que devuelva tal tipo de diccionario a partir de un nombre de fichero. Hacer otra función que reciba un diccionario como el anterior y un fragmento de secuencia y devuelva una lista de los identificadores de las secuencias que tienen al menos una vez este fragmento.*

*Imprimir esta lista de identificadores como en el ejemplo:*

```python
seqs = lee_secuencias("seqs.txt ")
print(tienen_secuencia(seqs, "AAGG")) #['Glaucocystis', 'Macrocystis pyrifera']
```

```
>Laurencia
TATGGTTGACATTGACCCCT
>Glaucocystis
ACTTTGGCTCCAGGAAGTAACCGGGGAA
GGCGAAGCTTCTCCGCATGGATCTTCCGTAGG
>Macrocystis pyrifera
ACTTTGGCTAAGGCCAAGTA
AATGGAGTGTGTACGATTGACGGGATGACGGACTAACAGT
```

```python
def leer_secuencias(nombre_fichero: str) -> dict:
    f = open(nombre_fichero, encoding="utf-8")
    secuencias: dict = {}
    for linea in f:
        # Analizar linea y añadir a secuencias
        linea = linea.strip()
        if linea[0] == ">":
            # nombre
            nombre: str = linea[1:]
            secuencias[nombre] = ""
        else:
            # secuencia
            secuencias[nombre] += linea
    f.close()
    return secuencias


def tienen_secuencia(secuencias: dict, subsec: str) -> list:
    lista: list = []
    for nombre, secuencia in secuencias.items():
        if subsec in secuencia:
            lista.append(f"{nombre} -> {secuencia}")
    return lista


# Programa principal
seqs: dict = leer_secuencias("seq.txt")
print(seqs)
print(tienen_secuencia(seqs, "AAGG")) # ['Glaucocystis', 'Macrocystis pyrifera']
```
