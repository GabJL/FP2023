# Clase 18: 27 de noviembre de 2023

En esta clase se introdujo el concepto de diccionario y cómo trabajar con ellos.

## Ejercicio 1: Libros
*Nos interesa hacer un programa para manejar libros. De cada libro queremos: título, autor, precio, número de páginas y editorial.*

* *Cree una variable `libro1` con los siguientes valores: El Marciano de Andy Weir, editorial Nova, edición rústica (2014) con 407 páginas y 20,50 € de precio (quizás no necesite todos los datos).*
* *Suponiendo que lee de teclado: `Dune # Frank Herbert # Debolsillo (Pengun Ed.) 784 11.35` almacene los valores de forma apropiada en otra variable llamada `libro2`.*
* *Muestre el título y número de páginas del libro que tiene más páginas de los dos.*
* *Aplique un descuento de un 5% al libro más caro.*

```python
libro1: dict = {
    "título": "El Marciano",
    "autor": "Andy Weir",
    "editorial": "Nova",
    "páginas": 407,
    "precio": 20.5
}

print("El autor del libro es", libro1['autor'])

libro2: dict = {}

info: str = "Dune # Frank Herbert # Debolsillo (Pengun Ed.) 784 11.35"
título, autor, resto = info.split("#")

libro2["título"] = título.strip()
libro2["autor"] = autor.strip()

datos: list = resto.split()
libro2["páginas"] = int(datos[-2])
libro2["precio"] = float(datos[-1])
libro2["editorial"] = " ".join(datos[:-2])
print(libro2)

libro3: dict = {
    "título": título.strip(),
    "autor": autor.strip(),
    "páginas": int(datos[-2]),
}

if libro1['páginas'] > libro2['páginas']:
    print(f"El libro {libro1['título']} tiene {libro1['páginas']} páginas")
else:
    print(f"El libro {libro2['título']} tiene {libro2['páginas']} páginas")

if libro1['precio'] > libro2['precio']:
    libro1['precio'] = libro1['precio']*0.95
    print(libro1)
else:
    libro2['precio'] = libro2['precio']*0.95
    print(libro2)
```

## Ejercicio 2: Ciudades
*Dadas las siguientes ciudades:*
```python
ciudades = {
	"Madrid": 		3266126,
	"Barcelona":		1636762,
	"Valencia": 		794288,
	"Sevilla": 		688592,
	"Zaragoza": 		674997,
	"Málaga": 		574654,
	"Murcia": 		453258,
	"Palma de Mallorca":	416065,    
	"Las Palmas de Gran Canarias": 379925,
	"Bilbao": 		346843
}
```
*Realice un programa que indique la población media.*

```python
ciudades: dict = {
    "Madrid": 3266126,
    "Barcelona": 1636762,
    "Valencia": 794288,
    "Sevilla": 688592,
    "Zaragoza": 674997,
    "Málaga": 574654,
    "Murcia": 453258,
    "Palma de Mallorca": 416065,
    "Las Palmas de Gran Canarias": 379925,
    "Bilbao": 346843
}

# Version 1
suma_claves = 0
for k in ciudades:
    suma_claves += ciudades[k]

# Version 2
suma_valores1 = 0
for k, v in ciudades.items():
    suma_valores1 += v

# Version 3
suma_valores2 = 0
for v in ciudades.values():
    suma_valores2 += v

print(suma_claves / len(ciudades), suma_valores1 / len(ciudades), suma_valores2 / len(ciudades))
```

## Ejercicio 3: Cartas
*Sabiendo que una carta tiene valor (1 a 10) y palo (oros, espadas, copas y bastos), realice las siguientes funciones:*
* *Una que genere una carta aleatoria (use `randint` de `random`)*
* *Otra que muestre por pantalla una carta*
* *Una función que nos diga si dos cartas son iguales*
* *Una función que reciba dos cartas y nos devuelva un valor booleano indicando si la primera carta es inferior a la segunda (es menor que otra si su valor es inferior o si es igual pero la figura es menor según el orden lexicográfico).*
* *El programa principal generará una carta para el usuario y otra para el ordenador (deben ser diferentes). Le mostrará su carta al usuario y éste debe apostar si su carta será la mayor o la menor. El ordenador mostrará su carta y si el usuario acertó con su apuesta.*

```python
from random import randint


def generar_carta() -> dict:
    palos: list = ["oros", "copas", "espadas", "bastos"]
    carta: dict = {
        "valor": randint(1, 10),
        "palo": palos[randint(0, 3)]
    }

    return carta


def escribir_carta(carta: dict) -> None:
    print(f"{carta['valor']} de {carta['palo']}")


def son_iguales(c1: dict, c2: dict) -> bool:
    return c1['valor'] == c2['valor'] and c1['palo'] == c2['palo']


def es_inferior(c1: dict, c2: dict) -> bool:
    return c1['valor'] < c2['valor'] or (c1['valor'] == c2['valor'] and c1['palo'] < c2['palo'])


# programa principal
carta1: dict = generar_carta()
carta2: dict = generar_carta()
while son_iguales(carta1, carta2):
    carta2 = generar_carta()

print("Tu carta es: ", end="")
escribir_carta(carta1)

respuesta: str = input("¿Crees que tu carta es la mayor (si/no)? ")
if (respuesta == "si" and es_inferior(carta2, carta1)) or (respuesta == "no" and es_inferior(carta1, carta2)):
    print("Acertaste!")
else:
    print("Fallaste")

print("La carta del ordenador era: ", end="")
escribir_carta(carta2)
```

## Ejercicio 4: Frecuencias
*Hacer una función `def freqs(s)` de recibiendo un texto s, nos devuelva un diccionario indicando cada letra que aparece en el texto cuántas veces aparece. Por ejemplo: `freqs("las gafas")` daría `{'l': 1, 'a': 3, 's': 2, ' ': 1, 'g': 1, 'f': 1}`.

```python
def freqs(s: str) -> dict:
    letras: dict = {}
    for i in s:
        if i not in letras:
            letras[i] = 1
        else:
            letras[i] += 1
    return letras


# Programa principal:
texto: str = "las gafas"

print("Las letras de", texto, "son:")
print(freqs(texto))
```
