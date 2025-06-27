# Creación de una aplicación Django

Nosotros nos dirigiremos a construir un blog con Django, para ellos vamos a utilizar
exactamento lo que hicimos en el capítulo anterior, inicializaremos de la misma forma,
con el cambio del nombre de la aplicación, esta será `primera_app`.

## Creación de la aplicación

Debemos crear la aplicación en el directorio `primera_app`, usaremos en la linea de comandos:

```bash
python manage.py startapp blog
```

Esto nos creara las siguientes carpetas:

```text
blog/
├── __init__.py
├── admin.py
├── apps.py
├── migrations/
│   └── __init__.py
├── models.py
├── tests.py
└── views.py
```

Explicaremos enseguida todas las nuevas que no hayamos visto.

### `admin.py`

Aquí registras tus modelos para que aparezcan en el panel de administración de Django (`/admin`).

### `apps.py`

Contiene la clase de configuración de la app. Django lo usa internamente para identificar la app.
Puede personalizarse si necesitas configuraciones específicas.

### `migrations/`

Carpeta que guarda los archivos de migración, los cuales Django usa para crear o modificar la base de datos según tus modelos.

### `models.py`

Aquí defines las estructuras de datos (modelos) de tu app.
Cada clase representa una tabla en la base de datos.

### `views.py`

Aquí defines las funciones o clases que controlan la lógica de cada página.
Una vista toma una petición (request) y devuelve una respuesta (HttpResponse o render).

### `tests.py`

Archivo para escribir pruebas automatizadas que aseguren que tu código funciona como debe.

### `settings.py`

Una vez que creamos nuestra app, ocupamos decirle a Django que la usaremos en nuestra aplicación.
Para esto, debemos agregar la app a la lista de apps en `settings.py`:

```python
INSTALLED_APPS = [
    'primera_app',
]
```

## Creación de modelos

Ahora que ya tenemos nuestra app creada, vamos a crear nuestros modelos
para nuestro blog.

```python
#blog/models.py:
from django.db import models

class Post(models.Model):
    titulo = models.CharField(max_length=200)
    contenido = models.TextField()
    fecha_creacion = models.DateTimeField(auto_now_add=True)
    publicado = models.BooleanField(default=False)

    def __str__(self):
        return self.titulo
```

## Migraciones y base de datos

Para que Django pueda crear la base de datos, debemos ejecutar las migraciones.
en nuestra terminal:

```bash
python manage.py makemigrations blog
python manage.py migrate
```

## Registrar el modelo en el admin
