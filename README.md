# Reto 1

1.Crear una función que realice operaciones básicas (suma, resta, multiplicación, división) entre dos números, según la elección del usuario, la forma de entrada de la función será los dos operandos y el caracter usado para la operación. entrada: (1,2,"+"), salida (3).

Para este punto se definieron las 4 operaciones básicas a través de funciones. Y luego después de definir las funciones, se le pide al usuario que ingrese dos números y el signo de la operación. Con un match y case imprimimos el resultado de la función correspondiente al signo ingresado. En caso de que se ingrese un caracter erróneo se imprime un mensaje de advertencia.

```python
def suma(a,b) -> float:
    return a + b
def resta(a,b) -> float:
    return a-b
def multiplicación(a,b) -> float:
    return (a*b)
def división(a,b) -> float:
    return(a/b)

if __name__=="__main__":
    a = float(input("Ingrese un número cualquiera: "))
    b = float(input("Ingrese otro número: "))
    signo = str(input("Ingrese el signo de la operación que desea realizar: "))
    match signo:
        case "+":
            print("La suma de " + str(a) + " y " + str(b) + " es " + str(suma(a,b)))
        case "-":
            print("La resta de " + str(a) + " y " + str(b) + " es " + str(resta(a,b)))
        case "*":
            print("La multiplicación de " + str(a) + " y " + str(b) + " es " + str(multiplicación(a,b)))
        case "/":
            print("La división de " + str(a) + " y " + str(b) + " es " + str(división(a,b)))
        case _:
            print("""Ingresa un signo de suma(+), multiplicación(*), resta(-) o división(/)""")
```
2.Realice una función que permita validar si una palabra es un palíndromo. Condición: No se vale hacer slicing para invertir la palabra y verificar que sea igual a la original.

Para este punto se hizo un ciclo for con el fin de iterar sobre cada letra de la palabra. Utilizando loos índices comparamos la primera letra con la última, la segunda con la penúltima y así sucesivamente para saber que son iguales. Si se verifica que esto sucede en todos los casos, devuelve un True, es decir que es un palíndromo, en caso contrario devuelve un False.

```python
def palindromo(palabra) -> str:
    for letra in range(len(palabra)):  #Recorremos cada letra de la palabra
        if palabra[letra] == palabra[len(palabra)-letra-1]:  #Se compara la letra del inicio con la que está al final (Es como el índice inicial y el índice a la reversa)
            return True
        else:
            return False

if __name__ == "__main__":
    palabra = str(input("Ingrese una palabra: "))
    if palindromo(palabra):
        print("La palabra ingresada es palindromo")
    else:
        print("La palabra ingresada no es palindromo")
```
Escribir una función que reciba una lista de números y devuelva solo aquellos que son primos. La función debe recibir una lista de enteros y retornar solo aquellos que sean primos.

Se inicializa i en dos y se le suma uno iterativamente para que se compruebe que no es posible dividir el número en la lista dada (En dado caso significa que es primo, ya que el residuo no daría cero).Se comprueba esto con cada número en la lista dada con un ciclo for y hasta que el número sea menor que i al cuadrado.
```python
def numeros_primos(lista):
    for num in lista:
        if num <= 1:
            return False
        i = 2
        while i * i <= num:
            if num % i == 0:
                return False
            i += 1
    return True

if __name__ == "__main__":
    lista = []
    lista_primos = []
    while True:
        numeros = input("Ingrese un número entero cualquiera (Vacío para terminar): ")
        if numeros == "":
            break
        numeros = int(numeros)
        lista.append(numeros)
    
    for num in lista:
        if numeros_primos([num]):
            lista_primos.append(num)
    
    if lista_primos:
        print("Los números primos en la lista son:", lista_primos)
    else:
        print("No hay números primos en la lista dada")
```
4.Escribir una función que reciba una lista de números enteros y retorne la mayor suma entre dos elementos consecutivos.
Primero se establece mayor suma a la sumna de los dos primeros elementos de la lista. Luego se suman los siguientes elementos y así sucesivamente utilizando el índice de i y i + 1 para iterar. En caso de que la siguiente suma sea mayor que la anterior, se establece la más reciente como "mayor suma" y así hasta completar todos los números de la lista.

```python
def mayor_suma(lista):
    mayor_suma = lista[0] + lista[1]
    for i in range(1, len(lista)-1):
        siguiente_suma = lista[i] + lista[i+1]     
        if siguiente_suma > mayor_suma:
            mayor_suma = siguiente_suma
    
    return mayor_suma


if __name__ == "__main__":
    lista = []
    while True:
        numeros = input("Ingrese un número entero cualquiera (Vacío para terminar): ")
        if numeros == "":
            break
        numeros = int(numeros)
        lista.append(numeros)
    
    print("La mayor suma entre dos números consecutivos es ", mayor_suma(lista))
```
5.Escribir una función que reciba una lista de string y retorne unicamente aquellos elementos que tengan los mismos caracteres. e.g. entrada: ["amor", "roma", "perro"], salida ["amor", "roma"]

Se utiliza un ciclo for aninado para comparar todas las palabras entre sí. Si ambas palabras son distintas y al organizar las letras con "sorted", se tienen las mismas letras y en la misma cantidad, entonces se añaden a una lista creada llamada lista_anagramas.

```python
def anagrama(lista_palabras):
    lista_anagramas = []
    for palabra1 in lista_palabras:
        for palabra2 in lista_palabras:
            if palabra1 != palabra2 and sorted(palabra1) == sorted(palabra2):
                lista_anagramas.append(palabra1)
                lista_anagramas.append(palabra2)
    return lista_anagramas

if __name__ == "__main__":            
    lista_palabras = []
    while True:
        palabra = input("Ingrese una palabra cualquiera (Vacío para terminar): ")
        if palabra == "":
            break
        lista_palabras.append(palabra)
    
    anagramas = anagrama(lista_palabras)
    if anagramas:
        print("Las palabras que son anagramas entre sí son:", anagramas)
    else:
        print("No hay anagramas en la lista de palabras.")
```
