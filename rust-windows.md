# Rust en Windows + Powershell 7 + VSCode

## Instalar Rust

Correr este comando y seleccionar la opción predeterminada (1)

```sh
Invoke-WebRequest -Uri https://win.rustup.rs -OutFile rustup-init.exe; Start-Process -FilePath rustup-init.exe -Wait; Remove-Item rustup-init.exe
```

Esto instala:

- El compilador: `rustc`.
- El gestor de paquetes: `Cargo`
- Gestor de versiones: `rustup`

En VSCode instalar las extensiones:

- Rust Analyzer (configurar el JSON según las instrucciones que aparecen cuando se instala).
- CodeLLDB: Para depurar Rust.
- Even Better TOML: Para trabajar los archivos `.toml`.
- Dependi: Para revisar dependencias.
- Rustfmt: para formatear Rust

En la configuración del tema de oh-my-posh, incluir en la sección de `segments[]`:

```json
{
  "type": "command",
  "command": "rustc --version",
  "style": "powerline",
  "foreground": "cyan",
  "background": "black"
}
```

## Crear un nuevo proyecto de Rust

```sh
cargo new enflujo-esp32-camara-rust
cd enflujo-esp32-camara-rust
```

Instalar paquetes de utilidad

`cargo-watch` para compilar pruebas al guardar

```sh
cargo install cargo-watch
```

se ejecuta con

```sh
cargo watch -x run
```

Para usar el lint de Rust

```sh
rustup component add clippy
```

```sh
cargo clippy
```

Formatear código

```sh
rustup component add rustfmt
```

```sh
cargo fmt
```
