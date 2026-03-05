# 💥 Level 5 💥

## Meta de nivel
La contraseña para el siguiente nivel se almacena en un archivo en algún lugar debajo del directorio inhere y tiene todas las siguientes propiedades:

legible para humanos
1033 bytes de tamaño
no ejecutable
Comandos que puedes necesitar para resolver este nivel:
**ls** , **cd** , **cat** , **file** , **du** , **find**

## Solucion

Para encontrar la bandera, haremos uso del comando find que significa buscar, tiene distintos parametros para buscar por tipo, dueño, peso, nombre, etc.

primero verificamos que existe la carpeta y accedemos:

```bash
bandit5@bandit:~$ ls
inhere
bandit5@bandit:~$ cd inhere/
```

ahora listamos su contenido:

```bash
bandit5@bandit:~/inhere$ ls
maybehere00  maybehere04  maybehere08  maybehere12  maybehere16
maybehere01  maybehere05  maybehere09  maybehere13  maybehere17
maybehere02  maybehere06  maybehere10  maybehere14  maybehere18
maybehere03  maybehere07  maybehere11  maybehere15  maybehere19
```

como podemos ver, hay muchos archivos asi que ver uno a uno no es una opcion, usamos el comando find:

```bash
bandit5@bandit:~/inhere$ find -size 1033c
./maybehere07/.file2
```

use el parametro -size para buscar por tamaño y encontre un archivo, como solo es uno tuve suerte, significa que es el unico archivo con esas caracteristicas:

```bash
bandit5@bandit:~/inhere$ cat ./maybehere07/.file2 
Bandera: Descrubela tu!
bandit5@bandit:~/inhere$ 
```




