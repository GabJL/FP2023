# Clase 17: 20 de noviembre de 2023

## Ejercicio 1

*alice una función que nos diga si una cadena contiene solo letras entre la “a” y “z” (sin utilizar la función `s.isalpha()`)*

```python
def tiene_letras2(t: str) -> bool:
    # COMPLETAR
    encontrada_letra: bool = False
    for letra in t:
        if letra >= "a" and letra <= "z":
            encontrada_letra = True
    return encontrada_letra

def tiene_letras(t: str) -> bool:
    # COMPLETAR
    encontrada_letra: bool = False
    pos: int = 0
    while pos < len(t) and not encontrada_letra:
        if t[pos] >= "a" and t[pos] <= "z":
            encontrada_letra = True
        pos += 1
    return encontrada_letra

# Programa principal
s1 = "hola"
print(f"El texto -{s1}- tiene letras? {tiene_letras(s1)}")
s2 = "123a"
print(f"El texto -{s2}- tiene letras? {tiene_letras(s2)}")
s3 = "1234"
print(f"El texto -{s3}- tiene letras? {tiene_letras(s3)}")
s4 = "a123"
print(f"El texto -{s4}- tiene letras? {tiene_letras(s4)}")
s5 = "12a3"
print(f"El texto -{s5}- tiene letras? {tiene_letras(s5)}")
s6 = ""
print(f"El texto -{s6}- tiene letras? {tiene_letras(s6)}")
s7 = "HOLA"
print(f"El texto -{s7}- tiene letras? {tiene_letras(s7)}")
```

## Ejercicio 2

*Desarrollar una función `def verParéntesis(texto)` que reciba un texto que representa una expresión matemática y confirme o no que los paréntesis están equilibados. Para ello, lleve un contador que se incrementa en 1 si encuentra un ’(’ y lo decrementa en 1 si encuenta un ’)’. Si al recorrer el texto, ese contador alguna vez vale negativo o al acabar no es 0, quiere decir que no está equilibrado (y la función devolverá False). En otro caso, la expresión es correcta y devolverá True.*

```python
def verParéntesis(t: str) -> bool:
    contador: int = 0
    pos: int = 0
    es_correcto: bool = True
    while pos  < len(t) and es_correcto:
        l = t[pos]
        if l == '(':
            contador += 1
        elif l == ')':
            contador -= 1
        if contador < 0:
            es_correcto = False
        pos += 1
    return (contador == 0)
"""
    if contador == 0:
        return True
    else:
        return False
"""

s = '(2+(3 - x) *4) /(3+ y)'
print (f"{verParéntesis(s)}: {s}") # True
s = '2+(3 -x) /3+ y)'
print (f"{verParéntesis(s)}: {s}") # False
s = '('
print (f"{verParéntesis(s)}: {s}") # False
s = ') 3 + 4 ('
print (f"{verParéntesis(s)}: {s}") # False
```

## Ejercicio 3

*Realice una función que reciba un texto y nos devuelva la cantidad de palabras que tiene.*

```python
def cantidad_palabras(t: str) -> int:
    palabras: list = t.split()
    return len(palabras)


s: str = "hola y adios"
print(f"El texto -{s}- tiene {cantidad_palabras(s)} palabras")
s: str = "		hola    y 	adios	"
print(f"El texto -{s}- tiene {cantidad_palabras(s)} palabras")
s: str = "hola"
print(f"El texto -{s}- tiene {cantidad_palabras(s)} palabras")
s: str = "		hola 			  "
print(f"El texto -{s}- tiene {cantidad_palabras(s)} palabras")
s: str = ""
print(f"El texto -{s}- tiene {cantidad_palabras(s)} palabras")
s: str = "		    		"
print(f"El texto -{s}- tiene {cantidad_palabras(s)} palabras")
```

## Ejercicio 4

*Realice una función que reciba un texto y nos devuelva un texto donde las palabras estén separadas entre sí por “ – “ (espacio, guion, espacio).*

```python
def juntar_palabras(t: str) -> str:
    palabras: list = t.split()
    frase: str = " - ".join(palabras)
    return frase
    # return " - ".join(t.split())

s: str = "hola y adios"
print(f"El texto -{s}- se convierte en {juntar_palabras(s)}")
s: str = "		hola    y 	adios	"
print(f"El texto -{s}- se convierte en {juntar_palabras(s)}")
s: str = "hola"
print(f"El texto -{s}- se convierte en {juntar_palabras(s)}")
s: str = "		hola 			  "
print(f"El texto -{s}- se convierte en {juntar_palabras(s)}")
s: str = ""
print(f"El texto -{s}- se convierte en {juntar_palabras(s)}")
s: str = "		    		"
print(f"El texto -{s}- se convierte en {juntar_palabras(s)}")
```

## Ejercicio 5

*Realice una función que reciba un texto y nos devuelva un listado con la longitud de las palabras que tiene.*

