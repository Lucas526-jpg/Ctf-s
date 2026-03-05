# 💥 Level 4 💥

## Meta de nivel
La contraseña para el siguiente nivel se almacena en el único archivo legible por humanos del directorio inhere . Consejo: si tu terminal falla, prueba el comando "reset".

Comandos que puedes necesitar para resolver este nivel:
**ls** , **cd** , **cat** , **file** , **du** , **find**

## Solucion

Como nos dice la meta de nivel, debemos acceder al directorio inhere y buscar el archivo que es "legible por humanos", en este caso, se refiere al tipo de archivo ASCII text, lo veremos en los siguientes comandos.

Primero verificamos que esta la carpeta y accemos a ella, listando su contenido:

```bash
bandit4@bandit:~$ ls
inhere
bandit4@bandit:~$ ls inhere/
-file00  -file02  -file04  -file06  -file08
-file01  -file03  -file05  -file07  -file09
bandit4@bandit:~$ cd inhere/
```

Ahora para revificar que archivo es legible por humanos y cuales no, usaremos el comando file:

```bash
bandit4@bandit:~/inhere$ file -file00
file: Cannot open `ile00' (No such file or directory)
```

Aqui me di cuenta que teniamos un archivo con un "-" al principio del nombre, para que no lo tome como un parametro, usamos la ruta relativa:

```bash
bandit4@bandit:~/inhere$ file ./-file00
./-file00: data
```

Como podemos ver, es un tipo de archivo "data", no es lo que buscamos, continuamos hasta encontrar una respuesta diferente:

```bash
bandit4@bandit:~/inhere$ file ./-file01
./-file01: data
bandit4@bandit:~/inhere$ file ./-file02
./-file02: data
bandit4@bandit:~/inhere$ file ./-file03
./-file03: data
bandit4@bandit:~/inhere$ file ./-file04
./-file04: data
bandit4@bandit:~/inhere$ file ./-file05
./-file05: data
bandit4@bandit:~/inhere$ file ./-file06
./-file06: data
bandit4@bandit:~/inhere$ file ./-file07
./-file07: ASCII text
```

el archivo "-file07" es un texto legible por humanos, con cat leemos su contenido para ver la bandera:

```bash
bandit4@bandit:~/inhere$ cat ./-file07
Bandera: Descrubela tu!
bandit4@bandit:~/inhere$ 
```


