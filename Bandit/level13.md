# 💥 Level 13 💥

## Meta de nivel
La contraseña para el siguiente nivel se almacena en /etc/bandit_pass/bandit14 y solo puede ser leída por el usuario bandit14 . En este nivel, no se obtiene la siguiente contraseña, sino una clave SSH privada que permite acceder al siguiente nivel. Consulta los comandos que te permitieron acceder a niveles anteriores de Bandit y descubre cómo usar la clave para este nivel.

Comandos que puedes necesitar para resolver este nivel:
**ssh, scp, umask, chmod, cat, nc, install**

## Solucion

Este nivel es mas como un tutorial de como configurar una sshkey y conectarte atravez de la misma.

Empezamos listando el contenido de nuestra ubicacion:

```bash
bandit13@bandit:~$ ls
sshkey.private
```

Al confirmar que esta la clave, nos desconectaremos de la maquina con exit y descargaremos el sshkey en nuestra computadora con scp junto al puerto 2220:

```bash
scar@scar-AHV:~$ scp -P 2220 bandit13@bandit.labs.overthewire.org:sshkey.private .
                         _                     _ _ _   
                        | |__   __ _ _ __   __| (_) |_ 
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_ 
                        |_.__/ \__,_|_| |_|\__,_|_|\__|
                                                       

                      This is an OverTheWire game server. 
            More information on http://www.overthewire.org/wargames

backend: gibson-0
bandit13@bandit.labs.overthewire.org's password: 
```

Nos pedira contraseña, usamos la que pusimos para conectarnos a bandit13, luego se nos descargara y podremos verla con ls:

```bash
sshkey.private                                100% 1679     2.8KB/s   00:00    
scar@scar:~$ 
scar@scar:~$ ls
sshkey.private
```

ahora hay que configurar los permisos, si no, no nos podremos conectar por la sshkey, junto a chmod 600 para decirle que solo nosostros como dueños tienen permisos de lectura y escritura a ese archivo, nadie mas tiene algun permiso:

```bash
scar@scar-AHV:~$ chmod 600 sshkey.private 
```

Ahora usamos la sshkey para conectarnos a la siguiente maquina de bandit:

```bash
scar@scar-AHV:~$ ssh -i sshkey.private -p 2220 bandit14@bandit.labs.overthewire.org
                         _                     _ _ _   
                        | |__   __ _ _ __   __| (_) |_ 
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_ 
                        |_.__/ \__,_|_| |_|\__,_|_|\__|
                                                       

                      This is an OverTheWire game server. 
            More information on http://www.overthewire.org/wargames

backend: gibson-0

      ,----..            ,----,          .---.
     /   /   \         ,/   .`|         /. ./|
    /   .     :      ,`   .'  :     .--'.  ' ;
   .   /   ;.  \   ;    ;     /    /__./ \ : |
  .   ;   /  ` ; .'___,/    ,' .--'.  '   \' .
  ;   |  ; \ ; | |    :     | /___/ \ |    ' '
  |   :  | ; | ' ;    |.';  ; ;   \  \;      :
  .   |  ' ' ' : `----'  |  |  \   ;  `      |
  '   ;  \; /  |     '   :  ;   .   \    .\  ;
   \   \  ',  /      |   |  '    \   \   ' \ |
    ;   :    /       '   :  |     :   '  |--"
     \   \ .'        ;   |.'       \   \ ;
  www. `---` ver     '---' he       '---" ire.org


Welcome to OverTheWire!
bandit14@bandit:~$ 
```

como ya sabemos la ubicacion de la contraseña, solo la mostramos en pantalla:

```bash
bandit14@bandit:~$ cat /etc/bandit_pass/bandit14
Bandera: Descrubela tu!
bandit14@bandit:~$ 
```


