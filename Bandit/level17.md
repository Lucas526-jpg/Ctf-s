# 💥 Level 17 💥

## Meta de nivel

Hay dos archivos en el directorio de inicio: passwords.old y passwords.new . La contraseña para el siguiente nivel se encuentra en passwords.new y es la única línea que se ha modificado entre passwords.old y passwords.new.

NOTA: si has resuelto este nivel y ves "¡Adiós!" al intentar iniciar sesión en bandit18, esto está relacionado con el siguiente nivel, bandit19.

Comandos que puedes necesitar para resolver este nivel:
**gato, grep, ls, diff**

## Solucion

Para analizar las modificaciones de archivos, usaremos el comando diff:

```bash
bandit17@bandit:~$ diff passwords.old passwords.new 
42c42
< BMIOFKM7CRSLI97voLp3TD80NAq5exxk
---
> Bandera: Descrubela tu!
bandit17@bandit:~$ 
```

