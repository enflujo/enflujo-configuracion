<img src="/carpeta-imagenes/docker.png" alt="rpi5" style= "height: 250px;"/>

# Instalar Docker usando el repositorio

Antes de instalar Docker Engine por primera vez en una nueva máquina es necesario configurar el repositorio de Docker. Luego es posible instalar y actualizar Docker desde su repositorio.

**Configurar el repositorio:**

Actualizar apt e instalar los paquetes para que apt pueda utilizar un repositorio sobre HTTPS

```bash
sudo apt-get update
```

```bash
sudo apt install apt-transport-https ca-certificates curl software-properties-common
```

**Añadir luego la clave GPC para el repositorio oficial de Docker en el sistema:**

```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

**Configurar el repositorio estable:**

```bash
sudo echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

## Instalar Docker Engine

```bash
sudo apt-get update
```

```bash
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin
```

**Para asegurar que la instalación fue exitosa correr el siguiente comando:**

```bash
sudo docker run hello-world
```

## Post-instalacion de Docker

Para evitar poner siempre en la terminal `sudo` antecediendo al comando `docker` debemos crear un grupo Unix llamado docker y agregar posteriormente los usuarios.

**Pasos para crear el grupo:**

1. Crear el grupo:

```bash
 sudo groupadd docker
```

2.  Agregar nuestro usuario al grupo:

```bash
 sudo usermod -aG docker $USER
```

3. Activar los cambios en el grupo:

```bash
 newgrp docker
```

4. Verificar que podemos correr docker sin sudo:

```bash
 docker run hello-world
```

### Configurar Docker para que se inicie al prender el computador
La mayoría de distribuciones de Linux (RHEL, CentOS, Fedora, Debian, Ubuntu 16.04 y superiores) usan systemd para controlar qué servicios se inician cuando se prende el computador. En Debian y Ubuntu el servicio de Docker está configurado para iniciar por defecto. Para iniciar Docker y Containerd al prender el computador en otras distribuciones se usan los siguientes comandos:

```bash
 sudo systemctl enable docker.service

 sudo systemctl enable containerd.service
```

Para desactivar este comportamiento se usa el mismo comando pero con *disable*.

```bash
 sudo systemctl disable docker.service

 sudo systemctl disable containerd.service
