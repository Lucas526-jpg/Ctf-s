# Lab: SQL injection vulnerability allowing login bypass

Como el ejercicio nos pide que iniciemos sesion con el usuario administrator, buscaremos un login donde efectuar la inyeccion, una vez encontrado, ademas de poner el usuario administrator, podemos poner seguido la expresion booleana verdadera ' or 1=1-- -, podemos ponerla tambien en donde va la contraseña, al darle a iniciar sesion con esa expresion, obtendremos acceso al usuario
