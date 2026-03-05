# 📚 Guia de Natas 7 📚

## Conocimientos previos necesarios   
Comandos basicos de escalada de directorios.  
Que es local file inclusion(LFI).

## Preparacion
Iniciamos con el siguiente usuario  
Username: natas7  
Password: bandera obtenida de natas 6

## Resolucion
Al ingresar a la room, veremos una pagina con dos enlace, una que es el inicio y otra que es "sobre nosotros".

Al analizar el codigo fuente veremos un interesante comentario que nos indica donde esta ubicada la bandera, esta ubicada en otro directorio donde estamos ahora mismo.  
Para poder llegar a ese directorio tendremos que experimentar con la pagina un poco, al acceder a la pagina "sobre nosotros" o inicio, podemos ver en la url que la pagina en la que estamos se maneja de la forma "page=index.html", para poder movernos por el servidor podemos usar eso a nuestro favor, por ejemplo:

page=etc/natas_webpass/natas8, al hacerlo veremos un error, el cual si le prestamos atencion, nos dira donde estamos ubicados!  
Luego no es mas que movernos por el servidor hasta llegar a la ubicacion donde esta la bandera:

page=../../../../etc/natas_webpass/natas8

## Aprendizaje
Este es otro tipo de local file inclusion, el cual debemos tener en cuenta a la hora de realizar una auditoria.
