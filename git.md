<img src="/carpeta-imagenes/git.png" alt="git" />

# Configurar Git

Esta configuración es para todos los repositorios

```bash
git config --global user.name "nombre.usuario"
```

**Confirmar el nombre del usuario:**

```bash
git config --global user.name
```

**Confirmar el email del usuario:**

```bash
git config --global user.email
```

### Almacenar las credenciales de Github en el cache dentro de Git:

**Tener instalado Github CLI:**

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

**Luego de tener esto instalado, configuramos nuestro acceso a Github:**

```bash
gh auth login
```

Escogemos después la cuenta desde donde queremos loguearnos. Por lo general se escoge desde Github.com. Después escogemos el protocolo HTTPS. Luego aceptamos la autenticación con las credenciales de Github y escogemos si se realiza por medio del navegador web o por medio de un token de autenticación.

Si se escoge la autenticación por medio del navegador web es necesario ingresar el codigo que aparece en este punto de la instalación. Ingresando este código en el navegador la autenticación queda completa con este mensaje: "logged in as nombre.usuario"
