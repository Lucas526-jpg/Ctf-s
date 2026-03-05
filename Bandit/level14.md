# 💥 Level 14 💥

## Meta de nivel
La contraseña para el siguiente nivel se puede recuperar enviando la contraseña del nivel actual al puerto 30000 en localhost .

Comandos que puedes necesitar para resolver este nivel:
**ssh, telnet, nc, openssl, s_client, nmap**

## Solucion 

Para enviar la contraseña del nivel actual al puerto 30000 en localhost, usamos nc, en este caso use un echo junto a "|" para hacerlo mas rapidamente:

```bash
bandit14@bandit:~$ echo MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS | nc localhost 30000
Correct!
Bandera: Descrubela tu!
bandit14@bandit:~$ 
```



