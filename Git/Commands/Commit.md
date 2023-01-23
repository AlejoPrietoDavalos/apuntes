---
Elimina el **último** commit, con el código tal cual estaba antes del commit.
~~~bash
git reset --soft HEAD~1
~~~
Si queremos eliminar el commit, y todo lo hecho hasta el commit anterior, cambiar `--soft` por `--hard`.


