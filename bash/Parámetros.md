Se puede pedir parámetros por consola al usuario usando el comando `read`.
~~~bash
read variable
echo $variable
~~~

-   `$0` representa el nombre del script
-   `$1` – `$9` los primeros nueve argumentos que se pasan a un script en Bash
-   `$#` el número de argumentos que se pasan a un script
-   `$@` todos los argumentos que se han pasado al script
-   `$?` la salida del último proceso que se ha ejecutado
-   `$$` el ID del proceso del script
-   `$USER` el nombre del usuario que ha ejecutado el script
-   `$HOSTNAME` se refiere al _hostname_ de la máquina en la que se está ejecutando el script
-   `$SECONDS` se refiere al tiempo transcurrido desde que se inició el script, contabilizado en segundos.
-   `$RANDOM` devuelve un número aleatorio cada vez que se _lee_ esta variable.
-   `$LINENO` indica el número de líneas que tiene nuestro script.
