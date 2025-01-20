
<img src="/carpeta-imagenes/rpi5cover.png" alt="rpi5" style= "height: 500px;"/>

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

- En "Set hostname:" darle un nombre específico al nodo (cada Raspberry va a ser un nodo en el cluster).
  - La convención acá va a ser: `enflujo1.local`, `enflujo2.local`, `enflujo3.local`, etc.
- Activar SSH.
- Crear nombre de usuario y contraseña. Estos los usamos luego para conectarse por SSH.
- (opcional) Configurar el WiFi donde SSID es el nombre de la red.

<img src="/carpeta-imagenes/opciones-avanzadas.png" alt="require config p" style="height: 800px;"/>

## Configurar la Raspberry

Poner la memoria SD a la Raspberry y conectarla a corriente. Esperar un momento mientras carga.

```bash
ssh enflujo@enflujo1.local
```

Inicialmente no estamos haciendo cambios a la configuración general, pero para hacerlo:

```bash
sudo raspi-config
```
