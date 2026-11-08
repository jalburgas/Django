


<div align="center">

# 🚀 Mi Blog con Django

### Un blog completo, funcional y con estilo — desde cero

<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&size=22&duration=3000&pause=1000&color=0C7BDC&center=true&vCenter=true&width=600&lines=Aprende+Django+paso+a+paso;Blog+con+panel+de+admin;Dise%C3%B1o+responsive+con+Bootstrap" alt="Typing SVG" />

<br/>

![Python](https://img.shields.io/badge/Python-3.12+-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Django](https://img.shields.io/badge/Django-5.x-092E20?style=for-the-badge&logo=django&logoColor=white)
![Bootstrap](https://img.shields.io/badge/Bootstrap-5.3-7952B3?style=for-the-badge&logo=bootstrap&logoColor=white)
![SQLite](https://img.shields.io/badge/SQLite-003B57?style=for-the-badge&logo=sqlite&logoColor=white)

<br/>

![Estado](https://img.shields.io/badge/Estado-Completado-2ecc71?style=flat-square)
![Licencia](https://img.shields.io/badge/Licencia-MIT-blue?style=flat-square)
![Nivel](https://img.shields.io/badge/Nivel-Principiante-orange?style=flat-square)

</div>

---

<div align="center">

## 📖 Índice

| 🧩 | Sección | 🧩 | Sección |
|:--:|:--|:--:|:--|
| 1️⃣ | [Requisitos](#-requisitos-previos) | 9️⃣ | [Admin](#️-paso-9-registrar-el-modelo-en-el-admin) |
| 2️⃣ | [Entorno virtual](#-paso-2-crear-la-carpeta-del-proyecto-y-el-entorno-virtual) | 🔟 | [Vistas](#-paso-10-crear-las-vistas) |
| 3️⃣ | [Instalar Django](#-paso-3-instalar-django) | 1️⃣1️⃣ | [Rutas](#-paso-11-crear-las-rutas-urls) |
| 4️⃣ | [Crear proyecto](#-paso-4-crear-el-proyecto-django) | 1️⃣2️⃣ | [Plantillas](#️-paso-12-crear-las-plantillas-html) |
| 5️⃣ | [Crear app](#-paso-5-crear-la-aplicación-blog) | 1️⃣3️⃣ | [Servidor](#-paso-13-arrancar-el-servidor-y-probar) |
| 6️⃣ | [Modelo](#-paso-6-definir-el-modelo-la-tabla-de-artículos) | 1️⃣4️⃣ | [Publicar](#️-paso-14-publicar-tu-primer-artículo) |
| 7️⃣ | [Migraciones](#️-paso-7-aplicar-las-migraciones) | 1️⃣5️⃣ | [Español](#-paso-15-opcional-poner-todo-en-español) |
| 8️⃣ | [Superusuario](#-paso-8-crear-el-superusuario) | 🧯 | [Errores](#-solución-de-errores-comunes) |

</div>

---

## ✅ Requisitos previos

<table>
<tr>
<td width="50%">

**🖥️ Sistema**
Windows 10 u 11

</td>
<td width="50%">

**🌐 Internet**
Para instalar Django y cargar Bootstrap

</td>
</tr>
<tr>
<td width="50%">

**⌨️ Terminal**
PowerShell o CMD

</td>
<td width="50%">

**🐍 Python**
3.10 o superior

</td>
</tr>
</table>

---

## 🐍 Paso 1: Instalar Python

> Descarga Python desde [python.org/downloads](https://www.python.org/downloads/)

1. Ejecuta el instalador.
2. ⚠️ **Marca la casilla “Add python.exe to PATH”** antes de hacer clic en *Install Now*.
3. Abre una terminal nueva y verifica:

```powershell
python --version
```

> 💡 Debe mostrar un número de versión (ej. `Python 3.15.x`). Si dice “no se reconoce”, reinstala marcando la casilla del PATH.

---

## 📁 Paso 2: Crear la carpeta del proyecto y el entorno virtual

```powershell
cd C:\pythonproyectos
mkdir blogdjango
cd blogdjango
python -m venv venv
venv\Scripts\activate
```

Sabrás que el entorno está activo porque verás `(venv)` al inicio de la línea:

```
(venv) C:\pythonproyectos\blogdjango>
```

> ⚠️ **Importante:** cada vez que abras una terminal nueva, deberás ejecutar `venv\Scripts\activate` de nuevo.

---

## 📦 Paso 3: Instalar Django

```powershell
python -m pip install django
django-admin --version
```

> 💡 Si `django-admin --version` falla, el entorno virtual no está activo o la instalación no terminó.

---

## 🏗️ Paso 4: Crear el proyecto Django

```powershell
django-admin startproject miblog
cd miblog
```

<details>
<summary>📂 Ver estructura generada</summary>

```
miblog/
├── manage.py
└── miblog/
    ├── __init__.py
    ├── settings.py
    ├── urls.py
    ├── asgi.py
    └── wsgi.py
```

</details>

> ⚠️ **Todos los comandos siguientes se ejecutan desde la carpeta `miblog` (donde está `manage.py`).**

---

## 🧩 Paso 5: Crear la aplicación `blog`

```powershell
python manage.py startapp blog
```

Abre `miblog\settings.py` y agrega `'blog'` a `INSTALLED_APPS`:

```python
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'blog',   # 👈 agregar esta línea
]
```

---

## 🗄️ Paso 6: Definir el modelo (la tabla de artículos)

Abre `blog\models.py` y reemplaza su contenido por:

```python
from django.db import models


class Articulo(models.Model):
    titulo = models.CharField(max_length=200)
    contenido = models.TextField()
    creado = models.DateTimeField(auto_now_add=True)

    def __str__(self):
        return self.titulo
```

---

## ⚙️ Paso 7: Aplicar las migraciones

```powershell
python manage.py makemigrations
python manage.py migrate
```

| Comando | Qué hace |
|:--|:--|
| `makemigrations` | Crea el archivo de migración con las instrucciones |
| `migrate` | Aplica esas instrucciones a la base de datos SQLite |

---

## 👤 Paso 8: Crear el superusuario

```powershell
python manage.py createsuperuser
```

<table>
<tr>
<th>Campo</th>
<th>Nota</th>
</tr>
<tr>
<td><b>Username</b></td>
<td>Tu nombre de usuario (ej. <code>juan</code>)</td>
</tr>
<tr>
<td><b>Email</b></td>
<td>Puedes dejarlo vacío con <i>Enter</i></td>
</tr>
<tr>
<td><b>Password</b></td>
<td>Escríbela dos veces (no se muestra en pantalla)</td>
</tr>
</table>

> 💡 Guarda estas credenciales, las usarás en el Paso 14.

---

## 🛠️ Paso 9: Registrar el modelo en el admin

Abre `blog\admin.py` y reemplaza su contenido por:

```python
from django.contrib import admin
from .models import Articulo

admin.site.register(Articulo)
```

---

## 🎨 Paso 10: Crear las vistas

Abre `blog\views.py` y reemplaza su contenido por:

```python
from django.shortcuts import render
from .models import Articulo


def inicio(request):
    return render(request, 'blog/inicio.html')


def lista_articulos(request):
    articulos = Articulo.objects.all().order_by('-creado')
    return render(request, 'blog/lista.html', {'articulos': articulos})
```

<table>
<tr>
<th>Vista</th>
<th>Función</th>
</tr>
<tr>
<td><code>inicio</code></td>
<td>Muestra la página de bienvenida</td>
</tr>
<tr>
<td><code>lista_articulos</code></td>
<td>Obtiene todos los artículos y los envía a la plantilla</td>
</tr>
</table>

---

## 🔗 Paso 11: Crear las rutas (URLs)

### 11.1 Crear `blog\urls.py`

```python
from django.urls import path
from . import views

urlpatterns = [
    path('', views.lista_articulos, name='lista_articulos'),
]
```

### 11.2 Configurar `miblog\urls.py`

```python
from django.contrib import admin
from django.urls import path, include
from blog import views as blog_views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', blog_views.inicio, name='inicio'),
    path('blog/', include('blog.urls')),
]
```

> ⚠️ **Verifica la ruta del archivo:** debe ser `C:\pythonproyectos\blogdjango\miblog\miblog\urls.py`.

---

## 🖼️ Paso 12: Crear las plantillas HTML

### 12.1 Crear las carpetas

```powershell
mkdir blog\templates
mkdir blog\templates\blog
```

### 12.2 Crear `base.html`

📄 `blog\templates\blog\base.html`

```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>{% block titulo %}Mi Blog{% endblock %}</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet">
</head>
<body class="bg-light">

    <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
        <div class="container">
            <a class="navbar-brand" href="/">Mi Blog</a>
            <div class="navbar-nav">
                <a class="nav-link" href="/">Inicio</a>
                <a class="nav-link" href="/blog/">Artículos</a>
                <a class="nav-link" href="/admin/">Admin</a>
            </div>
        </div>
    </nav>

    <div class="container mt-4">
        {% block contenido %}{% endblock %}
    </div>

    <footer class="text-center text-muted py-4 mt-5">
        <small>© 2026 Mi Blog — Hecho con Django</small>
    </footer>

    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"></script>
</body>
</html>
```

### 12.3 Crear `inicio.html`

📄 `blog\templates\blog\inicio.html`

```html
{% extends 'blog/base.html' %}

{% block titulo %}Inicio — Mi Blog{% endblock %}

{% block contenido %}
<div class="p-5 mb-4 bg-white rounded-3 shadow-sm">
    <h1 class="display-5 fw-bold">¡Bienvenido a mi blog! 👋</h1>
    <p class="lead">Esta es mi primera página hecha con Django. Aquí iré publicando contenido.</p>
    <a class="btn btn-primary btn-lg" href="/blog/">Ver artículos</a>
</div>
{% endblock %}
```

### 12.4 Crear `lista.html`

📄 `blog\templates\blog\lista.html`

```html
{% extends 'blog/base.html' %}

{% block titulo %}Artículos — Mi Blog{% endblock %}

{% block contenido %}
<h1 class="mb-4">Artículos</h1>

{% for articulo in articulos %}
    <div class="card mb-3 shadow-sm">
        <div class="card-body">
            <h2 class="h4 card-title">{{ articulo.titulo }}</h2>
            <p class="text-muted small">Publicado el {{ articulo.creado|date:"d/m/Y H:i" }}</p>
            <p class="card-text">{{ articulo.contenido }}</p>
        </div>
    </div>
{% empty %}
    <div class="alert alert-info">
        Todavía no hay artículos. Crea uno desde el <a href="/admin/">panel de admin</a>.
    </div>
{% endfor %}
{% endblock %}
```

---

## 🚀 Paso 13: Arrancar el servidor y probar

```powershell
python manage.py runserver
```

<table>
<tr>
<th>URL</th>
<th>Qué verás</th>
</tr>
<tr>
<td><code>http://127.0.0.1:8000/</code></td>
<td>Página de inicio con mensaje de bienvenida</td>
</tr>
<tr>
<td><code>http://127.0.0.1:8000/blog/</code></td>
<td>Lista de artículos (vacía al principio)</td>
</tr>
<tr>
<td><code>http://127.0.0.1:8000/admin/</code></td>
<td>Panel de administración</td>
</tr>
</table>

> 💡 Para detener el servidor: `Ctrl + C`.

---

## ✍️ Paso 14: Publicar tu primer artículo

1. Ve a `http://127.0.0.1:8000/admin/`
2. Inicia sesión con el superusuario del Paso 8.
3. En la sección **“Articulos”** haz clic en **“Añadir”**.
4. Escribe un título y contenido, guarda.
5. Visita `http://127.0.0.1:8000/blog/` y verás tu artículo con estilo. 🎉

---

## 🌎 Paso 15 (opcional): Poner todo en español

En `miblog\settings.py` cambia:

```python
LANGUAGE_CODE = 'es'
TIME_ZONE = 'America/Caracas'
```

Reinicia el servidor para aplicar los cambios.

---

## 🧯 Solución de errores comunes

<details>
<summary><b>❌ can't open file 'manage.py'</b></summary>

**Causa:** estás en la carpeta equivocada.

**Solución:** `cd` hasta la carpeta que contiene `manage.py`.

</details>

<details>
<summary><b>❌ No module named django</b></summary>

**Causa:** entorno virtual inactivo o Django no instalado.

**Solución:** activa `venv\Scripts\activate` y ejecuta `python -m pip install django`.

</details>

<details>
<summary><b>❌ No module named 'blog'</b></summary>

**Causa:** app no registrada o carpeta mal ubicada.

**Solución:** verifica `'blog'` en `INSTALLED_APPS` y que `blog\` esté junto a `manage.py`.

</details>

<details>
<summary><b>❌ No module named 'blog.models'</b></summary>

**Causa:** falta `models.py` o está en otra ubicación.

**Solución:** crea `blog\models.py` con el contenido del Paso 6.

</details>

<details>
<summary><b>❌ TemplateDoesNotExist</b></summary>

**Causa:** ruta de plantilla incorrecta.

**Solución:** debe ser exactamente `blog\templates\blog\inicio.html`.

</details>

<details>
<summary><b>❌ Sigues viendo el cohete en /</b></summary>

**Causa:** ruta `''` ausente en `miblog\urls.py`.

**Solución:** revisa el Paso 11.2.

</details>

<details>
<summary><b>❌ That port is already in use</b></summary>

**Causa:** puerto 8000 ocupado.

**Solución:** `python manage.py runserver 8001` y abre `http://127.0.0.1:8001/`.

</details>

---

## ⚡ Resumen de comandos

```powershell
# Crear entorno e instalar
cd C:\pythonproyectos\blogdjango
python -m venv venv
venv\Scripts\activate
python -m pip install django

# Crear proyecto y app
django-admin startproject miblog
cd miblog
python manage.py startapp blog

# Base de datos
python manage.py makemigrations
python manage.py migrate
python manage.py createsuperuser

# Arrancar
python manage.py runserver
```

---

## 🎯 Resultado final

```text
miblog/
├── manage.py
├── blog/
│   ├── templates/blog/
│   │   ├── base.html
│   │   ├── inicio.html
│   │   └── lista.html
│   ├── admin.py
│   ├── models.py
│   ├── urls.py
│   └── views.py
└── miblog/
    ├── settings.py
    └── urls.py
```

> ✅ Tienes un blog funcional: publicas desde el admin y los artículos se muestran con diseño limpio.

---

<div align="center">

## 🏷️ Etiquetas

![Django](https://img.shields.io/badge/-django-092E20?style=flat-square)
![Python](https://img.shields.io/badge/-python-3776AB?style=flat-square)
![Blog](https://img.shields.io/badge/-blog-FF6B6B?style=flat-square)
![Bootstrap](https://img.shields.io/badge/-bootstrap-7952B3?style=flat-square)
![Tutorial](https://img.shields.io/badge/-tutorial-F7B731?style=flat-square)
![Principiantes](https://img.shields.io/badge/-principiantes-20BF6B?style=flat-square)

<br/>

### ⭐ Si te sirvió, dale una estrella al repo

<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&size=18&duration=4000&pause=1000&color=0C7BDC&center=true&vCenter=true&width=500&lines=Hecho+con+%E2%9D%A4%EF%B8%8F+y+Django;%C2%A1Feliz+coding!" alt="Footer" />

</div>
```

---


