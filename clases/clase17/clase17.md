# Clase 17: 20 de noviembre de 2023

## Ejercicio 1

*alice una función que nos diga si una cadena contiene solo letras entre la “a” y “z” (sin utilizar la función `s.isalpha()`)*

```python
```

## Ejercicio 2

*Desarrollar una función `def verParéntesis(texto)` que reciba un texto que representa una expresión matemática y confirme o no que los paréntesis están equilibados. Para ello, lleve un contador que se incrementa en 1 si encuentra un ’(’ y lo decrementa en 1 si encuenta un ’)’. Si al recorrer el texto, ese contador alguna vez vale negativo o al acabar no es 0, quiere decir que no está equilibrado (y la función devolverá False). En otro caso, la expresión es correcta y devolverá True.*

```python
```

## Ejercicio 3

*Realice una función que reciba un texto y nos devuelva la cantidad de palabras que tiene.*

```python
```

## Ejercicio 4

*Realice una función que reciba un texto y nos devuelva un texto donde las palabras estén separadas entre sí por “ – “ (espacio, guion, espacio).*

```python
```

## Ejercicio 5

*Realice una función que reciba un texto y nos devuelva un listado con la longitud de las palabras que tiene.*

```python
```

## Ejercicio 6

*Realice una función que reciba un texto y nos devuelva la palabra más corta.*

```python
```

## Ejercicio 7

*Realice una función que reciba un texto y una letra l y nos devuelva un nuevo texto similar al original donde la letra l se reemplace por \*.*

```python
```

## Ejercicio 8

*Un robot médico ha empezado a fallar y estamos examinando sus ficheros de log donde informa de todas las situaciones anómalas ocurridas y las líneas ofrecidas son del tipo:*

```
[Sat Nov 27 11:33:59 2021] init: ERROR: ConfigInitializeCommon:665: Failed to mount /usr/lib/wsl/drive
[Sat Nov 27 11:33:59 2021] init: ERROR: ConfigInitializeCommon - Failed to mount /usr/lib/wsl/lib

```
*Como puede observar el formato es `“[fecha] programa: tipo_de_mensaje: mensaje”` (observe que el mensaje puede tener internamente dos puntos). Haz una función que recibiendo una línea de ese tipo, escriba por pantalla: “El programa XXX ha dado un mensaje de tipo XXX que indica XXX, el día XXX”.*

```python
```

## Ejercicio 9

*Realice una función que reciba un texto largo y una palabra corta y nos devuelva una lista con las posiciones donde aparece esa palabra corta en el texto largo (puede ser vacía si no aparece). Use rangos para comparar. Por ejemplo: `posiciones(“el elemento más común es el helio”, “el”)` -> `[0, 3, 25, 29]` o `posiciones(“Informática”, “e”)` -> `[]`.*

```python
```

