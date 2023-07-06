# SMB:Nmap Scripts

Vamos a utilizar ciertos scripts de nmap para encontrar informacion adicional que nos ayude en la enumeración

Escaneo básico con 'nmap'

Vemos en el puerto 445 el servicio microsoft-ds (SMB)

Ahora vamos a centrarnos en el puerto 445
Comando: 'nmap -p445 --script smb-protocols 10.2.16.247'

Con esto utilizamos el script smb-protocols, que nos arroja info sobre la version de SMB

**Todos los scripts de nmap estan en /usr/share/nmap/scripts**

Otro script que utiliza en el video es 'smb-security-mode'

Se ve que se utiliza una cuenta de tipo *guest*, y que la firma de mensajes está deshabilitada.
Por esto y tambien anteriormente mostrar como posible version la V1, puede indicar que es una configuración
por defecto, lo cual lo hace peligroso.


**smb-enum-sessions** -> Nos arroja info sobre las sesiones activas

Este script (y otros tambien) tiene argumentos que se le pueden pasar. En este caso probamos
'nmap -p445 --script smb-enum-sessions --script-args smbusername=administrator,smbpassword=smbserver_771'

Las credenciales nos las dan en la info del laboratorio

**smb-enum-shares** -> Nos da información de las unidades que se están compartiendo

**smb-enum-shares** -> Info de los usuarios que existen. En este caso si lo lanzamos sin autenticar, no nos da info

**smb-server-stats** -> Estadisticas del servidor. Logs...etc

**smb-enum-domains**

**smb-enum-groups** -> Enumera grupos

**smb-enum-services**

**smb-enum-ls** -> Hace como un ls, es decir, lista los directorios de las unidades que están compartidas