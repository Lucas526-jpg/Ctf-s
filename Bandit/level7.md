# 💥 Level 7 💥

## Meta de nivel
La contraseña para el siguiente nivel se almacena en el archivo data.txt junto a la palabra millionth.

Comandos que puedes necesitar para resolver este nivel:
**man**, **grep**, **sort**, **uniq**, **strings**, **base64**, **tr**, **tar**, **gzip, bzip2, xxd**

## Solucion

Empezamos listando los archivos en nuestra ubicacion:

```bash
bandit7@bandit:~$ ls
data.txt
```

Teniendo el archivo data.txt, usaremos el comando grep para buscar la linea que contenga la palabra "millionth":

```bash
bandit7@bandit:~$ grep "millionth" data.txt 
Bandera: Descrubela tu!
bandit7@bandit:~$ 
```