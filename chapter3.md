# Flask

Flask es un micro framework para python que te permite desarollar aplicaciones web.

Algunas de las tantas ventajas que Flask provee son:
  - Servidor web de desarrollo y debug
  - Soporte integrado para unit testing
  - Tratatamiento de peticiones RESTful
  - Compatibilidad para multiples sistemas de template
  - Documentación extensiva


## Instalación

Podemos instalr flask de distintas formas pero sin duda una de las más faciles es ejecutar desde una consola el siguiente comando:

```console
$ pip install Flask
```

Aunque siempre es preferible llevar un control de las dependencias que necesita nuestros programas, por ello te recomendamos poner las dependencias de tu aplicación en un archivo con nombre `requirements.txt` el cual contendrá los nombres y la versión de estas dependencias:

```
# requirement.txt
Flask
```

Por cierto el simbolo de gato o numeral le indica al instalar que ignore la linea marcada.
Ahora para instalar todas las dependencias escritas en el programa lo haremos ejecutando:

```console
$ pip install -r requirements.txt
```

Este archivo lo podrás agregar a tu manejador de versiones y asi mantener actualizaciones de las dependencias respecto a los desarollos futuros.


## ¡Mi primer servicio web!


Ahora nos toca escribir nuestro primer servicio web, coloca el siguiente codigo en un archivo con nombre `main.py`.

```python
from flask import Flask
app = Flask(__name__)

@app.route("/")
def hello():
    return "¡Hola Mundo!"

if __name__ == "__main__":
    app.run()
```

Las primeras dos lineas importan y crean una aplicación donde agregaremos nuestras funciones y que sean accesibles a internet.

Con la linea `@app.route("/")` le decimos a nuestra aplicación que cuando acceda a nuestro sitio y no proporcionen ninguna otra ruta (http://misitio.com o http://misitio.com/ ) más que el dominio o la dirección IP se ejecutará la función `hello`.

La funcion `Hello` se encarga de devolver el una cadena que se mostrara en nuestro navegador.

Por ultimo con la condicional valida que nuestro archivo es llamado directamente desde la linea de comandos, si se cumple esta condición se crea nuestro servidor web que correrá por siempre.

Ahora te preguntaras como haces que corra por siempre, pues bueno eso es ejecutando desde la linea de comandos:

```console
$ python main.py
```


# Agregando Html a mi servicio web


Si quieres que tu pagina se vea con contenido más enriquecido en vez de simple texto puedes usar el sistema de templates o plantillas.

Crea una carpeta con nombre `templates` donde colocaremos todas las plantillas que podremos mostrar a nuestros usuarios.
Agrega a un nuevo archivo `index.html` el contenido que quieres mostrar, en este caso pondremos un tipico hola mundo.

```html
<!doctype html>
<html>
<head>
<meta charset="utf-8">
<title>Hola mundo - Index</title>
<link href="bootstrap-3.1.1-dist/css/bootstrap.css" rel="stylesheet">
</head>
 
<body>
 <div class="row">
  <div class="col-md-6 col-md-offset-3">
    <div class="jumbotron">
    {% if nombre %}
      <h1>¡Hola {{ nombre }}!</h1>
    {% else %}
      <h1>¡Hola Mundo!</h1>
    {% endif %}
      <p class="lead">Primeros pasos con Flask</p>
      <p><a class="btn btn-primary btn-lg" role="button">Salud!</a></p>
    </div>
  </div>
 </div>
</body>
</html>
```

Como podras notar hay una condicional que verifica si `nombre` es verdadero para hacer un saludo personalizado. Esto es lo que permite un sistema de templates. Agregar, modificar datos basados en ciertas condiciones asi podemos generar contenido dinamico basado en las peticiones que hacen a nuestro servicio web.

Debes de mantener en claro dos conceptos:

1. Las etiquetas del tipo ``{{ variable }}`` producen una cadena con el valor de la variable, digamos que es como un printf pero usando corchetes.

2. El segundo tipo de etiquetas sirven para agregar control y no producen ningun valor. Ademas de if, tambien existe for, filter, call, macro, etc. Toda etiqueta de la forma `{% if variable %}` se cierra con otra etiqueta anteponiento end `{% endif %}`.

Ahora modifiquemos nuestro código de python en el archivo `main.py` para que mostremos esta pagina a nuestros usuarios, el código deberá lucir de la siguiente forma:

```python
from flask import Flask, render_template
app = Flask(__name__)

@app.route("/")
@app.route("/saluda/<name>")
def hello(nombre = None):
    return render_template("index.html", nombre = nombre)

if __name__ == "__main__":
    app.run()
```


Deberás terminar el servidor que levantaste anteriormente con `Ctrl + c` y volverlo a ejecutar para que los cambios se vean reflejados en la próxima petición al servició.

# Mi aplicación para el mundo

El siguiente paso es publicar la aplicación para esto usaremos Heroku.
Primero debemos de agregar una dependencia llamada `gunicorn` que nos permitirá manejar las peticiones de forma más optima que el servidor que trae Flask. Recuerda agregarlo en el archivo `requirements.txt` y despues ejecutar el comando para instalarlo.

```
Flask
gunicorn
```

Tambien crea un nuevo archivo `Procfile`:

```
web: gunicorn main:app --log-file -
```

Con esto le decimos a heroku que corra nuestra aplicación en un Dyno ejecutando el servidor gunicorn el cual recivira las peticiones web que le pasara a nuestra aplicación para que las procese.


Crea un nuevo projecto en heroku para esto primero te deberas de autenticar con `heroku login`:

```
$ heroku create nombre-del-proyecto
```

Puedes validar si el sitio se mostrara correctamente usando 

```
heroku local
```

Confirma los cambios que hemos hecho y sube los cambios a heroku como si se tratase de cualquier otro repositorio git.

```
git push heroku master
```


## Agregando la base de datos

Agregar dependencias.

```
Flask
gunicorn
mongoengine
flask_mongoengine
```


```python
from flask import Flask, render_template, request, jsonify, Response

app = Flask(__name__)

app.config["MONGODB_SETTINGS"] = {
        'db': 'locations',
        'host': os.getenv('MONGODB_URI', 'localhost')
    }
    
db = MongoEngine(app)
    
class Locations(db.Document):
    content = db.StringField(required=True)


@app.route('/new', methods=['POST'])
def register_location():
    try:
        data = geojson.loads(request.get_data())
        loc = Location(content=geojson.dumps(data))
        loc.save()
    except e:
        return jsonify({'result': 'Error', 'error': str(e)})


    return jsonify({'result': 'Ok', 'id': str(loc.id)})


@app.route('/<loc_id>')
def get_location(loc_id):
    element = Location.objects.get(id=loc_id)
    return jsonify(json.loads(element.content))
    
    
if __name__ == "__main__":
    app.run()
```


## MVC

## Cola de tareas

### Tips

- Agregando un proyecto de heroku al repositorio local

  ```
  $ heroku git:remote -a project
  ```