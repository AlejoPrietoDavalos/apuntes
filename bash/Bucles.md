### For
~~~bash
for VARIABLE in LISTA; do
    COMANDOS
done
~~~
##### Ejemplo:
~~~bash
for i in 1 2 3 4 5; do
    echo $i
done
~~~


### While
~~~bash
while [CONDICIÓN]; do
    COMANDOS
done
~~~
##### Ejemplo:
~~~bash
count=0
while [ $count -lt 5 ]; do
    echo $count
    count=$((count+1))
done

~~~