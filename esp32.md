<img src="/carpeta-imagenes/esp32.png" alt="rpi5" style= "height: 250px;"/>

# ESP32

## WIFI ESP-WROM 32

En el Laboratorio tenemos varias placas ESP-WROM 32. A continuación la configuración de estas para programarlas

### Configurar Arduino IDE para programar la placa

Agregar lista de placas de **espressif** a Arduino IDE

En Archivo -> Preferencias agregar el siguiente enlace en el campo de texto sobre placas adicionales.

```sh
https://dl.espressif.com/dl/package_esp32_index.json
```

En _Board Manager_ instalar las placas esp32. IMPORTANTE instalar la que dice "by Espressif Systems"

### Drivers CP210x

En algunos sistemas operativos hay que instalar los drivers para la USB.

Descarga: https://www.silabs.com/developer-tools/usb-to-uart-bridge-vcp-drivers?tab=downloads

En Windows por ejemplo, esta se instala así: https://www.youtube.com/watch?v=r_eMEXvt0v0

En la lista de placas, usar: **"EP·" Dev Module"**

### Probar

Para probar que este todo bien, se puede usar un programa simnple que prende y apaga el LED integrado de la placa:

```cpp
int ledIntegrado = 2;

void setup() {
  pinMode (ledIntegrado, OUTPUT);
}


void loop() {
  digitalWrite(ledIntegrado, HIGH);
  delay(1000);
  digitalWrite(ledIntegrado, LOW);
  delay(1000);
}
```

## ESP32-CAM

## ESP32 con pantalla OLED

https://www.electronicshub.org/esp32-oled-display/
