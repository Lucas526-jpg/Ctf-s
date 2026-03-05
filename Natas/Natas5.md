# 📚 Guia de Natas 5 📚

## Conocimientos previos necesarios 
Entender como funciona el protocolo http.  
Que es un cookie y como funciona.

## Preparacion
Iniciamos con el siguiente usuario  
Username: natas5  
Password: bandera obtenida de natas 4

## Resolucion
Al ingresar a la room, vemos un mensaje de acceso denegado, ya que no estamos logueados.

Para poder resolver esta room, debemos usar una herramienta que permita modificar la petición HTTP de nuestro dispositivo, engañando al servidor y fingiendo que realizamos una petición de acceso con una cookie valida..

Con Burp Suite interceptamos la petición HTTP, veremos que donde esta la coockie, esta en opcion loggedin=0, esto significa que nuestro usuario no esta logueado, lo modificamos para engañar al navegador:

loggedin=1

Esta línea le dice al servidor "estoy logueado". Luego, continuamos con la petición, y al recibir la respuesta, la bandera estará en la room.

## Aprendizaje

Se aprende sobre la vulnerabilidad de falsificación (spoofing) de la cookie HTTP. Esto me demostró que cualquier lógica de seguridad que dependa de datos enviados por el cliente puede ser fácilmente engañada y saltada. El servidor nunca debe confiar en cabeceras como Referer para conceder acceso, ya que son manipulables.
