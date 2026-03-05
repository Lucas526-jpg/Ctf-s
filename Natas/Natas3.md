# 📚 Guia de Natas 3 📚

## Conocimientos previos necesarios 
Que es un archivo Robots.txt y para que sirve.

## Preparacion
Iniciamos con el siguiente usuario  
Username: natas3
Password: bandera obtenida de natas 2

## Resolucion
Para poder encontrar la bandera para la siguiente room, como en la room anterior debemos analizar el codigo fuente de la pagina web, la clave esta en un comentario "No more information leaks!! Not even Google will find it this time...", se refiere a que ni google lo encontraria, esto hace referencia al robots.txt, que le dice a un motor de busqueda que paginas se deben mostrar o no.  
Al acceder al subdirectorio "/robots.txt" podemos encontrar un directorio secreto, accedemos al el para encontrar un archivo.txt llamado users, el cual tendra la bandera que buscamos.  

## Aprendizaje
Se aprende sobre la importancia de la configuración del servidor web y la "vulnerabilidad" de divulgación de información (Information Disclosure), ya que el robots.txt no es una capa de seguridad, solo funciona para los motores de busqueda, haciendo que un ciberdelincuente pueda acceder a directorios "ocultos" (solo para el motor de busqueda) como vimos en esta room.
