# Request
Yo interpreto, que cuando entra la request a la vista, y la serializamos.
Lo que hace el serializador, es:
1) Valida que la información que entra tenga la estructura pedida por la DB, es decir, (si es CharField, que entre texto, si es boolfield, booleanos, etc..)
2) Si hay campos extra que llegaron en la request y no están contemplados por el Serializador. Los descarta.
~~~python
request_serializado = mySerializador(data = request.data, context = {'request': request})
~~~



ver como hacer un decorador, para no meter esto en cada vista.

#print(check_password("asdasd123", "hash"))

from django.contrib.auth.hashers import check_password