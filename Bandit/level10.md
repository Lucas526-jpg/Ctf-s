# 💥 Level 10 💥

## Meta de nivel
La contraseña para el siguiente nivel se almacena en el archivo data.txt , que contiene datos codificados en base64.

Comandos que puedes necesitar para resolver este nivel:
**grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd**

## Solucion 

Primero analizamos si el archivo data se encuentra donde estamos ubicados:

```bash
bandit9@bandit:~$ ls
data.txt
```

Revisamos el contenido del data.txt:

```bash
bandit10@bandit:~$ cat data.txt 
VGhlIHBhc3N3b3JkIGlzIGR0UjE3M2ZaS2IwUlJzREZTR3NnMlJXbnBOVmozcVJyCg==
```

Para decodificar la contraseña, podemos usar el comando base64 con el parametro -d que le dice que es para decodificar un archivo:

```bash
bandit10@bandit:~$ base64 -d data.txt
The password is Bandera: Descrubela tu!
bandit10@bandit:~$ 
```

