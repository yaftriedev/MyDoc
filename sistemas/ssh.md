# Comandos Básicos Cliente
```bash
# Conectarse a un pc
ssh user@ip
ssh -p <puertp> usuario@IP
ssh <ip-guardadas>
ssh -i /ruta/clave usuario@IP

# Generar Claves SSH
ssh-keygen -t ed25519
ssh-copy-id -i /ruta/clave usuario@IP
```
# Guardar Hosts `.ssh/config`
```
Host <nombre>  
       HostName <IP/Dominio>
       User <usuario>
       IdentityFile </ruta/clave>  
...
```
# Configuración y Instalación Servidor
```bash
# Instalar SSH Server
sudo apt install openssh-server

# Configuraciones utiles en /etc/ssh/sshd_config
Port 22  
ListenAddress 0.0.0.0  
PermitRootLogin prohibit-password  
PubkeyAuthentication yes  
PasswordAuthentication yes  
PermitEmptyPasswords no  
UsePAM yes
```