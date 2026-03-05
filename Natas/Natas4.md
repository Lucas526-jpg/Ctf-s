# 📚 Guia de Natas 4 📚

## Conocimientos previos necesarios 
Entender como funciona el protocolo http.  
Que es la restricción de acceso basada en la cabecera HTTP Referer.

## Preparacion
Iniciamos con el siguiente usuario  
Username: natas4  
Password: bandera obtenida de natas 3

## Resolucion
Al ingresar a la room, vemos un mensaje de acceso denegado, ya que no se ha accedido desde la web "natas5". Esto significa que... ¿debemos acceder a Natas 5 y desde ahí resolver Natas 4? ¡NO!.

Para poder resolver esta room, debemos usar una herramienta que permita modificar la petición HTTP de nuestro dispositivo, engañando al servidor y fingiendo que realizamos una petición de acceso desde Natas 5. En este caso, yo uso Burp Suite.

Para poder entender qué debemos modificar o añadir, es necesario entender las diferentes etapas de una petición HTTP. En este caso, lo necesario para poder "decirle" al servidor que venimos de Natas 5 es añadir una cabecera llamada Referer, la cual le indica al servidor el origen de la URL desde donde se hace la petición.

Con Burp Suite interceptamos la petición HTTP, le añadimos la línea:

Referer: http://natas5.natas.labs.overthewire.org/

Esta línea le dice al servidor "vengo de Natas 5". Luego, continuamos con la petición, y al recibir la respuesta, la bandera estará en la room de Natas 4.

## Aprendizaje
Se aprende sobre la vulnerabilidad de falsificación (spoofing) de la cabecera HTTP. Esto me demostró que cualquier lógica de seguridad que dependa de datos enviados por el cliente puede ser fácilmente engañada y saltada. El servidor nunca debe confiar en cabeceras como Referer para conceder acceso, ya que son manipulables.
