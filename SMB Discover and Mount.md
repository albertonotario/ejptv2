# Parte de Explicacion y Laboratorio para descubrir servicios de SMB



Lo primero: Ojo con las mascaras de subred, que no siempre son 255.255.255.255
En este caso es 255.255.240.0 -> esto nos indica que tenemos 8 0's + 4 0's del 240 -> en total 12, por lo tanto
el numero de bits fijos de redes (los que están a 1) son 32-12 =20.

Para hacer el un escaneo de puertos con nmap sobre hosts conectados, utilizaremos entonces IP/20


Comando: 'nmap 10.2.29.0/20 -T4 --open'    -> Nos va a descubrir hosts conectados, va a analizar los puertos tipicos
y a parte, solo nos va a mostrar los que esten en estado "open".

Los puertos 135,139,445 son tipicos de maquinas Windows

El puerto donde se encuentra SMB es en el 445

Ahora procedemos a hacer un escaneo de versiones, directamente a la IP del host conectado -> **10.2.30.188**

Comando: 'nmap 10.2.30.188 -sV -O' -> Con esto descubrimos las versiones de los servicios que corren en los puertos
de la maquina, y también intenta averiguar el SO de la máquina

Ahora añadimos el flag -sC, que utilizará unos scripts básicos de reconocimiento

Comando: 'nmap 10.2.30.188 -sV -sC'

Por otro lado, SMB se ve en el curso que lo que hace es conectar discos en red, tipico en empresas. Pudiendo mapear el contenido de un disco de una maquina en la nuestra

Para crear conexiones en PowerShell: 'net use Z: \\IP\c'