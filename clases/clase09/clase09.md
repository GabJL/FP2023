# Clase 9: 11 de octubre de 2022

En esta clase hicimos un ejercicio avanzando como el de los 12 y después se resolvió ejercicios de parciales de otros años

# EC0: mcm:
*Calcule el mcm de dos números*

Aquí se pueden plantear diferentes acercamientos, el más eficiente que diseñamos parte de las siguientes premisas:
* Sabemos que el mcm es siempre más grande o igual que el mayor de los dos números.
* Entonces si partimos del mayor y vamos sumando el propio valor, generamos sus múltiplos (mayor*1, mayor*2, mayor*3...)
* Así que en el bucle solo debemos comprobar si es o no divisor del menor:

```python
a: int = int(input("a: ")
b: int = int(input("b: ")

if a > b:
  mayor = a
  menor = b
else:
  mayor = b
  menor = a

mcm: int = mayor
while mcm%menor != 0:
  mayor += mayor

print("El mcm de", a,"y", b, "es", mcm)
```

# EC1: Primer y último 12:

*Escribe un algoritmo que lea una lista de números enteros terminada en 0 y que encuentre y escriba en la pantalla al posición de la primera y última ocurrencia del número 12 dentro de la lista. Si el número 12 no está en la lista, el algoritmo debe escribir 0.*

Esto es un ejemplo de ejercicio avanzado que, salvo que se tenga experiencia, hay que ir resolviendo poco a poco:
* Primero leer hasta 0 (esto es un caso tradicional de lectura adelantada)
* Luego tenemos que ir contando las posiciones de los números que leemos:
  * En la primera lectura (la adelantada al bucle) indicamos que es la primera
  * Luego cada vez que leamos en el bucle decimos que hemos leído una mas.
* El siguiente punto es cómo saber la posición del último:
  * En el enunciado nos indica que si no existe ningún 12 devolvamos un 12, entonces se puede inicializar a 0
  * Luego cada vez que leamos un 12 debemos actualizarlo ya que ese doce leído es posterior a cualquiera que hayamos leído antes
* El último punto es cómo saber la primera posición:
  * Aquí el problema es distinguir si un 12 es el primero o no.
  * Si inicializamos el primero a 0 (por el mismo motivo que el último), eso ayuda a identificar el primero, ya que si la posición del primero es 0 (que es una posición incorrecta) quiere decir que aún no hemos leíso ningún doce y podemos actualizarlo. Luego ya la posición será diferente de 0 y no se actualizará más

```python
número: int = int(input("Dime un número: ")) # Lectura previa al bucle
pos_actual: int = 1
pos_ult_12: int = 0
pos_primer_12: int = 0
while número != 0:
  # Hacer cosas con "número"
  if número == 12:
    pos_ult_12 = pos_actual
      if pos_primer_12 == 0:
        pos_primer_12 = pos_actual
  número = int(input("Dime otro número: ")) # Lee un valor para la siguiente iteración
  pos_actual += 1

print("El último 12 está en la posición", pos_ult_12)
print("El PRIMER 12 está en la posición", pos_primer_12)
```

## EC2 (Ej 1 de Parcial 2021/2022 B)
*Hacer un programa que pide números enteros hasta el 0. El programa después debe indicar si todos los números estaban en orden, por ejemplo -3 5 5 9 0 diría True, con 0 también diría True pero con 8 7 0 diría False.*

```python
número: int = int(input("Dime un número: ")) # Lectura previa al bucle

anterior: int = número - 1 # Cualquier valor <= número vale
esta_ordenado: bool = True
while número != 0:
  # Hacer cosas con el número
  if número < anterior:
    esta_ordenado = False
  anterior = número
  número: int = int(input("Dime otro número: "))
    
if esta_ordenado:
  print("Está ordenado")
else:
  print("No está ordenado")
```

### EC6 (Ej 3 de diferentes parciales)
*Hacer programas que pinte las siguientes figuras. Los . son espacios, no hay que imprimirlos, sólo están para que se puedan ‘ver’ los espacios y facilitar el contarlos:*

```
...****
..*....*
.*......*
**********
```

```python
inferior: int = int(input("Parte de abajo: "))
superior: int = int(input("Dime la parte de arriba: "))

#  Primera linea
espacios: int = (inferior-superior)//2
astericos: int = superior
for e in range(espacios):
  print(".", end="")
for a in range(asteriscos):
  print("*", end= "")
print()

# Parte central
lineas: int =  (inferior-superior)//2 - 1
espacios1: int = (inferior-superior)//2 - 1
espacios2: int = superior
for l in range(lineas):
  for e in range(espacios1):
    print(".", end="")
  print("*", end="")
  for e in range(espacios2):
    print(".", end="")
  print("*", end="")
  print()
  espacios1 -= 1
  espacios2 +=  2
    
# Última linea
asteriscos = inferior
for i in range(asteriscos):
  print("*", end= "")
print()
```

