# Inicializando con una aplicación de Django

Antes de inicializar con cualquier cosa, debemos empezar con fundamentos
bases para la hora de crear un proyecto en Django, no podemos solamente lanzar
comandos en la consola sin entender que hace cada uno de ellos, con este objetivo
en mente, notros describiremos como inicializar un proyecto de Django desde el inicio.

## Inicializando el entorno de trabajo

Vamos a inicializar nuestro entorno de trabajo con Django. Para ello,
ncesitamos crear nuestro entorno virtual, procederemos escribir en la terminal:

```bash
python -m venv env
```

Necesitamos siempre que empecemos con el proyecto activar el entorno virtual,
procederemos a escribir en la terminal:

```bash
.\env\Scripts\activate
```

Una vez activado el entorno virtual, procederemos a instalar Django, para ello
usaremos django en su version 5.2, procederemos a escribir en la terminal:

```bash
pip install "django>=5.2"
```

## Inicializando el proyecto

Vamos a inicializar nuestro proyecto Django, usaremos el nombre `primer_proyecto`

```bash
django-admin startproject primer_proyecto .
```

Aquí le decimos a Django que inicialice el proyecto, y que lo guarde en la carpeta
con el nombre de `primer_proyecto`, además el `.` indica que el directorio
actual es el directorio de destino.

## Carpetas del proyecto

Una vez inicializado el proyecto, vamos a ver que se nos han creado
una serie de carpetas, las cuales iremos explicando puntualmente para que sirve
cada una de ellas.

```text
capitulo1/
├── primer_proyecto/         ← Carpeta interna del proyecto
│   ├── __init__.py
│   ├── asgi.py
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
├── manage.py
```

### `manage.py`

Es una utilidad para interactuar con tu proyecto desde la línea de comandos.
Por ejemplo podemos realizar los siguientes comandos en la terminal:

```bash
python manage.py runserver
python manage.py makemigrations
python manage.py migrate
```

### `__init__.py`

Indica que esta carpeta es un módulo Python, por ahora no vamos a utilizarlo.

### `asgi.py`

Igual que `wsgi.py`, pero para servidores `ASGI` (ej. para websockets con Django Channels).

### `settings.py`

Configuración global del proyecto. Aquí defines:

- Apps instaladas

- Configuración de base de datos

- Rutas estáticas/media

- Middleware

- Templates

- Idioma y zona horaria

### `urls.py`

Enrutador principal del proyecto.

Aquí defines a qué app o vista enviar cada URL.

### `wsgi.py`

Configuración para desplegar tu proyecto en servidores WSGI (como Gunicorn o Apache).

## Ejecutando el servidor de desarrollo

Para ejecutar el servidor de desarrollo, usaremos el comando `runserver`
en la terminal:

```bash
python manage.py runserver
```

Esto nos creara un archivo `db.sqlite3` que será nuestra base de datos.
Además si queremos consultar el servidor abrimos la URL `http://127.0.0.1:8000/`
en el navegador.
