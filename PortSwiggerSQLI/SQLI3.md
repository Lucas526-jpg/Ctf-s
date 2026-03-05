# 📚SQL injection attack, querying the database type and version on MySQL and Microsoft📚

## Conocimientos previos

El uso de burpsuite y su repetidor.

## Resolucion

Para poder resolver este laboratio, se usa una logica similar a la del laboratorio anterior, deberemos saber cuantas columnas tiene la base de datos, para esto, podemos usar la consulta ' ORDER BY 1-- -, podemos usarla directamente desde la url.

al realizar las pruebas, podremos ver como la base de datos tambien tiene dos columnas, entonces como siguiente paso es adaptar nuestra consulta de version en base a la cantidad de columnas que tiene nuestra base de datos, en el cheat sheet nos dan la siguiente consulta:  SELECT @@version, para poder usarla correctamente en este lab, deberemos usar UNION, seguido de la consulta SELECT @@version, desde aqui es donde varia segun la cantidad de columnas, ya que deberemos añadir tantos null como columnas tenga la base de datos.

Nos quedaria asi ' UNION SELECT @@version, null-- -, al ingresar esta inyeccion en la url, habremos completado este laboratorio.


