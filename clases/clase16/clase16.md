# Clase 16 (13 de noviembre de 2023)

En esta clase hemos repasado el tipo string. Luego se mostraron algunas operaciones interesantes sobre string, haciendo especial hincapié en `split` (aunque también se vió `join` y los `f-string`).

## Ejemplo de uso de split

```python
s: str = "San Sebastián: 23, 12, 13.2, AVE, 30"

print(s.split())		# Separa por los espacios
print(s.split(":"))		# Separa por los :

# Separa en dos partes (si tiene más, fallará)
ciudad, datos = s.split(":")
print("Valor de ciudad: ", ciudad)
print("Valor de datos: ", datos)

d: list = datos.split(",")	# Separa por coma
print(d)
print(int(d[0]) + int(d[1]))
```

## Ejercicio corto: De texto a lista

*Hacer una función que separe los números de una cadena como: "3.4 8.21 9.01 -34" y nos devuelva una lista de valores numéricos*

```python
def pasar_a_numeros(t: str) -> list:
    lista_texto: list = t.split()
    lista_numeros: list = []
    for valor in lista_texto:
        numero = float(valor)
        lista_numeros.append(numero)
    return lista_numeros
    
texto = "	3.4 8.29 9.01    -34"
print(pasar_a_numeros(texto))
```

## Ejercicio corto: Conversor de fechas
*Hacer una función que separe en los distintos números una fecha dada en formato estándar: "2021-11-22", y devuelva la misma fecha como cadena en formato español: "22/11/2021"*

Incluye varias versiones, una de ellas con `join`.

```python
def convertir_fecha(f_estandar: str) -> str:
    año, mes, dia = f_estandar.split("-")
    f_español = dia + "/" + mes + "/" + año
    return f_español
    

def convertir_fecha2(f_estandar: str) -> str:
    lista: list = f_estandar.split("-")
    f_español = lista[2] + "/" + lista[1] + "/" + lista[0]
    return f_español

def convertir_fecha3(f_estandar: str) -> str:
    lista: list = f_estandar.split("-")
    f_español = "/".join(lista[::-1])
    # f_español = "/".join([lista[2], lista[1], lista[0]])
    return f_español

fecha = "2023-11-13"
print("En formato español sería:", convertir_fecha(fecha))
print("En formato español sería:", convertir_fecha2(fecha))
print("En formato español sería:", convertir_fecha3(fecha))
```

## Ejercicio corto: Conversor de fechas-hora
*Dada la fecha hora con formato estándar así: "2021-11-22T12:30:01" devolver la cadena: "22/11/2021 12h 30m 01s"*

Incluye una versión con `f-string`.

```python
def convertir_fecha_hora(f: str) -> str:
    fecha, hora = f.split("T")
    año, mes, dia = fecha.split("-")
    h, m, s = hora.split(":")
    #return dia+"/"+mes+"/"+año+" "+h+"h "+m+"m "+ s+"s"
    return f"{dia}/{mes}/{año} {h}h {m}m {s}s"


tiempo: str = "2023-11-13T11:40:05"
print(f"La hora en otro formato es {convertir_fecha_hora(tiempo)}!")
```
## Ejercicio de examen 1

*Lea una línea con las notas de un alumno con el siguiente formato: "alumno: c1 c2 fi". Realice una función que reciba ese texto y nos devuelva dos valores: el nombre del alumno y su nota final (puede usar funciones auxiliares). Para calcular la nota final del alumno, wf = (10 - 0.15*c1 - 0.25*c2)/10 y después sumar todas las notas ponderadas: f*wf + 0.15*c1 + 0.25*c2.*

```python
def calcular_nota(t: str) -> (str, float):
    # Separar nombre y las notas
    nombre, notas = t.split(":")
    # Separar notas y convertirlas a números
    c1_str, c2_str, fi_str = notas.split()
    c1 = float(c1_str)
    c2 = float(c2_str)
    fi = float(fi_str)
    # Calcular notas
    wf: float = (10 - 0.15*c1 - 0.25*c2)/10
    nf: float = wf*fi + 0.15*c1 + 0.25*c2 
    # Devolver datos
    return nombre, nf

texto: str = "Tony Stark: 8 7 9.4"
nombre, nota = calcular_nota(texto)
print(f"El alumno {nombre} obtuno {round(nota,2)} como nota final")
```


## Ejercicio de examen 2

*Función `suma_numeros_encontrados()` que recibe  como parámetro una cadena caracteres con números pero que pueden estar separados por  cualquier otro carácter y devuelve la suma de todos  ellos. Así, por ejemplo, si recibe "Debe 10€ de café y 20€ de la habitación y algo (¿30€?) de propina" devuelve el número 60.*

```python
def quitar_letras(t:str) -> str:
    t2 = ""
    for letra in t:
        if letra >= "0" and letra <= "9":
            t2 = t2 + letra
        else:
            t2 = t2 + " "
    return t2

def convertir_a_numeros(t: str) -> list:
    lista_textos: list = t.split()
    lista_numeros: list = []
    for valor in lista_textos:
        lista_numeros.append(float(valor))
    return lista_numeros

def sumar(l: list) -> float:
    suma: float = 0
    for v in l:
        suma += v
    return suma

def suma_numeros_encontrados(t: str) -> float:
    t2: str = quitar_letras(t)
    lista: list = convertir_a_numeros(t2)
    suma = sumar(lista)
    return suma
    
texto: str = "Debe 10 euros y 20 € de la habitación y ¿30? de propina"
print(f"La suma de los números en '{texto}' es {suma_numeros_encontrados(texto)}")
```
