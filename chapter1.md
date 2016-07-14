# Python

Es un lenguaje de programación interpretado o de script,su sintaxis es clara, sencilla y simple, con un tipado dinámico, fuertemente tipado, multiplataforma y orientado a objetos.

## Instalación de Python

Existen diferentes implementaciones de Python, la que está instalada por defecto en la mayor parte de las distribuciones Linux y MacOS es CPython.Para comprobar si está instalado abre una terminal y escribe python. Si está instalado aparecerá la consola interactiva de Python como la siguiente:

```
$ python
Python 3.5.1 (default, Mar  3 2016, 09:29:07) 
[GCC 5.3.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> 
```

Podemos salir de la consola escribiendo `exit()` o pulsando Ctrl + D.

### Linux


Para instalar python en linux escribe el siguiente comando en una terminal, sustituye X.X por la versión de python:

```
$ sudo apt-get install pythonX.X
```


Verifica que se haya instalado python con el comando antes mencionado. También puedes verificar su versión con el siguiente comando:

```
$ python --version
```

### Windows

Para instalar en windows iremos al sitio oficial de python en la sección de [descargas](https://www.python.org/downloads/), por defecto se mostrarán los archivos correspondientes a Windows, seleccionar la versión correspondiente.

Una vez descargado python, lo ejecutaremos y seguiremos los pasos que indica el asistente, es importante tener en cuenta las rutas en donde se ha instalado python ya que posteriormente las agregaremos a las variables de entorno de windows.

Al terminar con la instalación, debemos configurar las variables de entorno con los siguientes pasos:

1. Ve a Equipo, haz clic en `Propiedades del sistema>Configuración avanzada>Variables de entorno` y seleccionar `Nueva`.

2. En el campo `Nombre de la variable` escribiremos `Python`, en `Valor de la variable` pondremos la ruta en donde se instaló Python y hacemos click en `Aceptar`

3. Ejecutar Python desde el menú inicio de nuestro sistema operativo.


>Ten en cuenta que puede variar el proceso de configuración dependiendo de la versión de Windows que tengas.



## Tipos básicos

### Números

* Enteros son todos aquellos numeros positivos o negativos que no tienen decimales

  ```python
  3
  4
  5
  ```

* Coma flotante son todos aquellos que tienen decimales, en python se expresan mediante el tipo `float`

  ```python
  34.9
  12.6 
  234.344
  ```

* Los numeros complejos son aquellos que tienen una parte real y una imaginaria y se expresan de la siguiente manera:

  ```python
  7 + 3j
  5 + j
  ```


Se puede comprobar el tipo de las variables con la función `type(nombre_variable)`.

```python
$ complejo = 7 + 3j
$ type(complejo)
<class 'complex'>
```

### Cadenas de texto

```python
"Hola mundo!"
```

### Valores booleanos

```python
True 
False
```

## Funciones

En el lenguaje de programación de Python, se declara una función con la palabra `def`, el nombre de la función y retorna el valor resultante de la operación usando `return`, si no hay un valor de retorno se regresará `None`.

En Python:

```python
def sumar(x, y):
  return x + y

print(sumar(3, 2))
```

Ejemplo de una función que puede devolver varios valores.

> En C solo se puede devolver un solo valor.

En Python, se declara la función multiplicacion y retorna dos valores. Estas multiplicaciones que regresa la funcion son asignadas a dos variables, donde en el caso de python no es necesario hacerlas independientemente, sino que se pueden definir separandolas por una coma.

```python
def multiplicacion(x, y):
  return x * 2, y * 2
a, b = funcion(1, 2)

print (a, b)
```

* \[ \] El paso es por valor, pero se pasa la dirección del objecto no como tal los valores, solo falta aclarar un poco este concepto. Te puedes basar en el siguiente [link](http://stackoverflow.com/questions/986006/how-do-i-pass-a-variable-by-reference)
  En C los argumentos de una funcion se pasan por valor, pero también está el paso por referencia utilizando punteros.
  En Python cuando se pasa un argumento a una función es por valor, sin embargo el parámetro que se pasa es la dirección del objeto.

## Tipos de colecciones de datos

### Listas

Es un tipo de estructura de datos, y es similar a lo que en otros lenguajes, conocemos como arrays, la diferencia radica en que las listas pueden aumentar o disminuir sus dimensiones al momento de ejecutar el script o programa.
En las listas podemos ordenar cualquier tipo de dato: números, cadenas, booleanos, incluso listas, entre otros.

### Tuplas

En las tuplas, los valores creados al inicio ya no se pueden modificar después y su tamaño es fijo. Una ventaja de las tuplas es que son más ligeras que las listas.

### Diccionarios

Los diccionarios son colecciones que relacionan una clave y un valor.

* \[ \] Definir que es un diccionario, el texto me dice que es una lista de elementos solo se necesita especificar un poco más sino puede confundirse con una lista.

* \[ \] Podemos agregar una pequeña descripción de por que en python es distinto que en C, es decir por que no tengo que usar indices. - \[ \] El punto anterior nos puede llevar a que es un iterador, recomiendo explicar brevemente con un ejemplo [con gatitos quedaria bien](http://nvie.com/img/iterable-vs-iterator.png)

En Python:

```python
lista_animales = ['gato', 'elefante', 'rinoceronte']
for animal in lista_animales:
  print ("El animal es:", animal, "la cantidad de letras:", len(animal))
```

* \[ \] Como funcionan los argumentos variables, esto argumentos funcionan como una lista.

```python
def suma(*numeros):
    total = 0
    for i in range(len(numeros)):
        total = total + numeros[i]
    return total

print suma(3, 2, 2)
```

```python
def multiplicacion(*numeros):
    total = 1
    for i in range(len(numeros)):
        total = total * numeros[i]
    return total

print multiplicacion(2, 1, 3, 4)
```

