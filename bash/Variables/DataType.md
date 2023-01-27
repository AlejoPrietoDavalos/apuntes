# Arrays
### Declaración
~~~bash
declare -a array=(
    "elem_1"
    "elem_2"
    # etc...
)
~~~

### Asignación
~~~bash
array[i]="Nuevo Valor"
~~~

### Utilidades
~~~bash
${array[@]}            # Accede a todos los elementos de la lista.
length=${#array[@]}    # Cantidad de elementos.
~~~

# Array Asociativo
~~~bash
declare -A array=(
    ["key_1"]="valor_1"
    ["key_2"]="valor_2"
    # etc...
)
~~~

### Asignación
~~~bash
array["key"]="Nuevo Valor"
~~~

### Utilidades
~~~bash
${!array[@]}    # Obtengo todas las claves del array asociativo
~~~