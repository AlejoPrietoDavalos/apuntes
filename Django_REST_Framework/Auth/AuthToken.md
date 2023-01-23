# Autenticación vía token.
Dentro de `settings.py`, en `INSTALLED_APPS`, agregamos `'rest_framework.authtoken'`.
~~~python
INSTALLED_APPS = [
    ...
    'rest_framework.authtoken',
]
~~~

Luego tenemos que hacer las migraciones.
~~~bash
python3 manage.py makemigrations
python3 manage.py migrate
~~~



