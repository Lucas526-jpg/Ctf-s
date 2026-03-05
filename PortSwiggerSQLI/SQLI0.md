# 📚 Lab: SQL injection vulnerability in WHERE clause allowing retrieval of hidden data 📚

Como no sabemos si la base de datos es oracle, podemos analizar la cantidad de columnas despues de seleccionar un producto con el siguiente comando en la url para verificar si da error, como en mi caso no dio error, la cantidad de columnas que tiene la tabla usada son dos y ademas la base de datos no es oracle:  

' UNION SELECT null,null-- -

Como el ejercicio nos dice que mostremos mas informacion de la que normalmente se mostraria, buscamos inyectar codigo sql a travez de las categorias, dandole un valor booleano verdadero para asi mostrar todos los productos, ya sea que esten listos para la venta o no, con el siguiente comando:

' or 1=1-- -
