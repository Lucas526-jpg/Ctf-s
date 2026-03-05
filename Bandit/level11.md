# 💥 Level 11 💥

## Meta de nivel
La contraseña para el siguiente nivel se almacena en el archivo data.txt , donde todas las letras minúsculas (az) y mayúsculas (AZ) se han rotado 13 posiciones.

Comandos que puedes necesitar para resolver este nivel:
**grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd**

## Solucion

Primero analizamos si el archivo data se encuentra donde estamos ubicados:

```bash
bandit9@bandit:~$ ls
data.txt
```

Miramos que contiene el archivo:

```bash
bandit11@bandit:~$ cat data.txt 
Gur cnffjbeq vf 7k16JArUVv5LxVuJfsSVdbbtaHGlw9D4
```

junto a cat, usaremos el comando tr para cambiar el orden de como se presentar las letras, indicando que desde la a hasta z ya sean minusculas o mayusculas, sean reemplazadas por n-z y luego de la z por a hasta la m, ya sea mayusculas o minusculas:

```bash
bandit11@bandit:~$ cat data.txt | tr "a-zA-Z" "n-za-mN-ZA-M"
The password is Bandera: Descrubela tu!
bandit11@bandit:~$ 
```