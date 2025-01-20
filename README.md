# CrudGridView
Crud en GridView usando webforms
Entiendo, a veces trabajar con archivos PFX puede ser complicado. Vamos a intentar otra forma de extraer la clave privada y luego crear el archivo P12.

1. Primero, extrae la clave privada del archivo PFX. Usa el siguiente comando:

    ```sh
    openssl pkcs12 -in tu_archivo.pfx -nocerts -out clave_privada.pem
    ```

   **Nota**: Este comando te pedirá la contraseña del archivo PFX y luego te pedirá que ingreses una contraseña nueva para proteger la clave privada extraída. Asegúrate de recordar esta nueva contraseña.

2. A continuación, convierte la clave privada al formato RSA (si es necesario):

    ```sh
    openssl rsa -in clave_privada.pem -out clave_privada_rsa.pem
    ```

   Este comando te pedirá la contraseña que usaste en el paso anterior para la clave privada extraída.

3. Extrae el certificado del archivo PFX:

    ```sh
    openssl pkcs12 -in tu_archivo.pfx -clcerts -nokeys -out certificado.pem
    ```

4. Finalmente, crea el nuevo archivo P12 con la clave privada y el certificado extraídos:

    ```sh
    openssl pkcs12 -export -out nuevo_archivo.p12 -inkey clave_privada_rsa.pem -in certificado.pem
    ```

Espero que estos pasos te ayuden a resolver el problema. Si encuentras algún error o necesitas más ayuda, ¡no dudes en decírmelo!
