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
      <html>
          <head>
              <meta charset="utf-8" />
              <link rel="stylesheet" href="/css/login.css" type="text/css" />
              <meta name="viewport" content="width=device-width, initial-scale=1.0" />
              <title>Video Club</title>
              <script src="/js/jquery-3.2.1.min.js" type="text/javascript"></script>
              <script src="/js/jquery.validate.min.js" type="text/javascript"></script>
              <script src="/js/login.js" type="text/javascript"></script>
          </head>
          <body>
              <div class="headerP">
                  <h1>Video Club</h1>
                  <div class="lan">
                      <a href="?lang=es">
                          <img src="/images/es.png" class="iconolan" alt="ES" />
                      </a>
                      <a href="?lang=en">
                          <img src="/images/en.png" class="iconolan" alt="EN" />
                      </a>
                  </div>
              </div>
              <div class="rowP">
                  <div class="col-2 menu">
                      <ul>
                          <li>
                              <a href="/create/user">Create new user</a>
                          </li>
                      </ul>
                  </div>
                  <div class="col-10">
                      <h2>Login</h2>
                      <form id="formlogin" role="form" method="post" action="/login">
                          <div class="newpform">
                              <label>User</label>
                              <br />
                              <input type="text" id="username" name="username" />
                              <br />
                              <br />
                              <label>Password</label>
                              <br />
                              <input type="password" id="password" name="password" />
                              <br />
                              <br />
                              <input type="submit" id="login" value="Login" />
                          </div>
                      </form>
                  </div>
              </div>
          </body>
      </html>
