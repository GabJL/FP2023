# Clase de repaso para el primer parcial (30/10)

## Ejercicio 3 de Parcial 1 - Extra (2021)
* Realice un programa que lea un valor, n y dibuje la siguiente figura. No se permite el uso del operador * para textos.*

```
Altura: 4
*******
 *   *
  * *
   *
```

```python
altura: int = int(input("Altura: "))

# Parte superior de la figura
num_asteriscos: int = altura * 2 - 1
for a in range(num_asteriscos):
    print("*", end="")
print() # Salto de línea

# Parte central
num_lineas: int = altura - 2

num_espacios_iniciales: int = 1
num_espacios_centrales: int = 2*altura - 5

for linea in range(num_lineas):
    # Una línea
    for e in range(num_espacios_iniciales):
        print(" ", end="")
    print("*", end="")
    for e in range(num_espacios_centrales):
        print(" ", end="")
    print("*", end="")
    print()
    # Cambio para la siguiente línea
    num_espacios_iniciales += 1
    num_espacios_centrales -= 2
    
# Parte inferior
num_espacios: int = altura -1
for e in range(num_espacios):
    print(" ", end="")
print("*", end="")
print()
```

## Ejercicio 5 de Parcial 1 - Extra (2021)
*Realice un programa que lea un número entero positivo, n, y nos indique si el número es perfecto (la suma de sus divisores propios –sin considerarse el mismo- da su propio valor). Por ejemplo 6 es perfecto ya que 6 = 1 + 2 + 3. Si el número no era perfecto siga leyendo números hasta que el usuario meta un número perfecto.*

```python
def es_perfecto(n: int) -> bool:
    perfecto: bool = False
    
    suma: int = 0
    for div in range(1, n):
        if n % div == 0:
            suma += div
    
    if n == suma:
        perfecto = True
    else:
        perfecto = False
    
    return perfecto

# Programa principal
numero: int = int(input("Dime un número: "))
while not es_perfecto(numero):
    print("No es perfecto.")
    numero = int(input("Dime un número: "))

print(numero, "es perfecto")
``` 
## Ejercicio 4 del parcial de 2022
Realice un programa que lea un número entero positivo, n, y busque el primer número mayor o igual que n, tal que la suma de sus dígitos sea primo. Se valorará la eficiencia de la solución.*

```python
def es_primo(n: int) -> bool:
    div: int = 2
    while n%div != 0:
        div += 1
    return n <= div

def suma_digitos(n: int) -> int:
    # Forma 1: con str
    suma: int = 0
    n_texto: str = str(n)
    for digito in n_texto:
        suma += int(digito)
    # Forma 2: con int
    suma: int = 0
    while n != 0:
        suma += n%10
        n = n//10
    
    return suma

# Programa principal
n: int = int(input("Dime un número"))

while not es_primo(suma_digitos(n)):
    n += 1
    
print(n)
```

## Ejercicios 1 y 2 de parcial de 2021
*Estamos probando un nuevo sistema de control para deportistas de élite. Es un pequeño dispositivo que se coloca en el tobillo del jugador y nos envía constantemente varias mediciones. Actualmente estamos ajustando la medición del pulso. Realice un programa que lea las pulsaciones enviadas por el dispositivo hasta que se lo quite (cuando se desconecta envía valores negativos). Luego queremos que nos indique también cuánto tiempo (cuántas pulsaciones) están en un rango de reposo (entre 40 y 60 pulsaciones por minuto, ambos valores están incluidos). Por ejemplo, para los valores: 40, 45, 57, 60, 90, 100, 115, 123, 125, 130, 110, 121, 115, 120, 100, 90, 70, 59, -1 indicará que hubo 5 mediciones en reposo.*

*Basándose en el ejercicio anterior, realice otro que nos diga cuál fue la última vez que superó las 120 pulsaciones por minuto (ppm). Si nunca se superaron, debe mostrar un mensaje indicando tal situación. Se forma extra también queremos que nos informe cuándo superó por primera vez las 120 ppm. En el ejemplo anterior, indicará que se superó por primera vez en la medida 8 y por última vez en la 12*

```python
reposo: int = 0
p: int = int(input("Pulsaciones: "))
pos: int = 1
ultimo: int = -1
primero: int = -1

while p >= 0:
    if p >= 40 and p <= 60:
        reposo += 1
        
    if p >= 120:
        ultimo = pos
        if primero == -1: # Nunca he encontrado un valor >= 120 ya que primero contiene -1 que es un valor incorrecto
            primero = pos
    
    p = int(input())
    pos += 1
    
print("Pulsaciones en reposo: ", reposo)
print("Posición del primer valor >= 120", primero)
print("Posición del ultimo valor >= 120", ultimo)
```

## Ejercicio 2 de parcial 2022
*Realice un programa que lea números hasta que encuentre uno negativo. Tras leer los valores debe escribir cuántos números pares se leyeron. Si no se leyó ningún par simplemente deberá escribir: “No se leyó ningún valor par”. Adicionalmente se pide mostrar el menor número par leído*
```python
n: int = int(input())

contador_pares: int = 0
menor: int = n
while n >= 0:
    if n % 2 == 0:
        contador_pares += 1
        if n < menor:
            menor = n
        elif menor % 2 != 0: # menor era impar
            menor = n
    
    n = int(input())
    
if contador_pares == 0:
    print("No hay números pares")
else:
    print(menor, contador_pares)
```
