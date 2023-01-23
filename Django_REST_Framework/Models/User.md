Modelo de usuario genérico que podemos usar como base para editar.

Hay que instalar pillow, para tener un campo `models.ImageField()`.
Si no vamos a usar ese campo, podemos omitirlo.
~~~bash
pip install pillow
~~~

~~~python
from django.db import models
from django.contrib.auth.models import BaseUserManager, AbstractBaseUser, PermissionsMixin
#-----(Opcional)-----> from simple_history.models import HistoricalRecords


class UserManager(BaseUserManager):
    def create_user(self, username, email, first_name, last_name, password=None, is_staff=False, is_superuser=False):
        user = self.model(
            username = username,
            email = email,
            first_name = first_name,
            last_name = last_name,
            is_staff = is_staff,
            is_superuser = is_superuser,
        )
        
        user.set_password(password)
        user.save(using = self.db)
        return user
    
    def create_superuser(self, username, email, first_name, last_name, password=None):
        return self.create_user(username, email, first_name, last_name, password, is_staff=True, is_superuser=True)


class User(AbstractBaseUser, PermissionsMixin):
    username = models.CharField(max_length = 30, unique = True)
    email = models.EmailField(max_length = 256, unique = True)
    first_name = models.CharField(max_length = 64, blank = True)
    last_name = models.CharField(max_length = 64, blank = True)
    #birth_day = models.DateField()
    #image = models.ImageField('Imagen de perfil', upload_to='perfil/', max_length = 255, null = True, blank = True)
    is_active = models.BooleanField(default = True)
    is_staff = models.BooleanField(default = False)
    is_superuser = models.BooleanField(default = False)
    historical = HistoricalRecords()
    objects = UserManager()
    
    
    USERNAME_FIELD = 'username'
    REQUIRED_FIELDS = ['email', 'first_name', 'last_name'] # Este campo solo afecta a la creación de superusuarios.
    
    class Meta:
        verbose_name = 'User'
        verbose_name_plural = 'Users'
~~~

Agregamos en `settings.py`, una constante que le dice a django, que la aplicación funcionará con "este" modelo usuario.
~~~python
AUTH_USER_MODEL = 'users.User'    # "users" es el nombre de la app de usuarios, y "User", el nombre del modelo.
~~~

Agregamos dentro de la app de `users`, en `admin.py`.
~~~python
from django.contrib import admin
from .models import User

admin.site.register(User)
~~~

---
### Opcional
`simple_history`  es una librería que reconoce cada cambio que hace cada usuario sobre del modelo de `User`.  
Se guarda en un campo llamado `historical`, se puede ver dentro del modelo `User`.
~~~bash
pip install django-simple-history
~~~
Luego en `settings.py`:  
Dentro de `INSTALLED_APPS`, agregamos `'simple_history'`.
~~~python
INSTALLED_APPS = [
	...
	'simple_history',
]
~~~
Dentro de `MIDDLEWARE`, agregamos `'simple_history.middleware.HistoryRequestMiddleware'`.
~~~python
MIDDLEWARE = [
	...
	'simple_history.middleware.HistoryRequestMiddleware',
]
~~~