```python
def tamaños_palabras(t: str) -> list:
    palabras: list = t.split()
    lista: list = []
    for palabra in palabras:
        lista.append(len(palabra))
    return lista

s: str = "hola y adios"
print(f"Las longitudes de las palabras del texto -{s}- son {tamaños_palabras(s)}")
s: str = "		hola    y 	adios	"
print(f"Las longitudes de las palabras del texto -{s}- son {tamaños_palabras(s)}")
s: str = "hola"
print(f"Las longitudes de las palabras del texto -{s}- son {tamaños_palabras(s)}")
s: str = "		hola 			  "
print(f"Las longitudes de las palabras del texto -{s}- son {tamaños_palabras(s)}")
s: str = ""
print(f"Las longitudes de las palabras del texto -{s}- son {tamaños_palabras(s)}")
s: str = "		    		"
print(f"Las longitudes de las palabras del texto -{s}- son {tamaños_palabras(s)}")
```

## Ejercicio 6

*Realice una función que reciba un texto y nos devuelva la palabra más corta.*

```python
def palabra_mas_corta(t: str) -> str:
    palabras: list = t.split()
    if len(palabras) == 0:
        corta = ""
    else:
        corta = palabras[0]
        for palabra in palabras:
            if len(palabra) < len(corta): #esta palabra es más corta de la que creia que era más corta:
                corta = palabra
    return corta

s: str = "hola y adios"
print(f"La palabra más pequeña de -{s}- es {palabra_mas_corta(s)}")
s: str = "		hola    y 	adios	"
print(f"La palabra más pequeña de -{s}- es {palabra_mas_corta(s)}")
s: str = "hola"
print(f"La palabra más pequeña de -{s}- es {palabra_mas_corta(s)}")
s: str = "		hola 			  "
print(f"La palabra más pequeña de -{s}- es {palabra_mas_corta(s)}")
s: str = ""
print(f"La palabra más pequeña de -{s}- es {palabra_mas_corta(s)}")
s: str = "		    		"
print(f"La palabra más pequeña de -{s}- es {palabra_mas_corta(s)}")
```

## Ejercicio 7

*Realice una función que reciba un texto y una letra l y nos devuelva un nuevo texto similar al original donde la letra l se reemplace por \*.*

```python
def reemplazar_letras(t: str, l: str) -> str:
    nuevo_t: str = ""
    for letra in t:
        if letra == l:
            # poner *
            nuevo_t += "*"
        else:
            # poner letra
            nuevo_t += letra
    return nuevo_t

s: str = "Informatica"
l: str = "a"
print(f"Si cambiamos a * la letra {l} en {s} sale: {reemplazar_letras(s,l)}")
s: str = "Informatica"
l: str = "I"
print(f"Si cambiamos a * la letra {l} en {s} sale: {reemplazar_letras(s,l)}")
s: str = "Informatica"
l: str = "b"
print(f"Si cambiamos a * la letra {l} en {s} sale: {reemplazar_letras(s,l)}")
```

## Ejercicio 8

*Un robot médico ha empezado a fallar y estamos examinando sus ficheros de log donde informa de todas las situaciones anómalas ocurridas y las líneas ofrecidas son del tipo:*

```
[Sat Nov 27 11:33:59 2021] init: ERROR: ConfigInitializeCommon:665: Failed to mount /usr/lib/wsl/drive
[Sat Nov 27 11:33:59 2021] init: ERROR: ConfigInitializeCommon - Failed to mount /usr/lib/wsl/lib

```
*Como puede observar el formato es `“[fecha] programa: tipo_de_mensaje: mensaje”` (observe que el mensaje puede tener internamente dos puntos). Haz una función que recibiendo una línea de ese tipo, escriba por pantalla: “El programa XXX ha dado un mensaje de tipo XXX que indica XXX, el día XXX”.*

```python
frase1: str = "[Sat Nov 13 11:33:59 2023] init: ERROR: ConfigInitializeCommon:665: Failed to mount /usr/lib/wsl/drive [Sat Nov 13 11:33:59"
fecha, resto = frase1.split("]")
fecha = fecha[1:]
textos: list = resto.split(":")
programa = textos[0].strip()
tipo = textos[1].strip()
mensaje = ":".join(textos[2:])
mensaje = mensaje.strip()
# print(textos)
texto_final = f"El programa {programa} ha dado un mensaje de tipo {tipo} que indica {mensaje}, el día {fecha}"
print(texto_final)
```

## Ejercicio 9

*Realice una función que reciba un texto largo y una palabra corta y nos devuelva una lista con las posiciones donde aparece esa palabra corta en el texto largo (puede ser vacía si no aparece). Use rangos para comparar. Por ejemplo: `posiciones(“el elemento más común es el helio”, “el”)` -> `[0, 3, 25, 29]` o `posiciones(“Informática”, “e”)` -> `[]`.*

```python
def posiciones(largo: str, corto: str) -> list:
    lista: list = []
    for pos in range(len(largo)):
        if corto == largo[pos:pos+len(corto)]:
            lista.append(pos)
    return lista

print(posiciones("el elemento mas comun es el helio", "el"))
```

