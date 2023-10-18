# Clase 10: 18 de octubre de 2022

Un par de ejercicios de repaso (en los del tema 4 de esta clase también hay alguno)


## Ejemplo: Secuencia
*Haz un programa, llamado a05e02.secuencia.py que dada una secuencia de números naturales leída de teclado y terminada en 0, averiguar si existe un elemento cuyo valor coincide con la suma de los que le proceden. La secuencia tendrá al menos 2 valores diferentes a 0. Por ejemplo, la secuencia 1, 1, 2, 5, 0 satisface la propiedad, sin embargo, la secuencia 1, 3, 1, 2, 0 no la satisface.*

```python
print("Dime una serie de valores acabados en 0: ")

cumple_propiedad: bool = False
suma: int = 0

n: int = int(input(""))
while n != 0:
  n = int(input())
  if n == suma:
    cumple_propiedad = True
  suma += n

if cumple_propiedad:
  print("La secuencia sí cumple la propiedad")
else:
  print("La secuencia no cumple la propiedad")      
```


## Números romanos

*Realice un programa que pase de número romanos a números arábigos*

```python
numero_romano: str = input("Numero en romano: ")
numero_decimal: int = 0
tengo_valor_anterior: bool = False
for letra in numero_romano:
    # hacer cosas con letra
    if letra == "M":
        valor = 1000
    elif letra == "D":
        valor = 500
    elif letra == "C":
        valor = 100
    elif letra == "L":
        valor = 50
    elif letra == "X":
        valor = 10
    elif letra == "V":
        valor = 5
    else:
        valor = 1
    if tengo_valor_anterior:
        if valor_anterior < valor:
            numero_decimal += (valor - valor_anterior)
            tengo_valor_anterior = False
        else:
            numero_decimal += valor_anterior
            valor_anterior = valor
            tengo_valor_anterior = True
    else:
        valor_anterior = valor
        tengo_valor_anterior = True

if tengo_valor_anterior:
    numero_decimal += valor_anterior

print("El número en decimal es: ", numero_decimal)
```
