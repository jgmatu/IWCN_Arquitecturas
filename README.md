# Arquitecturas escalables y tolerante a fallos

En esta práctica se van a realizar medidas y estudios sobre las diferentes arquitecturas
vistas en clase, midiendo y jusfiticando el uso de cada una de las arquitecturas.

## Arquitectura centralizada

Como primera parte del ejercicio usaremos postman como cliente web para comprobar
el correcto funcionamiento de nuestro servicio web.

    # [Descargar postman de la página oficial](https://app.getpostman.com/app/download/linux64?_ga=2.91368154.1961962681.1514476967-828309672.1514476967)
    $ tar -xvzf Postman-linux-x64-5.5.0.tar.gz
    $ ./Postman/Postman

Por otro lado arrancamos el servicio web del video club.

    # docker start mysql
    $ mvn spring-boot:run

Una vez arrancado el servicio web debemos comprobar el correcto funcionamiento del servicio
comprobando los métodos del controlador usando el cliente postman.


### Testeo del controlador a través de postman.

La primera petición HTTP será un GET a la página home, el servicio web nos devolverá la vista
HTML con la página de inicio del servicio web. Donde se puede crear el usuario o comprobar una película
para ver.

![alt text](home.png)

Si intentamos acceder a la página de administración de usuarios sin estar autenticados frente al servicio web como usuarios administradores
nos redigirá a la página de login por no estar todavía autenticados, relizando cualquier tipo de petición post get put delete etc...

    POST localhost:8080/management/films
    GET localhost:8080/management/films

Ambas peticiones nos llevan a la misma plantilla:

    login.html

Una vez comprobada la autenticación del servicio web vamos a loguearnos deberemos rellenar en una petición post los siguientes campos en formato
body form-data.

      username : root
      password : root1
      _csrf : 842e8745-aa30-43ce-9d6b-4e1c7220185f

De esta manera seremos capaces de loguearnos frente al servicio web con la configuración de autenticación de spring boot. El servicio web nos
responderá con la página de inicio dandonos la bienvenida al VideoClub.

![alt text](debug-login.png)
