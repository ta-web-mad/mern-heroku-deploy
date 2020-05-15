[<--- Volver al index](/Readme.md)
# 📦 Registro en MongoDB Atlas y Creación de la DB 

El primer paso es **crear una cuenta** en [Mongodb Atlas](https://www.mongodb.com/cloud/atlas/register)


1. Elegimos el plan free
2. Para crear el cluster, elegimos **un servidor que esté en europa y sea gratuito**.
3. Esperamos a que se cree el cluster, debemos ver esta imagen.
4. Vamos a la pestaña ​**Security​** a la opción​ **IP Whitelist** ​y pulsamos en **​ADD IP ADDRESS​**. Marcamos la opción **Allow access from Anywhere**​.
5. Dentro de **​Security**​, vamos a **​MongoDB Users​** y creamos un usuario con los permisos **​Atlas admin**​. **Apuntamos las credenciales** de ese usuario, pues serán las que usemos para conectarnos.
6. Vamos a la pestaña ​Overview​ y pulsamos en C​ONNECT​. Elegimos ​Connect your Application.​
      - Nos aseguramos que el ​DRIVER​ sea Node y copiamos el texto de ​Connection String. Only.
      - Guardamos la cadena de conexión teniendo cuidado de sustituir por la contraseña del usuario de la base de datos.
      - En la cadena de conexión, podemos sustituir ​test​ por el nombre que queramos que tenga nuestra base de datos.

## Ejecutar el seed

En el archivo ​.env​ del `server` hay que crear una variable local con la cadena remota, y cambiar la variable en `mongoose.connect()` tanto en el `seed.js` como en `app.js` o en `mongoose.config.js` (según el proyecto y la estructura de archivos)​.

El `.env`, a parte de configuraciones propias, debe tener estas dos strings de conexión con la base de datos.

```
DBLOCAL=mongodb://localhost:27017/midatabase
DB=mongodb+srv://admin:<password>@cluster0-qyxqt.mongodb.net/test?retryWrites=true&w=majority
 Copy
```

- Ojo! Hay que cambiar `<password>` por la contraseña que corresponda y `test` por el nombre de la base de datos que prefieras.

1. En ​el `seed.js` ponemos la cadena de conexión `DB` en `mongoose.connect()`​.
2. Ejecutamos el script en local: `$node bin/seeds.js`

Si todo ha ido bien, en el siguiente paso veremos que está toda la info en la bd.

## Conectar a la DB Remota con Mongo Compass


1. Copiamos al portapapeles la cadena de conexión remota desde nuestro archivo `.env`.
2. Abrimos Compass. Compass detectará que tenemos la cadena de conexión en el portapapeles y
nos preguntará si queremos usarla. Decimos que sí. Si no, se pega directamente en la barra de direcciones.

