# SMB Samba 1

Herramienta extra: nmblookup

Para establecer conexiones 'smbclient'


Questions

IP TARGET: 192.42.197.3

Find the default tcp ports used by smbd.
    . Puertos 139,445

Find the default udp ports used by nmbd.
What is the workgroup name of samba server?
    . RECONLABS
Find the exact version of samba server by using appropriate nmap script.
    --script smb-os.discovery  (Este viene en los scripts de enumeracion por defecto)
    Samba 4.3.11
Find the exact version of samba server by using smb_version metasploit module.
    . Abrimos metasploit con 'msfconsole'
    . use auxiliary/scanner/smb/smb_version
    . show options (nos muestra las opciones)
    . Configuramos rhosts
    . Ejecutamos con 'run' o 'exploit'

What is the NetBIOS computer name of samba server? Use appropriate nmap scripts.
Find the NetBIOS computer name of samba server using nmblookup
    . nmblookup -A 192.42.197.3
Using smbclient determine whether anonymous connection (null session)  is allowed on the samba server or not.
Using rpcclient determine whether anonymous connection (null session) is allowed on the samba server or not.
    . rpcclient -U "" -N 192.42.197.3