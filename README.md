# Django-basic-start-project
Basic setting start project Django 
### สร้าง virtualenv
```python
virtualenv venv
```
```python
venv\Scripts\activate
```
### install django
```python
pip install django
```
### สร้าง projact
```python
django-admin startproject Myproject .
```
### สร้าง app 
```python
python manage.py startapp MyWebsite
```
### settings.py 
```python
INSTALLED_APPS = [
	'MyWebsite'
]
TIME_ZONE = 'Asia/Bangkok'
SESSION_ENGINE = 'django.contrib.sessions.backends.signed_cookies'

SESSION_EXPIRE_AT_BROWSER_CLOSE = True

STATIC_URL = '/static/'

STATICFILES_DIRS = [Path.joinpath(BASE_DIR, 'MyWebsite/static')]
STATIC_ROOT = Path.joinpath(BASE_DIR, 'staticfiles')

MEDIA_URL = '/media/'
MEDIA_ROOT = Path.joinpath(BASE_DIR, 'MyWebsite/static/media')
```
### urls.py 
```python
from django.urls import include
from django.conf import settings
from django.conf.urls.static import static

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('MyWebsite.urls')),
]

urlpatterns += static(settings.MEDIA_URL, document_root=settings.MEDIA_ROOT)
```
### urls.py ใน app
```python
from django.urls import path
from . import views

urlpatterns = [
    path('', views.index, name='index'),
]
```
### folder
`static`

`templates`
### views.py
```python
from django.shortcuts import render
def index(request):
    return render(request, 'index.html')
```
### คำสั่งอื่นๆ
`python manage.py makemigrations`

`python manage.py migrate`

`python manage.py createsuperuser`
