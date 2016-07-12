# Python

Es un lenguaje de programación interpretado o de script,su sintaxis es clara, sencilla y simple, con un tipado dinámico, fuertemente tipado, multiplataforma y orientado a objetos.

### Instalación de Python

Existen diferentes implementaciones de Python, la que está instalada por defecto en la mayor parte de las distribuciones Linux y MacOS es CPython.Para comprobar si está instalado abre una terminal y escribe python. Si está instalado aparecerá la consola interactiva de Python como la siguiente:

```
$ python
Python 3.5.1 (default, Mar  3 2016, 09:29:07) 
[GCC 5.3.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> 
```

Podemos salir de la consola escribiendo exit\(\) o pulsando Ctrl + D.

Si no se muestra algo parecido no te preocupes, instalar Python es muy sencillo. Puedes [descargar](https://www.python.org/downloads/)  la versión correspondiente a tu sistema operativo.

### Funciones

Ejemplo de una función que retorna un solo valor.
Este es un ejemplo de como se retorna un valor en C, con una función llamada sumar, donde los parámentros declarados como enteros "x" y "y" retornan la suma de ellos.

```c
int sumar(int x, int y){
  return x + y;
}

main(){
  printf("%d", sumar(3, 2));
}
```

El mismo ejemplo anterior ahora representado en el lenguaje de programación de Python, donde se declara la función con la palabra def, el nombre de la función y retorna la misma operacion de suma.

En Python:

```python
def sumar(x, y):
  return x + y

print(sumar(3, 2))
```

Ejemplo de una función que puede devolver varios valores.

> En C solo se puede devolver un solo valor.

En Python, se declara la función multiplicacion y retorna dos operaciones. Estas multiplicaciones que regresa la funcion son asignadas a dos variables, donde en el caso de python no es necesario hacerlas independientemente, sino que se pueden definir separandolas por una coma.

```python
def multiplicacion(x, y):
  return x * 2, y * 2
a, b = funcion(1, 2)

print (a, b)
```

### Diccionarios

En el lenguaje de programación C, se utiliza un arreglo o estructuras para declarar una lista de elementos en una variable, sin embargo en python a esa estructura se le llama diccionario.

En C:

```c

```
En Python:
```python
lista_animales = ['gato', 'elefante', 'rinoceronte']
for animal in lista_animales:
  print ("El animal es:", animal, "la cantidad de letras:", len(animal))
```

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

\`\`\`python

\`\`\`

