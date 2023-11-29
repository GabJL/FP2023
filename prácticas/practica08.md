# Práctica 8: Diccionarios

## Ejercicio de casa: Fútbol

*Vamos a desarrollar un único ejercicio (p8e01.futbol.py) con varios apartados. Se va a leer de un fichero los resultados de los partidos de fútbol de La Liga 23/24 jugados hasta la fecha y obtendremos diferentes resultados de tratarlo.*

*__Lectura del fichero:__*

*En el campus virtual se facilita el fichero [futbol.txt](futbol.txt) que tiene el siguiente contenido (se muestran las primeras líneas):*
```
  1. UD Almería, Rayo Vallecano, 0-2
  1. Athletic Club de Bilbao, Real Madrid CF, 0-2
  1. Club Atlético de Madrid, Granada CF, 3-1
  1. RC Celta, CA Osasuna, 0-2
  1. Sevilla FC, Valencia CF, 1-2
  1. UD Las Palmas, RCD Mallorca, 1-1
       ...
```
Es decir, son un conjunto de líneas, cada una de las cuales representa un partido y tiene el siguiente formato:

```
Jornada. Equipo_local, Equipo_visitante, goles_local-goles_visitante
```

*__Apartado A (★★★★✰)__ Desarrollar una función `def obtener_partido(p: str) -> dict` que reciba una cadena de caracteres `s` con el formato anterior y nos devuelva un diccionario con los datos separados. Por ejemplo `obtener_partido("1. UD Almería, Rayo Vallecano, 0-2")` devolvería el diccionario `{"jornada": 1, "local": "UD Almería", "visitante": "Rayo Vallecano", "goles_local": 0, "goles_visitante": 2}`. Observe que los campos jornada, goles_locales y goles_visitante deben ser números naturales y local y visitante serán textos. Use `split()`.*

*__OBJETIVOS__: Realizar funciones y uso avanzado del `split`.*

*__Apartado B (★★✰✰✰)__ Desarrollar una función `def leer_fichero(s: str) -> list` que reciba el nombre del fichero en `s` y lee el fichero con el formato anteriormente descrito. Como resultado debe devolver una lista de partidos. El esquema para leer un fichero es el siguiente:*

```python
# Abrir el fichero s con codificación "utf-8": 
f = open(s, encoding = "utf-8")
# TODO: Crear lista vacía
# Para cada línea del fichero
for linea in f:
	# Obtener un partido a partir de la línea del fichero
      d: dict = obtener_partido(linea)
	# TODO: Añadir el partido a la lista
# Cerrar fichero
f.close()
```
*__OBJETIVOS:__ Leer un fichero y generar una lista de diccionarios*

*__Apartado C (★✰✰✰✰)__ En la parte del programa principal, llame de forma apropiada a leer_partidopara obtener los datos del partido  y  muestre  por  pantalla  cuántos  partidos  se  leyeron  con  el  siguiente  formato: `Se  han  cargado XXX partidos correctamente`donde `XXX`(deberían ser 128) serán los partidos que se han leído del fichero.*

*__OBJETIVOS:__ Uso de funciones.* 

*__Operaciones sencillas:__*

*__Apartado D (★★★✰✰)__ Desarrolle una función `def partidos_equipo(lista: list, equipo: str) -> None`que reciba el nombre de un equipo y nos  muestre  por  pantalla  los  partidos  en  los  intervino  dicho  equipo. Cada  partido  debe  mostrarse  con  el  formato mostrado en este ejemplo:*
```
Cádiz CF 0 - 1 Real Sociedad de Fútbol
```

*En el programa principal llame a la función con un equipo fijo (el que prefiera).*

*__OBJETIVOS:__ Mostrar datos filtrados de un listado.*

*__Apartado E (★★✰✰✰)__ Hacer función `def goles_equipo(lista: list, equipo: str) -> (int, int)`que nos devuelva cuantos goles ha marcado (goles a favor) y cuántos ha recibido (goles en contra) del equipo que pasan como parámetro. En el programa principal llame a esta función de forma apropiada. Por ejemplo, para `goles_equipo(l, "Cádiz CF")`devolvería `10` a favor y `17` en contra.*

*__OBJETIVOS:__ Cálculos sobre datos que cumplen cierta condición.*

