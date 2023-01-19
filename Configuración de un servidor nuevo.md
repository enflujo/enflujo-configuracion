# Configuración de un servidor nuevo

## Crear usuario sudo

Acceder al servidor como `root`.

Crear primero el usuario

```bash
adduser enflujo
```

Agregar usuario a grupo sudo:

```bash
usermod -aG sudo enflujo
```

Comprobar que el nuevo usuario pertenece al grupo sudo:

```bash
id enflujo
```

Debe mostrar algo como esto

```bash
uid=1000(enflujo) gid=1000(enflujo) groups=1000(enflujo),27(sudo)
```

### No pedir clave en comandos sudo

```bash
sudo visudo
```

Al final del archivo, agregar:

```bash
enflujo ALL=(ALL) NOPASSWD:ALL
```

Guardar cambios con CTR + o y salir con CTRL + x

### Copiar llave de ssh para acceder sin escribir la clave

```bash
ssh-copy-id -i ~/.ssh/id_rsa.pub enflujo@ip.del.servidor
```

Comprobar que se puede acceder entrando normalmente con:

```bash
ssh enflujo@ip.del.servidor
```

No deberías pedir la clave.

### ZSH

sacar de https://github.com/enflujo/enflujo-configuracion

### Instalar docker

Seguir instrucciones actualizadas en https://docs.docker.com/engine/install/ubuntu/

Y seguir instrucciones para no usar sudo con docker: https://docs.docker.com/engine/install/linux-postinstall/

### Instalar nodejs con NVM

https://github.com/nvm-sh/nvm

1. Instalar con curl ...
2. `source ~/.zshrc`
3. nvm install --lts

Para actualizar node en NVM más adelante cuando cambia LTS

```bash
nvm install --lts --reinstall-packages-from=current
```

### Instalar Yarn

```bash
npm i -g yarn
```

### Nginx
https://www.digitalocean.com/community/tutorials/how-to-install-nginx-on-ubuntu-22-04

### SSL con Letsencrypt
https://www.digitalocean.com/community/tutorials/how-to-secure-nginx-with-let-s-encrypt-on-ubuntu-22-04