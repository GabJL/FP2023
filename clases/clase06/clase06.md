# Clase 6 (2 de octubre de 2023)

En esta clase se repasó la parte de condiciones, sentencias de selección y se empezó a trabajar con sentencias de repetición.

A continuación se muestran los códigos trabajados en clase o aquellos que se dejaron para que los intentase el alumnado.

Especialmente importante para la parte de bucles son los [ejercicios cortos finales](#ejercicios-cortos).

## Calculadora

*Realice un programa que actúe como una calculadora simple. Para ello debemos leer dos valores reales, que serán los operadores y una letra, operador. Las posibles operaciones permitidas son +, -, \* o /.*

*Como resultado debe dar el valor de evaluar la operación o ERROR si no fue posible realizarla.*

Es un ejemplo típico de sentencia de selección múltiple.

```python
perando1: float = float(input("Dime el primer operando: "))
operando2: float = float(input("Dime el segundo operando: "))
operación: str = input("Dime qué operación hacer: ")

es_correcto: bool = True
if operación == "+":
  resultado = operando1 + operando2
elif operación == "-":
  resultado = operando1 - operando2
elif operación == "*":
  resultado = operando1 * operando2
elif operación == "/":
  if operando2 == 0:
    print("No se puede dividir entre 0")
    es_correcto = False
  else:
    resultado = operando1 / operando2
else:
  print("Operación inválida")
  es_correcto = False

if es_correcto:
  print(operando1, operación, operando2, "=", resultado)
```

## Ecuación de segundo grado

*Modifique el ejemplo del principio del tema, para que como respuesta el programa indique cuántas soluciones reales tiene (0, 1, 2 o infinitas) y en caso de tener un número contable que indíquelas.*

*Antes de empezar a programar piense los posibles casos:*
* *Hay una situación en la que hay infinitas soluciones*
* *Hay dos situaciones en las que no hay solución (al menos real)*
* *Hay dos situaciones en las que solo hay una solución*
* *Hay una situación en las que hay dos soluciones diferentes*

*Lea los coeficientes y calcule el discriminante (b*b-4ac). Posteriormente use una sentencia de selección múltiple para identificar los casos (únalos cuando sea posible) y calcule las soluciones.*

En este caso no se desarrolló el código pero si se identificaron los casos correspondientes:
* Hay una situación en la que hay infinitas soluciones
    * Si a, b y c son 0
* Hay dos situaciones en las que no hay solución (al menos real)
    * Si es discriminante es negativo
    * Si a y b son 0 y c no lo es
* Hay dos situaciones en las que solo hay una solución
    * a es 0 y b no lo es
    * El discriminante es 0
* Hay una situación en las que hay dos soluciones diferentes
    * El discriminante es positivo y mayor que 0 y a no es 0

## Escribir N "Hola Mundo!"

*Realice un programa que escriba N (siendo N leído de teclado) veces la frase "Hola Mundo!"*

Ejemplo usado para introducir el bucle `while`.

```python
N: int = int(input("Dime cuantas veces quieres que diga hola: "))

num_veces: int = 0
while num_veces < N:
  print("Hola Mundo!")
  num_veces += 1
```

## Tabla del 7

*Realice un programa que escriba la tabla de multiplicar del 7.*

Otro ejemplo usado para introducir el bucle `while`.

```python
num: int = 1
while num <= 10:
  print("7 x", num, "=", 7*num)
  num += 1
```

## Ejercicios cortos

### Ejercicio 1
*Lee 20 números y nos diga cuántos 0s hay*

Un elemento importante a destacar en este ejercicio, es que realmente no nos interesan los números concretos que hemos leído hasta el momento si no hay variable que nos almacene un resumen (de la parte que nos interese) de todos esos valores. Es decir, no nos interesa saber si el usuario ha metido 0 1 3 5 0 2 sino que hemos leído 2 ceros. Por ello, tendremos una variable `contador_de_0s` que nos almacene ese valor mientras que los números leídos los podemos ir machacando. Este tipo de variable que resumen los datos contando los valores que cumplen cierta propiedad se denominan **contadores**.

```python
MAX: int = 20 # Valores a leer para las pruebas se puede bajar a algo más manejable (3 o 4)

contador_de_0s: int = 0 # No hemos leído ningún 0
num_veces: int = 0 # Número de números leídos

while num_veces < MAX:
  num: int = int(input("Dime un número: ")) # Valor actual
  if num == 0:
    contador_de_0s += 1
  num_veces += 1

print("Se han leído", contador_de_0s, "0s")
```


### Ejercicio 2
*Lee 10 números y nos diga su suma*

Similar al ejercicio anterior pero en este caso no nos interesa contar, sino sumar (acumular) todos los valores. Estas variables se denominan **acumuladores**.

```python
MAX: int = 10 # Valores a leer para las pruebas se puede bajar a algo más manejable (3 o 4)

suma: int = 0 # No hemos leído ningún valor por lo tanto la suma actual es 0
num_veces: int = 0 # Número de valores leídos

while num_veces < MAX:
  num: int = int(input("Dime un número: ")) # Valor actual
  suma += num
  num_veces += 1

print("La suma vale", suma)
```

### Ejercicio 3
*Modifique el anterior para calcular la media de los números leídos*

Sabiendo la suma de los valores, calcular la media es bastante sencillo, ya que solo hay que dividir esa suma entre el número de valores (10).

```python
MAX: int = 10 # Valores a leer para las pruebas se puede bajar a algo más manejable (3 o 4)

suma: int = 0 # No hemos leído ningún 0

num_veces: int = 0

while num_veces < MAX:
  num = int(input("Dime un número: "))
  suma += num
  num_veces += 1

print("La media vale", suma/10)
```


