# Clase 22: 11 de diciembre de 2021

En esta clase seguimos repasando ficheros y hacemos ejercicios de examen:

## Ejercicio 1: 
*Hacer una función (`def esc(l1: list, l2: list) -> float`) que devuelva el producto escalar de los dos vectores recibidos como parámetros, esto es: suma de los productos de los correspondientes componentes. Suponer que siempre los vectores recibidos tienen ambos la misma longitud. Probar:*

```python
print(esc([1.0, 2, 3], [3, 2, 1])) # 10.0
print(esc([0, 1.1, 0, 2], [-1, 10, 0, 2])) # 15.0
```

```python
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
```


## Ejercicio 4:

*Suponer que tenemos un fichero con los nombres de estudiantes y una serie de calificaciones en una cantidad dada, para todos igual, de asignaturas. Hacer una función `lee_notas(nombre_fichero: str) -> dict` que recibe el nombre de ese fichero y devuelve un diccionario del tipo: `{'Pedro Perez': [2.0, 6.0, 3.0, 8.1], 'Maria ... ': [1.0, 7.0, ...], ...}` Imprimir este diccionario para comprobar su contenido. Luego, realice otra función que nos devuelva el alumno con nota media más alta (todas las notas tienen el mismo peso). Usar como ejemplo el fichero [`notas.txt`](notas.txt) al final*

```text
ro Pérez: 2, 6, 3 ,8.1
María Rodríguez: 1, 7,7, 4
Ana Gómez: 5, 5,6, 5
```
```python
```

## Ejercicio 5:

*Usaremos los diccionarios que se proporciona en el fichero [poblaciones.txt](poblaciones.txt). Se pide definir una función `def pobComunidad(comunidad)` que devuelva la población total de una comunidad autónoma, por ejemplo: `pobComunidad("Andalucía")` devolvería: `2394851`. Probar la función con esa comunidad e imprimir el número resultante. No se requiere `input()`.*

```python
```

## Ejercicio 6:
*En el fichero [series.txt](series.txt), se muestra la información (nombre y descripción) de las series más populares de 2021 (según IMDB). Realice una función `def leeSeries(nombFich)` que nos devuelva un diccionario con el contenido del fichero. Como clave tendremos el nombre de la serie y como valor su descripción.*

*También desarrolle otra función `def buscarSerie(series, palabra)` que nos devuelva una lista con los títulos de las series donde en su descripción aparece la palabra. En el programa principal escriba el contenido de esa lista. Por ejemplo, con `buscarSerie(series, "Avengers")` escribiría `["Loki", "The Falcon and the Winter Soldier"]`.*

```python
```
