\### Práctica de laboratorio - Búsqueda de información a partir de certificados SSL



En esta practica de laboratorio se alcanzarán los siguientes objetivos:

\- Ver información de certificados en hosts

\- Acceder a la información detallada del certificado

\- Usar herramientas de escaneo de SSL en Kali

\- Usar las herramientas de Kali para recopilar información del certificado



\## Parte 1: Ver información del certificado en hosts



\#### Paso1. Ver certificados de un sitio desde un navegador.

\- En la mayoría de los navegadores aparece un candado al lado de la URL. Explorar las configuraciones disponibles.

\- Se puede ver los certificados de sitio web desde las mismas opciones.

\- (certificados)



\#### Paso2. Ver los certificados almacenados en el SO.

\- Para ver los certificados de windows usamos el comando `certmgr.msc` en el buscador de windows.

\- Y en kali se usa `/usr/share/ca-certificates/mozilla`

\- (Certificado Kali)

\- Para acceder a la información sobre certificados raíz e intermedio de confianza podemos usa entrar en la siguiente ruta de kali \*\*/usr/share/ca-certificates/mozilla.\*\* y para poder enumerar los archivos de certificados raíz \*\*ls -l | grep root\*\*



\## Parte 2. Acceda a información detallada del certificado en línea



Se puede acceder a los registros de CT (Transparencia de certificados) a través de varios servidores de registros de CT y API. También hay varias herramientas de monitoreo de TC disponibles, como CertSpotter y Censys, que pueden ayudar a automatizar el proceso de monitoreo de registros de TC para dominios específicos o certificados SSL/TLS



\## Parte 3. Uso de las herramientas de escaneo de SSL en KALI.



\#### Paso 1: Investigar las herramientas de KALI

\- Buscamos en Kali el termino de SSL.



\### Parte 4. Usar las herramientas de Kali para recopilar información del certificado



\- El sslscan es una herramienta de reconocimiento de kali que recopila información sobre los certificados SSL asociados con los dominios. 

\#### Paso 1. Instalar aha.



la aplicación \*\*aha\*\* crea un archivo HTML estándar que captura la salida de los comandos del terminal en archivos HTML estándar. \*\*Aha\*\* captura cualquier código de color y formato básico de la salida del comando.



\- actualizamos la información del paquete de apto con el comando `apt update`.

\- Intalamos \*\*Aha\*\* con el comando `sudo apt install -y aha`



\#### Paso 2. Ejecutar sslscan y guarde el resultado en un archivo HTML.

\- Desde la terminal ejecutar el siguiente comando + la pagina objetivo `sslscan "pagina objetivo"`

\- (sslscan)

\- Después de una demora se verá los resultados del escano.

\- La salida esta códificada por colores para facilitar la interpretación de la gravedad de los Problemas detectados. Significado de colores:

&#x09;- Texto de fondo rojo: cifrado NULO. No se utilizó cifrado.

&#x09;- Rojo: cifrado roto (menor o igual a 40 bits), protocolo vulnerable o roto como SSLv2 o SSLv3 o algoritmo de firma de certificados roto como MD5.

&#x09;- Amarillo: cifrado débil (menor o igual a 56 bits) o algoritmo de firma débil, como SHA-1.

&#x09;- Violeta: cifrado anónimo, como ADH o AECDH.

\- Si bien sslscan ofrece opciones para generar resultados en formatos de archivo de texto o XML, \*\*aha\*\* proporciona la legibilidad de HTML y la preservación de la codificación de colores. 

\- Para esto, canalizamos la salida del comando \*\*sslscan\*\* a \*\*aha\*\* y luego redirija la salida de \*\*aha\*\* a un archivo HTML

