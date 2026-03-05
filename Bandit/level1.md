# 💥 Level 1 💥 

## Meta de nivel

La contraseña para el siguiente nivel se almacena en un archivo llamado - ubicado en el directorio de inicio

Comandos que puedes necesitar para resolver este nivel:
**ls** , **cd** , **cat** , **file** , **du** , **find** 

## Solucion

para acceder al contenido en pantalla, debemos saber que el comando "cat" no sirve para imprimir en pantalla el contenido de un archivo, pero al intentar usar el comando:

```bash
bandit1@bandit:~$ cat -
^C
```

se queda trabajo y se debe cancelar, al investigar un poco, vi que el "-" es usado para asignar parametros en un comando, eso es lo que nos da problemas ahora mismo, para evitar que lo tome como un parametro hay que usar "./" que como una ruta relativa(tenemos que estar ubicados en la misma carpeta que el archivo -):

```bash
bandit1@bandit:~$ cat ./- 
``` 

**Descrubrela tu!**

```bash
bandit1@bandit:~$ 
```