# Django
 # Django

## Installation

### Install Python
Ensure Python is installed on your system.

### Install Django
```bash
pip install django    
Creating a Project
Option 1: Standard project creation
bash

django-admin startproject mi_sitio

Option 2: Create project in current directory
bash

python -m django startproject mi_sitio .

Apply initial migrations
bash

python manage.py migrate

Creating a Super User
bash

python manage.py createsuperuser

Follow the prompts to set:

    Username

    Email address

    Password

Running the Development Server
bash

python manage.py runserver

The server will start at http://127.0.0.1:8000/
Optional: Specify different port
bash

python manage.py runserver 8080

Optional: Make server accessible on network
bash

python manage.py runserver 0.0.0.0:8000

Next Steps

    Visit http://127.0.0.1:8000/admin to access the admin panel

    Start creating your first app: python manage.py startapp mi_app

text

