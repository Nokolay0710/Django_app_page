1. [Django quick start](https://github.com/Nokolay0710/Django-quick-start)

2. ```python
   py manage.py startapp newapp
   ```
4. config -> settings.py ->
   ```python
    INSTALLED_APPS = [
        'django.contrib.admin',
        'django.contrib.auth',
        'django.contrib.contenttypes',
        'django.contrib.sessions',
        'django.contrib.messages',
        'django.contrib.staticfiles',

        # Apps
        'newapp', # new
    ]
    ```

5. config -> urls.py ->
   ```python
    from django.urls import include # new

    urlpatterns = [
        path('admin/', admin.site.urls),
        path('', include('newapp.urls')), # new
    ]
    ```

7. create file urls.py to dir newapp
   ```python
    from . import views
    from django.urls import re_path

    urlpatterns = [
        re_path(r'^$', views.index, name='index'),
    ]
    ```

9. newapp -> views.py ->
    ```python
    from django.shortcuts import render

    def index(request):
        return render(request, 'index.html')
    ```

11. create dir templates to dir newapp

12. create file index.html to dir templates
    ```html
    <!-- templates/index.html -->
    {% include static %}
    <!DOCTYPE html>
    <html lang="en">
    <head>
    <meta charset="utf-8">
    {% block styles %}
    {% endblock %}
    <title>{% block title %}Django index.html{% endblock %}</title>
    </head>
    <body>
    <main>
        <h2>Hello index page!</h2>
    </main>
    </body>
    </html>
    ```

13. ```python
    py manage.py runserver
    ```
14. Starting development server at http://127.0.0.1:8000/

15. Hello index page!
