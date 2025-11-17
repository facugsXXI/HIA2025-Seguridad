## ⚙️ Configuración inicial

1. **Crear cuenta en LocalXpose**  
   - Ingresa a [LocalXpose](https://localxpose.io/) y regístrate.  
   - Una vez dentro, ve a la sección **Access**.  
   - Copia el **Access Token** que te proporciona la plataforma.

2. **Agregar el token como variable de entorno**  
   - En tu sistema, define la variable `LX_ACCESS_TOKEN` con el valor del token copiado.  

   ### 🔧 Ejemplos:
   - **Linux/macOS (bash/zsh):**
     ```bash
     export LX_ACCESS_TOKEN="TU_TOKEN_AQUI"
     ```

   - **Windows (PowerShell):**
     ```powershell
     setx LX_ACCESS_TOKEN "TU_TOKEN_AQUI"
     ```
     Luego cierra y vuelve a abrir la terminal para que se aplique.


3. Ejecutar Docker Compose

  En la carpeta del proyecto:

    docker compose up -d

  Esto iniciará:

    localxpose

    nginx secure proxy

    adminer

    phpmyadmin

4. Obtener la URL pública generada por LocalXpose

  Ejecutá:

    docker logs localxpose

  Verás una dirección similar a:

    https://ofjcf3hcvv.loclx.io

  Copiala y pegala en el navegador.

5. Entender la primera pantalla (403 Forbidden)

  Cuando ingreses por primera vez vas a ver:

    403 Forbidden

  Esto es normal.
  El proxy bloquea todo por defecto y sólo permite las rutas:

    /adminer

    /phpmyadmin

6. Acceder a los servicios

  Tomá la URL entregada por LocalXpose (ejemplo):

    https://ofjcf3hcvv.loclx.io/


  Y agregá la ruta deseada:

    Adminer
    https://ofjcf3hcvv.loclx.io/adminer

    phpMyAdmin
    https://ofjcf3hcvv.loclx.io/phpmyadmin

7. Autenticación

  Al entrar te pedirá usuario y contraseña definidos en .htpasswd.
  Ejemplo de credenciales de prueba:

    usuario: admin password: admin

    usuario: user password: user

Si las credenciales son correctas, te redirigirá al servicio seleccionado.

8. Comportamiento esperado: errores 403 ocasionales

  Durante la navegación, si aparece nuevamente:

    403 Forbidden


  Es normal.
  Todavía se están ajustando algunas redirecciones internas de los servicios.

  Simplemente volvé a la ruta correcta:

    /adminer

    /phpmyadmin

⏳ Nota importante sobre LocalXpose (versión gratuita)

  El túnel gratuito tiene un límite de tiempo aproximado de 30 minutos.
  Pasado ese tiempo deberás volver a levantar el servicio ejecutando:

    docker compose restart localxpose


  Y obtener una nueva URL pública.
