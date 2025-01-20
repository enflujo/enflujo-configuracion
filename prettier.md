![Node JS](./carpeta-imagenes/prettier.png)
# Configuración de Prettier en VS Code

## Paso 1: Abrir preferences
- En MAC: command + shift + p 
- Windows/ Linux: control + shift + p
- Hacer click en "Preferences: Open Settings (UI)"

<img src="/carpeta-imagenes/command-shift1.png" alt="command shift p"/>

## Paso 2: Require Config
- Buscar: "Require config" en Preferences
- Hacer click en donde dice "Prettier: Require Config" para activar el chulito.

<img src="/carpeta-imagenes/require-config1.png" alt="require config p"/>

## Paso 3: Format On Save
- Buscar: "Format On Save" en Preferences
- Hacer click en donde dice "Format On Save" para activar el chulito.

<img src="/carpeta-imagenes/format-save.png" alt="format save p"/>

## Paso 4: Default Formatter
- Buscar: "Formatter" en Preferences
- Hacer click en donde dice "Default formatter"
- Seleccionar la opción que dice "Prettier - Code formatter"
<img src="/carpeta-imagenes/default-format.png" alt="default format"/>

## Paso 5: Si estás usando Astro

### 5.1
- En MAC: command + shift + p 
- Windows/ Linux: control + shift + p
- Hacer click en "Preferences: Open User Settings (JSON)

<img src="/carpeta-imagenes/buscar-json1.png" alt="default format"/>
### 5.2
- Agregar adentro del JSON:
  
```
"[astro]": {
    "editor.defaultFormatter": "astro-build.astro-vscode"
  }
```
  
