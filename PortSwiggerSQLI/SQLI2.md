# SQL injection attack, querying the database type and version on Oracle
## Conocimientos previos

-Uso de burpsuite.  
-comandos de sqli basicos para ver cantidad de columnas, tipo de datos de columna.

## Resolucion

Al inicar el laboratorio. Podemos confirmar que la pagina es vulnerable a SQLI ya que al seleccionar una etiqueta de filtrado, si ponemos una comilla simple ( ' ) al final de la url o en burpsuite, podremos ver como la pagina da error, advirtiendo que es vulnerable.

Para empezar a resolver el lab, debemos identificar cual es nuestro objetivo, como nos dice en la parte superior de la web vulnerable, debemos conseguir que la base de datos nos devuelva la siguiente cadema: 'Oracle Database 11g Express Edition Release 11.2.0.2.0 - 64bit Production, PL/SQL Release 11.2.0.2.0 - Production, CORE 11.2.0.2.0 Production, TNS for Linux: Version 11.2.0.2.0 - Production, NLSRTL Version 11.2.0.2.0 - Production', para esto, PortSwigger nos da un comando en el apartado "pistas" que deberemos usar que es: UNION SELECT 'abc' FROM dual y SELECT banner FROM v$version, pero como los usamos? Bien, empezare explicando un poco sobre la funcion de estos comandos.

- UNION SELECT: Es el operador SQL que combina el conjunto de resultados de la consulta original (SELECT columna1, columna2...) con el conjunto de resultados de la consulta inyectada.  
- v$version: Es una vista del sistema en bases de datos Oracle que contiene información sobre la versión y los componentes de la base de datos.  
- banner: Es una columna de la vista v$version que generalmente contiene una cadena de texto larga con la información completa de la versión (por ejemplo, "Oracle Database 19c Enterprise Edition...").  
- -- (Doble guion): Es un comentario SQL que anula o ignora el resto de la consulta original que sigue a la inyección (como la comilla final '; o una cláusula AND).  
- null: Es un valor nulo utilizado como marcador de posición. Su función es asegurar que la consulta inyectada tenga el número correcto de columnas para coincidir con la consulta origina.

Ahora vamos a analizar la logica de la inyeccion, para poder usarla y que no nos devuelva un error deremos usar una sintaxis correcta que varia en todas las bases de datos, segun sus numeros de columnas y generalmente el tipo de dato que almacenan.  
En este caso, con la inyeccion ' ORDER BY 2-- podremos ver si la base de datos tiene 1 columna, si es el caso, dara error, si solo se inyecta y no da ningun error significa que la base de datos tiene mas columnas, tocaria inyectar ' ORDER BY 2-- y asi hasta llegar a un error, cuando lleguemos al error, entonces tendremos el numero de columnas de la base de datos, que sera el numero colocado en order by menos 1.

Sabiendo eso, procedemos a inyectar la consulta ' UNION SELECT banner, null FROM v$version --, ya que al tener dos columnas, ponemos banner para la primera columna y null como segunda columna, si tuviera tres seria ' UNION SELECT banner, null, null FROM v$version --, al inyectar la consulta habremos superado el laboratorio.
