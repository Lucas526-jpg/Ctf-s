# 💥 Level 8 💥

## Meta de nivel
La contraseña para el siguiente nivel se almacena en el archivo data.txt y es la única línea de texto que aparece solo una vez.

Comandos que puedes necesitar para resolver este nivel:
**grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd**

## Solucion 

Empezamos listando el contenido de nuestra ibucacion para confirmar que el archivo data.txt existe:

```bash
bandit8@bandit:~$ ls
data.txt
```

Para mostrar las lineas que estan duplicadas o las que no, usaremos el comando uniq:

```bash
bandit8@bandit:~$ uniq -u data.txt 
eEAA4ytk957MspwYKLeOgooPzJKOg8jY
VVamYLR8vQaPhZV8sFPh7NVrqt3cwx5E
q9C0UQZ52GznEieTtXOgPrVvIvB60jxL
1kopVbuefPoyJ5GDXH0q46SXQVQQZmge
HeSAR9opVOfF0r39s92ig6Pu9EOeVwhF
6WLU0f8RPUW6O9z6rdXb2wHufXmbYn8f
.... Y continua con 900 lineas mas...
bandit8@bandit:~$ 
```

Al investigar un poco como funciona uniq, entendi que el comando uniq cuenta duplicados pero unicamente si estan en la linea siguiente, es decir, si no estan juntas no las tomara como duplicados, por ende, lo que habria que hacer antes de usar uniq sera ordenar alfabeticamente el archivo, con el comando sort:

```bash
bandit8@bandit:~$ sort data.txt | uniq -u
Bandera: Descrubela tu!
bandit8@bandit:~$ 
```

Use dos comandos en una linea, primero use sort para ordenar alfabeticamente el archivo data.txt, luego uso "|" para tomar la salida de sort y usarla como los datos que uniq analizara.
