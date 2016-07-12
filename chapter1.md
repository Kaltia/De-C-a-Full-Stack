
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

El mismo ejemplo anterior ahora representado en el lenguaje de programación de Python, donde se declara la función con la palabra def, el nombre de la función y retorna el valor resultante de la operación, si no hay un valor de retorno se regresará none.

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

- [ ] El paso es por valor, pero se pasa la dirección del objecto no como tal los valores, solo falta aclarar un poco este concepto. Te puedes basar en el siguiente [link](http://stackoverflow.com/questions/986006/how-do-i-pass-a-variable-by-reference)
En C los argumentos de una funcion se pasan por valor, pero también está el paso por referencia utilizando punteros.
En Python cuando se pasa un argumento a una función es por valor, sin embargo el parámetro que se pasa es la dirección del objeto.

## Tipos de colecciones de datos

### Listas 

Es un tipo de colección ordenada, y seria igual a lo que en otros lenguajes,como C, conocemos como arrays.
En las listas podemos ordenar cualquier tipo de dato: números, cadenas, booleanos, incluso listas, entre otros.
### Tuplas

En las tuplas, los valores creados al inicio ya no se pueden modificar después y su tamaño es fijo. Una ventaja de las tuplas es que son más ligeras que las listas.

### Diccionarios

Los diccionarios son colecciones que relacionan una clave y un valor.

 - [ ] Definir que es un diccionario, el texto me dice que es una lista de elementos solo se necesita especificar un poco más sino puede confundirse con una lista.

En el lenguaje de programación C, se utiliza un arreglo o estructuras para declarar una lista de elementos en una variable, sin embargo en python a esa estructura se le llama diccionario.

En C:

```c

```

- [ ] Podemos agregar una pequeña descripción de por que en python es distinto que en C, es decir por que no tengo que usar indices. - [ ] El punto anterior nos puede llevar a que es un iterador, recomiendo explicar brevemente con un ejemplo [con gatitos quedaria bien](http://nvie.com/img/iterable-vs-iterator.png)

En Python:
```python
lista_animales = ['gato', 'elefante', 'rinoceronte']
for animal in lista_animales:
  print ("El animal es:", animal, "la cantidad de letras:", len(animal))
```


- [ ] Como funcionan los argumentos variables, esto argumentos funcionan como una lista.

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



