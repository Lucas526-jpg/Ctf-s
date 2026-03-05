# 📚 Writeups de  CTFS 📚

## Indice de plataformas

* [OverTheWire:Bandit](#bandit)
* [DockerLabs](#-dockerlabs-)
* [HackTheBox](#hackthebox)
* [OverTheWire:Natas](#overthewire-natas)
* [PortSwiggerSQLI](#portswigger-sqli)

## Bandit 

| Room | Dificultad | Habilidades Destacadas | Acceso Directo |
| :--- | :--- | :--- | :--- |
| **Level 0** | ![Dificultad](https://img.shields.io/badge/_Muy_facil-green?style=flat-square) | Conexion ssh. | [Ver Solución Aquí](Bandit/level0.md) |
| **Level 1** | ![Dificultad](https://img.shields.io/badge/_Muy_facil-green?style=flat-square) | Uso de comandos como ls y cat con ruta relativa. | [Ver Solución Aquí](Bandit/level1.md) |
| **Level 2** | ![Dificultad](https://img.shields.io/badge/_Muy_facil-green?style=flat-square) | Ruta relativa, Nombre con espacios | [Ver Solución Aquí](Bandit/level2.md) |
| **Level 3** | ![Dificultad](https://img.shields.io/badge/_Muy_facil-green?style=flat-square) | Archivos ocultos | [Ver Solución Aquí](Bandit/level3.md) |
| **Level 4** | ![Dificultad](https://img.shields.io/badge/Facil-blue?style=flat-square) | Comando file | [Ver Solución Aquí](Bandit/level4.md) |
| **Level 5** | ![Dificultad](https://img.shields.io/badge/Facil-blue?style=flat-square) | Busqueda de archivos con find | [Ver Solución Aquí](Bandit/level5.md) |
| **Level 6** | ![Dificultad](https://img.shields.io/badge/Facil-blue?style=flat-square) | Busqueda de archivos y uso del 2>/dev/null | [Ver Solución Aquí](Bandit/level6.md) |
| **Level 7** | ![Dificultad](https://img.shields.io/badge/Facil-blue?style=flat-square) | Uso del comando grep para analizar lineas | [Ver Solución Aquí](Bandit/level7.md) |
| **Level 8** | ![Dificultad](https://img.shields.io/badge/_Editar-green?style=flat-square) | Uso del comando uniq y sort para el manejo de texto | [Ver Solución Aquí](Bandit/level8.md) |
| **Level 9** | ![Dificultad](https://img.shields.io/badge/Facil-blue?style=flat-square) | Uso del comando string para analizar texto no legible | [Ver Solución Aquí](Bandit/level9.md) |
| **Level 10** | ![Dificultad](https://img.shields.io/badge/Facil-blue?style=flat-square) | Decodificar base64 | [Ver Solución Aquí](Bandit/level10.md) |
| **Level 11** | ![Dificultad](https://img.shields.io/badge/_Medio-yellow?style=flat-square) | Comando tr para intercambiar letras | [Ver Solución Aquí](Bandit/level11.md) |
| **Level 12** | ![Dificultad](https://img.shields.io/badge/_Medio-yellow?style=flat-square) | Analisis, cambio de nombre y extraccion de archivos | [Ver Solución Aquí](Bandit/level12.md) |
| **Level 13** | ![Dificultad](https://img.shields.io/badge/_Muy_facil-green?style=flat-square) | Conexion con sshkey | [Ver Solución Aquí](Bandit/level13.md) |
| **Level 14** | ![Dificultad](https://img.shields.io/badge/Facil-blue?style=flat-square) | Uso de netcat | [Ver Solución Aquí](Bandit/level14.md) |
| **Level 15** | ![Dificultad](https://img.shields.io/badge/Facil-blue?style=flat-square) | Uso de s_client | [Ver Solución Aquí](Bandit/level15.md) |
| **Level 16** | ![Dificultad](https://img.shields.io/badge/_Medio-yellow?style=flat-square) | Analisis de puertos, juntos con analisis de certificados ssl | [Ver Solución Aquí](Bandit/level16.md) |
| **Level 17** | ![Dificultad](https://img.shields.io/badge/_Muy_facil-green?style=flat-square) | Analisis de diferencias entre dos archivos | [Ver Solución Aquí](Bandit/level17.md) |

## 🐋 DockerLabs 🐋

| Room | Dificultad | Habilidades Destacadas | Acceso Directo |
| :--- | :--- | :--- | :--- |
| **FirstHacking** | ![Dificultad](https://img.shields.io/badge/_Muy_facil-green?style=flat-square) | Vulnerabilidad critica en una version antigua del servicio ftp                              | [Ver Solución Aquí](Dockerlabs/firsthacking.md) |
| **Tproot**       | ![Dificultad](https://img.shields.io/badge/_Muy_facil-green?style=flat-square) | Vulnerabilidad critica en la version 2.3.4 del servicio ftp                                 | [Ver Solución Aquí](Dockerlabs/tproot.md)       |
| **Trust**        | ![Dificultad](https://img.shields.io/badge/_Muy_facil-green?style=flat-square) | Escaneo de directorios, ataque de fuerza bruta y acceso SSH                                 | [Ver Solución Aquí](Dockerlabs/trust.md)        |
| **Vacaciones**   | ![Dificultad](https://img.shields.io/badge/_Muy_facil-green?style=flat-square) | Analisis de directorios web, fuerza bruta, ssh, comandos de linux y escalada de privilegios | [Ver Solución Aquí](Dockerlabs/vacaciones.md)   |
| **Breakmyssh**   | ![Dificultad](https://img.shields.io/badge/_Muy_facil-green?style=flat-square) | Ataque de fuerza bruta con un usuario por defecto en ssh                                    | [Ver Solución Aquí](Dockerlabs/breakmyssh.md)   |
| **Borazuwarah**  | ![Dificultad](https://img.shields.io/badge/_Muy_facil-green?style=flat-square) | Analisis de metadatos, fuerza bruta y ssh                                                   | [Ver Solución Aquí](Dockerlabs/borazuwarah.md)  |

## HackTheBox

| Máquina | Dificultad | Habilidades Destacadas | Informe (PDF) |
| :--- | :--- | :--- | :--- |
| **Meow** | ![Dificultad](https://img.shields.io/badge/_Facil-blue?style=flat-square) | Enumeración de servicios, fuerza bruta en servicio telnet. | [Ver Informe](HackTheBox/informe_Meow.pdf) |
| **Fawn** | ![Dificultad](https://img.shields.io/badge/_Facil-blue?style=flat-square) | Enumeración de servicios, vulnerabilidad en servicio ftp. | [Ver Informe](HackTheBox/informe_Fawn_HTB_.pdf) |

## OverTheWire: Natas

| Room | Dificultad | Habilidades Destacadas | Acceso Directo |
| :--- | :--- | :--- | :--- |
| **Level 0** | ![Dificultad](https://img.shields.io/badge/_Facil-blue?style=flat-square) | Analisis de codigo fuente. | [Ver Solución Aquí](Natas/Natas0.md) |
| **Level 1** | ![Dificultad](https://img.shields.io/badge/_Facil-blue?style=flat-square) | Analisis de codigo fuente. | [Ver Solución Aquí](Natas/Natas1.md) |
| **Level 2** | ![Dificultad](https://img.shields.io/badge/_Facil-blue?style=flat-square) | Analisis de subdirectorios | [Ver Solución Aquí](Natas/Natas2.md) |
| **Level 3** | ![Dificultad](https://img.shields.io/badge/_Facil-blue?style=flat-square) | Busqueda del robots.txt. | [Ver Solución Aquí](Natas/Natas3.md) |
| **Level 4** | ![Dificultad](https://img.shields.io/badge/_Facil-blue?style=flat-square) | Spoofing de cabecera http. | [Ver Solución Aquí](Natas/Natas4.md) |
| **Level 5** | ![Dificultad](https://img.shields.io/badge/_Facil-blue?style=flat-square) | Spoofing de cookie http. | [Ver Solución Aquí](Natas/Natas5.md) |
| **Level 6** | ![Dificultad](https://img.shields.io/badge/_Facil-blue?style=flat-square) | IDOR (Insecure Direct Object Reference) o LFI (Local File Inclusion) simple. | [Ver Solución Aquí](Natas/Natas6.md) |

## PortSwigger SQLI

| Room | Dificultad | Habilidades Destacadas | Acceso Directo (Writeup) |
| :--- | :--- | :--- | :--- |
| **SQL injection vulnerability in WHERE clause allowing retrieval of hidden data** | ![Dificultad](https://img.shields.io/badge/_Facil-blue?style=flat-square) | Explotacion SQL. | [Ver Solución Aquí](PortSwiggerSQLI/SQLI0.md) |
| **SQL injection vulnerability allowing login bypass** | ![Dificultad](https://img.shields.io/badge/_Facil-blue?style=flat-square) | Explotacion SQL. | [Ver Solución Aquí](PortSwiggerSQLI/SQLI1.md) |
| **SQL injection attack, querying the database type and version on Oracle** | ![Dificultad](https://img.shields.io/badge/_Facil-blue?style=flat-square) | Explotacion SQL. | [Ver Solución Aquí](PortSwiggerSQLI/SQLI2.md) |
| **SQL injection attack, querying the database type and version on MySQL and Microsoft** | ![Dificultad](https://img.shields.io/badge/_Facil-blue?style=flat-square) | Explotacion SQL. | [Ver Solución Aquí](PortSwiggerSQLI/SQLI3.md) |
| **SQL injection attack, listing the database contents on non-Oracle databases** | ![Dificultad](https://img.shields.io/badge/_Facil-blue?style=flat-square) | Explotacion SQL. | [Ver Solución Aquí](PortSwiggerSQLI/SQLI4.md) |