### Laboratorio - búsqueda de DNS

Herramientas comunes utilizadas para recopilar información sobre un objetivo a través del sistema de nombres de dominio (DNS).
- nslookup - obtener información de dominio y dirección IP.
- whois - encontrar información de registro adicional.
- comparativa de herramientas nslookup y Dig.
- búsquedas DNS inversas

### Parte 1.
- Apertura de la maquina virtual para el desarrollo del laboratorio de manera optima.

### Parte 2.
- Uso del nslookup -> uso básico, convertir el nombre del dominio en una dirección IP. | Otra función es que proporciona información adicional.
	- Accedemos al manual con el comando `man nslookup` 
	- [manual](screenshots/manual_nslookup.png)

### Paso 3.
- En la terminal usar nslookup, para entrar en modo interactivo y para poder convertir un dominio en IP, ingresar el nombre, por ejemplo cisco.com
- (nslookup_cisco)
- Para encontrar los servidores de nombres de dominio configurados para cisco.com se usa el comando `set type` y si ke agregamos `ns` devolvemos la información del servidor de nombres.
- (settype_ns)

### Paso 4.
- Es conveniente cambiar de servidor DNS para realizar búsquedas. Esto puede ser necesario si le servidor local no puede resolver una dirección o resuelve el nombre de host en una dirección privada interna y necesita obtener la dirección accesible de Internet del host.
	- Usaré la sintaxis del comando de una línea nslookup para cambiar el servidor y buscar netacad.com. Sintaxis a usar `nslookup [nombre de host][IP del servidor]`
	- (netacad_8)
	- En el tipo de consulta `any` puede recuperar gran parte o toda la información contenida en el registro DNS para un nombre de host.
	- (netacad_any)

### Parte 2:  uso de la función whois
La herramienta whois consulta la información de registro de dominio, en lugar de los registros del servidor DNS.
Tener en cuenta que la información de contacto es la del servicio de alojamiento, en lugar de  la organización en sí.

#### Paso 1. Comprar el resultado de whois de varias organizaciones.
- iniciamos con `whois` cisco.com
- (comparacion_whois)

#### Paso2. whois para determinar dirección IP.
- Después de usar la herramienta `nslookup` en cisco, registramos la IP -> 72.163.5.201
- Usamos la herramienta `whois` ingresando la IP obtenida anteriormente.
- Debido a que las organizaciones pueden usar las mismas redes IP para otros servidores externos, conocer los rangos es valioso para determinar a que redes apuntar durante una prueba de penetración.
- (whois_IP)

### Parte 3: Comprar resultados de nslookup y dig

#### Paso 1. Usamos dig para consultar servidores DNS.
La funcion de linux que realiza consultas al DNS. Se parece al nslookup.
- (dig_cisco)
Para obtener la dirección IPv6 de cisco.com, es necesario agregar un tipo a la estructura de comando. el comando es `dig [hostname][record type]`
- (dig_AAAA)

#### Paso 2. Utilice Dig para obtener info adicional.
En la primera parte se uso nslookup para obtener los servidores DNS de cisco.com.
ahora usaré el de google DNS de google 8.8.8.8 para consultar registros del servidor DNS.
La sintasix a usar es `dig [nombre de host] @ [IP del vervidor DNS][tipo]` 
(dig_adicional)

El tipo de registro `any` también se puede consultar mediante dig.
(dig_any)


### Parte 4: Busquedas de DNS inversas.

#### Paso1. uso dig para búsqueda de rDNS
Uso dig para buscar nombres de host adicionales. En la buúqueda de DNS inverso (rDNS) utilizan la dirección IP para consultar los nombres de host de los servicios que se resuelven en esa dirección.

- Introducimos el comando: `dig -x 72.163.5.201` ya que es el registro del servidor DNS de cisco.
- (dig_x)
- ahora consultamos otra IP de la misma red.
- (dig_x2)

#### Paso2. Uso la utilidad de host para realizar búsquedas de rDNS

Realiza búsquedas para convertir direcciones IP en nombres de host.
Utilizamos la utilidad para buscar otro host en la red 72.163.0.0/16
- Usamos la sintaxis `host [dirección IP]`
- (host)
- tambíen se puede usar para realizar una búsqueda rápida de direcciones IP para un nombre de host conocido.
- (host_2)
- La información sobre los alias es útil al intentar determinar dónde se encuentra el sitio web o el servicio real.
