<img src="/carpeta-imagenes/zsh.png" alt="zsh" style= "height: 400px;"/>

# ZSH

Para tener un terminal más cómodo con colores.

**Actualizar dependencias:**

```bash
sudo apt update
```

```bash
sudo apt dist-upgrade --yes
```

**Instalar zsh:**

```bash
sudo apt install zsh --yes
```

***Definir como SHELL predeterminado:***

```bash
chsh -s $(which zsh)
```

***Salir:***

```bash
exit
```

***volver a entrar:***

```bash
ssh enflujo@enflujo1.local
```

### Al reiniciar debe configurarse el zsh. Para ello hay dos opciones:

1. Escribir en el terminal zsh y luego escoger la opción (2).

2. Al entrar de nuevo escoger la opción (2) si el menú de opciones aparece automáticamente

> (2) Populate your ~/.zshrc with the configuration recommended
> by the system administrator and exit (you will need to edit
> the file by hand, if so desired).

```bash
2
```

## Instalar Oh-My ZSH

### Instalar git

```bash
sudo apt install git --yes
```

```sh (para correr este comando debe estar instalado curl)
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

### Plugins del ZSH

**zsh-autosuggestions**

```bash
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

**zsh fast syntax highlighting**

```bash
git clone https://github.com/zdharma-continuum/fast-syntax-highlighting.git \
  ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/plugins/fast-syntax-highlighting
```

**Powerlevel10k**

1. Instalar las fuentes:

   [MesloLGS NF Regular.ttf](https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Regular.ttf)
   [MesloLGS NF Bold.ttf](https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Bold.ttf)
   [MesloLGS NF Italic.ttf](https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Italic.ttf)
   [MesloLGS NF Bold Italic.ttf](https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Bold%20Italic.ttf)

2. Escoger las fuentes desde el terminal. Abrir Terminal → Preferencias y escoger el profile predeterminado. Escoger luego `custom fonts` (activarlo si aun no lo está) y escoger `MesloLGS NF Regular`.

### Hacer lo siguiente para configurar las fuentes en VS Code:

Abrir File → Preferences → Settings (PC) o Code → Preferences → Settings (Mac), escribir `terminal.integrated.fontFamily` en la caja de búsqueda y poner el nombre de la fuente: `MesloLGS NF`. Para ver los cambios es necesario reiniciar VS Code.

3. Instalar el tema en sí mismo:

3.a. Clonar el repositorio:

```bash
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```

3.b. Poner el tema dentro del archivo `~/.zshrc` (para abrir este archivo seguir las instrucciones abajo "Activar estos plugins")

```bash
ZSH_THEME="powerlevel10k/powerlevel10k"
```

4. Reiniciar zsh

```bash
exec zsh
```

5. Configurar el tema. Escribir lo siguiente en la consola si no aparece automáticamente:

```bash
p10k configure
```

## Activar los plugins:

```bash
sudo nano ~/.zshrc
```

Con el teclado, presionar la fecha de abajo hasta la línea que dice `plugins=(git)` y sumar los plugins que acabamos de descargar:

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

Listo, ahora al escribir en el terminar deben salir las sugerencias al escribir y usar colores que resaltan el texto.
