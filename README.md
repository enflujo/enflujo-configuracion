# Cluster de Raspberry Pi

## Equipos

- Cuatro Raspberry Pi 4.
- Cluster case
- Cuatro USB C
- Disipadores
- Ventiladores.
- Cuatro memorias SD 32GB ScanDisk Ultra serie 10.

## Preparar las memorias SD

Descargar [Raspberry Pi Imager](https://www.raspberrypi.com/software/).

- OS: Raspberry Pi OS Lite (64-bit)

### Activar SSH y nombrar el nodo

- En "Set hostname:" darle un nombre especifico al nodo (cada Raspberry va a ser un nodo en el cluster).
  - La convención acá va a ser: `enflujo1.local`, `enflujo2.local`, `enflujo3.local`, etc.
- Activar SSH.
- Crear nombre de usuario y contraseña. Estos los usamos luego para conectarse por SSH.
- (opcional) Configurar el WiFi donde SSID es el nombre de la red.

![Opciones Avanzadas](./opciones-avanzadas.png)

## Configurar la Raspberry

Poner la memoria SD a la Raspberry y conectarla a corriente. Esperar un momento mientras carga.

```bash
ssh enflujo@enflujo1.local
```

Inicialmente no estamos haciendo cambios a la configuración general, pero para hacerlo:

```bash
sudo raspi-config
```

## ZSH

Para tener un terminal más cómodo.

Actualizar dependencias:

```bash
sudo apt update
```

```bash
sudo apt dist-upgrade --yes
```

Instalar zsh:

```bash
sudo apt install zsh --yes
```

Definir como SHELL predeterminado:

```bash
chsh -s $(which zsh)
```

Salir:

```bash
exit
```

volver a entrar:

```bash
ssh enflujo@enflujo1.local
```
Al reiniciar debe configurarse el zsh. Para ello hay dos opciones:

1) Escribir en el terminal zsh y luego escoger la opcion (2).

2) Al entrar de nuevo escoger la opcion (2) si el menu de opciones aparece automaticamente

> (2) Populate your ~/.zshrc with the configuration recommended
> by the system administrator and exit (you will need to edit
> the file by hand, if so desired).

```bash
2
```

### Instalar Oh-My ZSH

Instalar git

```bash
sudo apt install git --yes
```

```sh (para correr este comando debe estar instalado curl)
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)" 
```

### Plugins ZSH

zsh-autosuggestions

```bash
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

zsh fast syntax highlighting

```bash
git clone https://github.com/zdharma-continuum/fast-syntax-highlighting.git \
  ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/plugins/fast-syntax-highlighting
```

Activar estos plugins:

```bash
sudo nano ~/.zshrc
```

Con el teclado, presionar la fecha de abajo hasta la linea que dice `plugins=(git)` y sumar los plugins que acabamos de descargar:

```bash
plugins=(git zsh-autosuggestions fast-syntax-highlighting)
```

Para [actualizar Oh My ZSH automáticamente](https://github.com/ohmyzsh/ohmyzsh#getting-updates), quitar el comentario `#` en la linea.

```bash
zstyle ':omz:update' mode auto
```

Guardar los cambios con `CTRL+o`.

Salir del editor con `CTRL+x`.

Activar los cambios:

```bash
source ~/.zshrc
```

Listo, ahora al escribir en el terminar deben salir sugerencias al escribir y usar colores que resaltan el texto.

### Configurar Git

Esta configuracion es para todos los repositorios 

```bash
git config --global user.name "nombre.usuario"
```
Confirmar el nombre del usuario:

```bash
git config --global user.name
```

### Almacenar las credenciales de Github en el cache dentro de Git:

Tener instalado Github CLI:

Para Linux (Debian, Ubuntu Linux, Raspberry Pi OS (apt))
```bash
curl -fsSL https://cli.github.com/packages/githubcli-archive-keyring.gpg | sudo dd of=/usr/share/keyrings/githubcli-archive-keyring.gpg
```

```bash
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | sudo tee /etc/apt/sources.list.d/github-cli.list > /dev/null
```

```bash
sudo apt update
```

```bash
sudo apt install gh
```

Luego de tener esto instalado, configuramos nuestro acceso a Github:

```bash
gh auth login 
```

Luego escoger desde cual cuenta queremos hacer el login. Por lo general se escoge desde Github.com. Despues escogemos el protocolo HTTPS. Luego aceptamos la autenticacion con las credenciales de Github y escogemos si se realiza por medio del navegador web o por medio de un token de autenticacion.

Si se escoge la autenticacion por medio del navegador web se pide ingresar el codigo que aparece en este punto de la instalacion. Ingresando este codigo en el navegador la autenticacion queda completa con este mensaje: "logged in as nombre.usuario"


### Instalar Docker usando el repositorio

Configurar el repositorio:

Actualizar apt e instalar los paquetes para que apt pueda utilizar un repositorio sobre HTTPS

```bash
sudo apt-get update
```

```bash
sudo apt install apt-transport-https ca-certificates curl software-properties-common
```
Añadir luego la clave GPC para el repositorio oficial de Docker en el sistema

```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```
Configurar el repositorio estable

```bash
sudo echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

### Instalar Docker Engine

```bash
sudo apt-get update
```
```bash
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin
```
Para asegurar que la instalacion fue exitosa correr el siguiente comando

```bash
sudo docker run hello-world
```

### Instalar Yarn

```bash
sudo apt install yarn
```
### Instalar Node.js

```bash
sudo apt install nodejs
```

### Instalar NPM

```bash
sudo apt install npm
```

### Instalar y actualizar NVM (Node.js Version Manager)

Cambiar v0.35.0 por la ultima version que se quiera instalar (https://github.com/nvm-sh/nvm)

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
```
Para confirmar que la instalacion fue exitosa poner en el terminal:

```bash
command -v nvm
```
La respuesta debe ser: nvm

