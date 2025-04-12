# Setup

What we do in desktop

```powershell
> mkdir django_rest_listable; cd django_rest_listable
> py -m venv venv
> .\venv\Scripts\activate
> py -m pip install --upgrade pip
> pip install django djangorestframework
```

Now we start to scaffold the project

```powershell
> django-admin startproject listable .
> py manage.py startapp core
> echo > README.md
> code .
```

Finish setting up Django

```powershell
> py manage.py migrate
> py manage.py createsuperuser
```

* admin/admin

# Version Control

* Initialize Git and get on GitHub (4/12 2:30 pm)
* use .gitignore from [Project Rocket](https://github.com/Roburlion/rocket).

* push to [django_rest_listable](https://github.com/Roburlion/django_rest_listable).

# Configure

* Added `rest_framework` and `listable` to `INSTALLED_APPS` in `settings.py` (2:34 pm)

# Endpoint

```python
# core\views.py
from rest_framework.decorators import api_view
from rest_framework.response import Response

@api_view(['GET'])
def hello_world(request):
    return Response({"message": "Hello, world!"})
```

```python
# core\urls.py
from django.urls import path
from .views import *

urlpatterns = [
    path('', hello_world, name='hello_world'),
]
```

```python
# listable\urls.py
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('api/', include('core.urls')),
]
```

# Test

```powershell
> py manage.py runserver
```

* Eureka!  It works! (3 pm)

# Next Steps

* What am I trying to do next?

### Options

- **Model Creation:** Define models in `listapp/models.py` to represent list items.
- **Serializers:** Create serializers in a new file (e.g., `listapp/serializers.py`) to convert model instances into JSON.
- **CRUD Endpoints:** Expand your API to support full CRUD operations using Django REST Framework’s generic views or viewsets.
- **Testing:** Write tests to ensure your API works as expected.
- **Deployment:** Look into deploying your Django app using platforms like Heroku, AWS, or Azure.









