# 📚 Guia de Natas 2 📚

## Conocimientos previos necesarios
Curiosidad.  
(opcional para un mayor entendimiento)  
Que es un servidor, para que sirve.  
Conceptos como Information disclosure y directory listing

## Preparacion
Iniciamos con el siguiente usuario  
Username: natas1  
Password: bandera obtenida de natas 1

## Resolucion
Para poder encontrar la bandera para la siguiente room, como en la room anterior debemos ser curiosos y analizar el codigo fuente de la pagina web, pero a diferencia de las rooms anteriores, esta vez no sera tan facil como analizar el codigo y "bandera encontrada", esta vez hay que leer con cuidado el codigo fuente y ver que informacion se puede obtener.  
En este caso podemos ver una imagen almacenada en una carpeta llamada files, que nos dice eso?... Que existe una carpeta y podria ser accesible!!
Entonces en nuestro enlace "http://natas2.natas.labs.overthewire.org" podemos escribir al final "/files" para decirle al navegador que queremos ir a la carpeta files de la pagina natas2, quedaria asi: "http://natas2.natas.labs.overthewire.org/files".  
Al acceder a esa carpeta veremos dos archivos, al acceder a uno de esos archivos estara la bandera, puedes adividar cual es?

## Aprendizaje
Se aprende sobre la importancia de la configuración del servidor web y la "vulnerabilidad" de divulgación de información (Information Disclosure), específicamente a través de la funcionalidad de Listado de Directorios (Directory Listing).  
En un pentesting real esto podria ser descubierto por herramientas de enumeracion de directorios como gobuster o dirb.
