# 💥 Level 2 💥

## Meta de nivel
La contraseña para el siguiente nivel se almacena en un archivo llamado --spaces in this filename--ubicado en el directorio de inicio.

Comandos que puedes necesitar para resolver este nivel:
**ls** , **cd** , **cat** , **file** , **du** , **find**

## Solucion

Empezamos listando el contenido de nuestra ubicacion con ls:

```bash
bandit2@bandit:~$ ls
--spaces in this filename--
```

al identificar el archivo, con cat intentaremos leerlo usando comillas dobles para aceptar espacios:

```bash
bandit2@bandit:~$ cat "--spaces in this filename--" 
cat: unrecognized option '--spaces in this filename--'
Try 'cat --help' for more information.
```


al investigar, me doy cuenta que estamos con el mismo problema que la room anterior, donde a los guiones los toma como una configuracion para parametros, se arreglaria con la ruta relativa:

```bash
bandit2@bandit:~$ cat ./"--spaces in this filename--" 
Bandera: Encuentrala tu!
bandit2@bandit:~$ 

```
