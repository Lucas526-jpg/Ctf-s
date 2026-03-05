# 💥 Level 0 💥 

## Meta de nivel

El objetivo de este nivel es que inicies sesión en el juego mediante SSH. El host al que debes conectarte es bandit.labs.overthewire.org , en el puerto 2220. El nombre de usuario y la contraseña son bandit0 . Una vez iniciada la sesión, ve a la página del Nivel 1 para descubrir cómo superarlo.

## Solucion

Para este nivel, solo hay que investigar sobre como usar el servicio ssh, donde:

- **ssh**: es el servicio que usaremos para conectarnos de forma remota a la maquina objetivo con usuario y contraseña "bandit0".

- **-p**: es el parametro que usaremos para especificar un puerto para la conexion.

- **usuario@host**: es la forma para especificar el usuario con el que nos vamos a conectar y el host.

dando como resultado:

```bash
ssh -p 2220 bandit0@bandit.labs.overthewire.org
```

al usar este comando, se nos pedira una contraseña :

```bash

                         _                     _ _ _   
                        | |__   __ _ _ __   __| (_) |_ 
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_ 
                        |_.__/ \__,_|_| |_|\__,_|_|\__|
                                                       

                      This is an OverTheWire game server. 
            More information on http://www.overthewire.org/wargames

backend: gibson-0
bandit0@bandit.labs.overthewire.org's password: 
```

Al usar la contraseña que es bandit0, habremos obtenido el acceso inicial a la maquina objetivo:

```bash

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

If you find any problems, please report them to the #wargames channel on
discord or IRC.

--[ Playing the games ]--

  This machine might hold several wargames.
  If you are playing "somegame", then:

    * USERNAMES are somegame0, somegame1, ...
    * Most LEVELS are stored in /somegame/.
    * PASSWORDS for each level are stored in /etc/somegame_pass/.

  Write-access to homedirectories is disabled. It is advised to create a
  working directory with a hard-to-guess name in /tmp/.  You can use the
  command "mktemp -d" in order to generate a random and hard to guess
  directory in /tmp/.  Read-access to both /tmp/ is disabled and to /proc
  restricted so that users cannot snoop on eachother. Files and directories
  with easily guessable or short names will be periodically deleted! The /tmp
  directory is regularly wiped.
  Please play nice:

    * don't leave orphan processes running
    * don't leave exploit-files laying around
    * don't annoy other players
    * don't post passwords or spoilers
    * again, DONT POST SPOILERS!
      This includes writeups of your solution on your blog or website!

--[ Tips ]--

  This machine has a 64bit processor and many security-features enabled
  by default, although ASLR has been switched off.  The following
  compiler flags might be interesting:

    -m32                    compile for 32bit
    -fno-stack-protector    disable ProPolice
    -Wl,-z,norelro          disable relro

  In addition, the execstack tool can be used to flag the stack as
  executable on ELF binaries.

  Finally, network-access is limited for most levels by a local
  firewall.

--[ Tools ]--

 For your convenience we have installed a few useful tools which you can find
 in the following locations:

    * gef (https://github.com/hugsy/gef) in /opt/gef/
    * pwndbg (https://github.com/pwndbg/pwndbg) in /opt/pwndbg/
    * gdbinit (https://github.com/gdbinit/Gdbinit) in /opt/gdbinit/
    * pwntools (https://github.com/Gallopsled/pwntools)
    * radare2 (http://www.radare.org/)

--[ More information ]--

  For more information regarding individual wargames, visit
  http://www.overthewire.org/wargames/

  For support, questions or comments, contact us on discord or IRC.

  Enjoy your stay!

bandit0@bandit:~$ 
```

Con esto aprendido y completado, podremos empezar hacia bandit1:

La contraseña para el siguiente nivel se guarda en un archivo llamado "readme" ubicado en el directorio de inicio. Usa esta contraseña para iniciar sesión en bandit1 mediante SSH. Cuando encuentres la contraseña de un nivel, usa SSH (en el puerto 2220) para iniciar sesión en ese nivel y continuar el juego.

Comandos que puedes necesitar para resolver este nivel:
**ls** , **cd** , **cat** , **file** , **du** , **find**

Para obtener la contraseña asi accedemos al nivel1, buscaremos el archivo readme con ls:

```bash
bandit0@bandit:~$ ls
readme
```

una vez ubicado, mostramos en pantalla su contenido

```bash
bandit0@bandit:~$ cat readme 
Congratulations on your first steps into the bandit game!!
Please make sure you have read the rules at https://overthewire.org/rules/
If you are following a course, workshop, walkthrough or other educational activity,
please inform the instructor about the rules as well and encourage them to
contribute to the OverTheWire community so we can keep these games free!

The password you are looking for is: Encuentrala tu!

bandit0@bandit:~$ 
```
