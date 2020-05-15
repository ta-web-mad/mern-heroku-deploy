# Deploy a Heroku de un MERN Stack 🔥

Con esta guía haremos un deploy sencillo pero funcional para los proyectos finales.

Haremos el deploy de la app en **Heroku** y la db irá en **MongoDB Atlas**.

## Server - Configuración entorno local:

1. Instalar y configurar el módulo ​`dotenv​`. Acordaos de requerir el módulo donde sea necesario.
2. Asegurarse de tener en el `.gitignore` los archivos o carpetas que queremos evitar que se suban.
3. En el fichero `.env`, añadir la URL de la base de datos local. También tenemos que añadir otros datos que no queremos que se suban al repositorio (credenciales, claves API...).
4. En `app.js` poner antes del `module.exports` cual es el `index` que tiene que enviar:
```javascript
app.use((req,res)=>{
res.sendFile(__dirname+"/public/index.html");
})

//aquí deben ir las rutas de la api (nuestras rutas del back), ejemplo:
app.use("/api",require("/routes"))
```

## Client - Configuración del entorno local:

1. Confirmar que está instalado el `dotenv-cli` en la **carpeta client**. De lo contrario instalarlo:

    `$npm install dotenv-cli`

2. Crear los dos ficheros de variables de entorno **en la raíz de la carpeta client**:

   `$touch .env.dev .env.prod`


3. Poner las variables de entorno. También se añadirán los otros datos que no queremos que se suban al repositorio y pertenecen al front (credenciales, claves API, etc.)

  `.env.dev` 

```mk
REACT_APP_API_URL=http://localhost:5000/api
REACT_APP_APP_URL=http://localhost:5000/
```

`.env.prod` 

```mk
REACT_APP_API_URL=http://myapp.herokuapp.com/api
REACT_APP_APP_URL=http://myapp.herokuapp.com/
```
- Es muy importante sustituir todas las url de los `services`que tengamos en la app por las variables de entorno que hemos creado con `process.env.REACT_APP_API_URL`

4. Dentro del archivo `package.json`en **client** hay que configurar los `scripts`:

```json
"start" : "dotenv -e .env.dev react-scripts start",
"build-dev" : "dotenv -e .env.dev react-scripts build",
"build-prod" : "dotenv -e .env.dev react-scripts build",
```

5. Ejecutar `npm run build-prod` **en la carpeta client** y mover **todo el contenido** de la carpeta **build** (se ha creado después de hacer la build) dentro de **public** en **server** (la carpeta public de server hay que borrarla antes de mover el contenido de client).
