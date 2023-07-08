# SMBMap

Herramienta escrita en python

'smbmap -u usuario -p "passwd" -d directorio -H target'

Todas las utilidades de smbmap las podemos chequear con el flag -h

Una muy útil es la de subir y descargar documentos del directorio remoto

smbmap -H host --upload SRC DEST
smbmap -H host --download SRC
smbmap -H host -R DIR -> Esto lista un directorio de manera recursiva

