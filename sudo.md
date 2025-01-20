# Configurar SUDO para que no exija el password

**1. Acceder al archivo /etc/sudoers**

```bash
sudo visudo
```

**2. Ir al final del archivo `/etc/sudoers` y agregar la siguiente linea**

```bash
`suNombreDeUsuario` ALL=(ALL) NOPASSWD:ALL
```
