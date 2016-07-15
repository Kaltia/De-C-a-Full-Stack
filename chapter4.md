# MongoDB, El otro enfoque

Mongo es una base de datos dististinta a las bases de datos tradicionales y esto implica pensar distinto al momento de guardar la información o tal vez no tanto.

Para esto vallamos por partes, es posible que esi estas familizarizado con bases de datos tradicionales te pueda costar un poco adaptarte pero hey el mundo no se hizo en un día. Ahora que si no tienes experiencia es mas probable que te acomodes más rapido a el modelo propuesto.

Es importante que no te cases con un modelo pues es importante tener distintas opciones y disernir cual de estos conviene a tus propositos, alcances y costos.

## Instalación

La instalación es muy sencilla realmente, todo lo que debemos de hacer es acceder a la pagian de [descargas de MongoDB](https://www.mongodb.com/download-center#community) y seleccionar el paquete para el sistema operativo que estemos usando. El manejador de paquete de tu distribución podra hacerse cargo del resto.

Para verificar si todo salio correctamante ejecutando una consola de mongo, la cual deberia mostrarse similar a esta:

```
mongoMongoDB shell version: 2.4.9
connecting to: test
Server has startup warnings: 
>
```

MongoDB requiere una carpeta llamada `data` en la raiz del sisema de archivos, es probable que no se conecte a la base de datos tengas que crear manualmente este directorio.

Despues de esto en algunos casos como el de algunas 
distribuciones linux tendremos que levantar el demonio con el manejador de procesos de la distribución.

```
systemctl start mongod
```

## DBs, Documentos, Collecciones y algo más

Deberiamos empezar con un las bases del algebrea relacional, tocas los diagras y finalizar con un twist de SQL si esto fuea una clase de base de datos comun, pero esto no es una clase ni tampoco hablamos de algo que comunmente se enseñe en las aulas.

Tomando empezemos por definir que en MongoDB necesitamos tres contenedores de datos, los cuales entran en una categoria muy simple:

```
Base De Datos
  |-- Collección
    |-- Documento
      |-- Campos
```

Esta es la jerarquia de contenedores de datos, comenzamos por una base de datos, detro de la cual se encuentran colleciones de datos, las cuales estan compuestas por documentos y como ya sabemos la historia estas se encuentran conformados por campos.

Un campo no es más que la asociación de una clave con un valor:

```
nombre: "Pastel de Queso con Zarzamora"
```

Ahora los documentos son un conjunto de campos y los cuales se representan como un objecto de javascript o muy similar a los hash en Python:

```
{
  nombre: "Pastel de Queso con Zarzamora",
  costo: 240.50,
  medida: "grande"
}
```

Como te habras dado cuenta los documentos son basicamente objectos de javascript, pero que esto no te confunda pues estas usado una consola de JS para acceder a los datos, De hecho podemos considerar a los documetos como un superconjuto de los objetos de JS por que agrega más tipos de datos soportado como BinaryData, Code, Simbolos, Regex, entre otros. Los datos no se alacenan como json si no utilizan un formato para serializar los datos llamado BSO, el cual no es más que un formato binari para reprentar objetos o documentos, pero adentrarse más en el tema esta fuera del alcance de esta guia.


Continuando con nuestros conceptos base, las colecciones son un conjunto de documentos:

```
> db.creators.find()
{ first: "Yukihiro", aka: "Matz", last: "Matsumoto" } 
{ last: "van rossum", first: "Guido" }
```

La función `find()` nos ayuda a obtener y hacer consultas a los documentos de la colleción, por defecto nos trae los 20 primeros elementos de la collección llamada `creators`.

Ya que vimos que solo el agrupación de agrupaciónes el siguiente concepto no es distinto, la base de datos es un conjunto de collecciones:

```
> db.getCollectionNames()
[ "creators", "employees", "system.indexes" ]
```

Ahora te preguntaras que significa db, pues bien no es más que una referencia a la base de datos que esta en uso actualmente y la cual se selecciona con el comando `use`.

```
> show dbs
local 0.00006866455078125GB
locations 0.00006103515625GB
practica 0.00006866455078125GB
test 0.0001373291015625GB
> use test
switched to db test
> db
test
```

Al final o al inicio podemos tener varias bases de datos en una instancia de MongoDB, piensalo como ogros o cebollas son capas que cubren otras capas.

## CRUD a bordo


Hasta este moment ya conocemos la estructura de como se almacena la información pero que hay de crear nuevos elementos, buscarlos, actualizarlo y eliminarlos.
Esto es lo que significa CRUD (Creat, Read, Update, Delete) pero en mongo cambiaron un poco los nombre pero agrandes razgos funcionan de la misma forma.

```
Create -> Insert
Read -> Find
Update -> Update
Delete -> Remove
```

Para crear un nuevo elemento usamos la forma `db.collection.acción`, para este caso es insert:

```
db.alumnos.insert({nombre: "Jesus", apellido: "Ramirez" })
```

Para buscar un elemento es de la misma forma solo que el documento indica que elementos seran buscado y cual sera su predicado:

```
db.alumnos.find({'nombre': { $in: ["Nanaka", "Jesus"] } })
```

En este caso queremos encontrar aquellos elementos cuyo campo nombre tenga el valor de "Jesus" o "Nanaka". Para ello es que se usa el operador [$in](https://docs.mongodb.com/manual/reference/operator/query/in/), además de este existen muchos mas operadores en la documentación pero de momento no los necesitamos.

Actualizar un elemento es similar solo que esta vez el primer elemento es usada para obtener el documento a actualizar y el segundo indica las reglas y valores para actualizar.

```
db.alumnos.update(
  {'nombre': { $in: ["Jesus", "Xavi"] } }, 
  { $set: { sexo: "masculino" } }
)
```

Esto solo actualizara al primer elemento que conincida con la query (el primer documento pasado como argumento), en caso de querer actualizar todos lo campos se debe de agregar un tercer documento con el campo `{multi: true}`.

```
db.alumnos.update(
  { 'nombre': { $in: ["Jesus", "Xavi"] } },
  { $set: { sexo: "masculino" } },
  { multi: true}
)
```

El operador `$set` unicamente actualiza o crea los campo especificado, no sobreescribe el documento, para lograr esto solo remueve el comando `set` del segundo objecto pasado como parametro.

Como ultima operación que forma parte del CRUD, `remove` necesita un parametro que sirva para consultar los elmentos que se vana  eliminar y en caso de querer eliminar todo los documentos que cumplan dicho criterio deberemos pasarle otro documento con el campo `multi` con valor `true`.

```
db.alumnos.remove(
 { 'nombre': "Jesus" },
 { multi: true}
)
```

Esto eliminara a todos los documentos que tengan `"Jesus"` en su campo `nombre`.
