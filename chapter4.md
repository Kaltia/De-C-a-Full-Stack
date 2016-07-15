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



## Semejanzas y similitudes con SQL 

## CRUD a bordo