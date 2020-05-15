[<--- Volver al index](/README.md)

# 🔋 Configuración de Heroku y Deploy

El primer paso es **crear una cuenta** en [Heroku](https://www.heroku.com)

1. Crear app. Region: Europa
2. Ponemos el nombre de la app (será el nombre que aparecerá en la url: `http://appname.herokuapp.com`
2. Descargar e instalar **Heroku CLI** siguiendo este [link ](​https://devcenter.heroku.com/articles/heroku-cli​)para instalar en el Sistema Operativo que corresponda.
3. Ejecutar en la terminal ​`$heroku login`​, presionamos cualquier tecla (menos la q) e introducimos las credenciales en la ventana del navegador.
4. Desde la carpeta raiz del proyecto añadimos un repositorio remoto al repositorio local con el siguiente comando:

    `$heroku git:remote -a nombre-de-la-app`

5. Comprobamos que lo ha añadido correctamente ejecutando ​git remote -v
## Configuración de las variables del entorno 

Aquí configuraremos dentro de heroku el equivalente al .env que **no se sube** a heroku.

1. Entramos en heroku y vamos al panel de control de la app que hemos creado
2. Vamos a Settings y desplegamos la pestaña **Reveal config vars**
3. Añadimos una a una todas las variables de entorno que tenemos en nuestro `.env` del server. (Sin comillas, espacios ni saltos de linea)

## Deploy

1. Desde la carpeta raiz del proyecto guardamos los cambios con 
     
    `$git add .`

    `$git commit -m ‘message’`

2. Hacer un push a heroku indicando con el subtree cual es la carpeta donde tiene que mirar.**Lo hacemos desde la carpeta raiz del proyecto**:

   `$git subtree push --prefix=server heroku master`

- Esperamos a que complete la tarea. Esto tardará unos minutos.

3. Ejecutamos `​$heroku logs​ --tail` para ver si hay errores. Este comando es importante para poder ver en nuestro terminal el log de heroku como si fuera el log que nos da el terminal en local cuando hacemos `npm run dev` en server.

4. En heroku, le podemos dar click a la pestaña desplegable ​`More > ​​View logs` ​para seguir el estado del deploy desde el navegador.

5. Cuando todo esté listo, podemos ver nuestra app funcionando en `http://appname.herokuapp.com`
