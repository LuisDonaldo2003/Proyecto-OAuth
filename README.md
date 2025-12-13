
## Instalar cacert.pem (SSL) 👀

Cuando se realiza el inicio de sesión mediante el login de Google, arroja el siguiente error.

cURL error 60: SSL certificate: unable to get local issuer certificate

Esto es debido a que PHP no cuenta con un certificado SSL, es por eso que se necesita obtener
- **Descargar** Da click a [cacert.pem](https://curl.se/ca/cacert.pem), descarga el archivo en automático


- **Guardar:** Copia `cacert.pem` en la carpeta de certificados de tu PHP. En mi caso la ruta es:

	C:\php-8.4.13\extras\ssl\

- **Editar `php.ini`:** Dentro del archivo se encuentran las siguientes directivas, las cuales se tiene que eliminar su ";", el resultado en mi caso es el siguiente


	- `curl.cainfo = C:\php-8.4.13\extras\ssl\cacert.pem`
	- `openssl.cafile = C:\php-8.4.13\extras\ssl\cacert.pem`

- **Reiniciar Apache:** Esto en caso de que se use Xampp, la cual no recomiendo la verdad, usen PHP puro🫠.

**Nota:** En el repositorio se incluye el archivo [confia.txt](confia.txt), que muestra un ejemplo de cómo desactivar la verificación SSL en el cliente HTTP (se usa `verify => false`). Si se elige este enfoque, será necesario ajustar las rutas de autenticación (por ejemplo `/auth/google/redirect` y `/auth/google/callback`) para integrar el código del ejemplo y adaptarlo al proyecto. Este método evita la necesidad de un certificado, pero es inseguro.

![Prueba](./assets/ssl.gif)


