# 💥 Level 3 💥

## Meta de nivel
La contraseña para el siguiente nivel se almacena en un archivo oculto en el directorio inhere .

Comandos que puedes necesitar para resolver este nivel:
**ls** , **cd** , **cat** , **file** , **du** , **find**

## Solucion

Como nos dice la meta de nivel, debemos leer un archivo que esta en un directorio oculto, con el siguiente comando lo encontraremos:

```bash
bandit3@bandit:~$ ls -a
.  ..  .bash_logout  .bashrc  inhere  .profile
```

### 🛠️Parametros usados

| Parametro o Comando | Descripcion |
| :--- | :--- |
| **`ls`** | Listar archivos o directorios |
| **`-a`** | indico que quiero listar tambien archivos o directorios ocultos |

Si quisieramos mas detalles, usariamos el siguiente parametro:

```bash
bandit3@bandit:~$ ls -la
total 24
drwxr-xr-x   3 root root 4096 Oct 14 09:26 .
drwxr-xr-x 150 root root 4096 Oct 14 09:29 ..
-rw-r--r--   1 root root  220 Mar 31  2024 .bash_logout
-rw-r--r--   1 root root 3851 Oct 14 09:19 .bashrc
drwxr-xr-x   2 root root 4096 Oct 14 09:26 inhere
-rw-r--r--   1 root root  807 Mar 31  2024 .profile
```

### 🛠️Parametros usados

| Parametro o Comando | Descripcion |
| :--- | :--- |
| **`-l`** | indico que quiero un listado detallado(permisos, dueño, etc) |

Accedemos a la carpeta oculta y listamos su contenido:

```bash
bandit3@bandit:~$ cd inhere/
bandit3@bandit:~/inhere$ ls
bandit3@bandit:~/inhere$ ls -a
.  ..  ...Hiding-From-You
```

### 🛠️Parametros usados

| Parametro o Comando | Descripcion |
| :--- | :--- |
| **`cd`** | indico que quiero acceder a un directorio |

encontramos el archivo que tiene bandera para el siguiente nivel, leemos su contenido con cat:

```bash
bandit3@bandit:~/inhere$ cat ...Hiding-From-You 
Bandera: Descrubela tu!
bandit3@bandit:~/inhere$ 
```