*__Operaciones avanzadas:__*

*__Apartado F (★★★★★)__ Desarrollar una función que partiendo del listado de partidos devuelva un diccionario que tenga como clave el nombre de un equipo y como valor tendrá cuántos puntos ha conseguido. Un equipo consigue 3 puntos si gana un partido, 1 punto se lo empata y no consigue puntos si pierde. El contenido de ese diccionario debería contener: `{'UD Almería': 3, 'Rayo Vallecano': 18, 'Athletic Club de Bilbao': 24, 'Real Madrid CF': 32, 'Club Atlético de Madrid': 28, …}`*

*__OBJETIVOS:__ Generación de un diccionario a partir de una lista.*

*__Apartado  G  (★★★★✰)__ Implemente  otra  función  que,  recibiendo  el  diccionario  previamente  generado,  nos  indique quién va en el primer puesto de la liga (el que tenga más puntos). Con los datos del fichero, el líder es `Girona FC`.*

*__OBJETIVOS:__ Mayor de un diccionario.*

*__Apartado H (★★★✰✰)__ Realizar otra función que, recibiendo el diccionario previamente generado y el nombre de un equipo, nos indique cuál es su puesto en la clasificación (su puesto viene determinado por cuántos equipos tienen más puntos que él, puede suponer que está delante de todos los que tiene sus mismos puntos). Por ejemplo, como posición del `Cádiz CF`debería devolver `16`.*

*__OBJETIVOS:__ Contar cuántos cumplen cierta propiedad.*

```python
# FUNCIONES
def obtener_partido(s: str) -> dict:
    jornada, resto = s.split(".")
    local, visitante, resultado = resto.split(",")
    goles = resultado.split("-")
    partido = {
            "jornada": int(jornada),
            "local": local.strip(),
            "visitante": visitante.strip(),
            "goles_local": int(goles[0]),
            "goles_visitante": int(goles[1])
    }
    return partido


def leer_fichero(s: str) -> list:
    fichero = open(s, encoding="utf-8")
    lista: list = []
    for línea in fichero:
        partido = obtener_partido(línea)
        lista.append(partido)
    fichero.close()
    return lista


def partidos_equipo(l: list, e: str) -> None:
    for p in l:
        if p["local"] == e or p["visitante"] == e:
            print(f"{p['local']} {p['goles_local']} - {p['goles_visitante']} {p['visitante']}")


def goles_equipo(l: list, e: str) -> (int, int):
    goles_favor: int = 0
    goles_contra: int = 0
    for p in l:
        if p["local"] == e:
            goles_favor += p["goles_local"]
            goles_contra += p["goles_visitante"]
        elif p["visitante"] == e:
            goles_contra += p["goles_local"]
            goles_favor += p["goles_visitante"]
    return goles_favor, goles_contra


def obtener_puntuación(l: list) -> dict:
    puntos = {}
    for p in l:
        if p["goles_local"] > p["goles_visitante"]:
            p_l = 3
            p_v = 0
        elif p["goles_local"] == p["goles_visitante"]:
            p_l = 1
            p_v = 1
        else:
            p_l = 0
            p_v = 3
            
        if p["local"] in puntos:
            puntos[p["local"]] += p_l
        else:
            puntos[p["local"]] = p_l
            
        if p["visitante"] in puntos:
            puntos[p["visitante"]] += p_v
        else:
            puntos[p["visitante"]] = p_v
    return puntos


def líder(puntos: dict) -> str:
    l: str = list(puntos)[0]
    for e in puntos:
        if puntos[l] < puntos[e]:
            l = e
    return l


def posicion(puntos: dict, eq: str) -> int:
    pos: int = 1
    for e in puntos:
        if puntos[e] > puntos[eq]:
            pos += 1
    return pos


# Programa principal
partidos = leer_fichero("futbol.txt")
print("Se han cargado", len(partidos), "partidos correctamente")
partidos_equipo(partidos, "Cádiz CF")
print(goles_equipo(partidos, "Cádiz CF"))
puntuacion = obtener_puntuación(partidos)
print(puntuacion)
print("El líder es", líder(puntuacion))
print("La posición del Cádiz CF es", posicion(puntuacion, "Cádiz CF"))
```

