# 🔧 Solución a Errores Comunes en C++ con VSCode: Configuración JSON y Depuración


Error comun a la hora de compilar en c++ en visual code debido a error lauch.json

[![Licencia MIT](https://img.shields.io/badge/Licencia-MIT-blue)](LICENSE)
[![GitHub Issues](https://img.shields.io/github/issues/tu-usuario/solucion-errores-cpp-vscode)](https://github.com/tu-usuario/solucion-errores-cpp-vscode/issues)

Guía completa para configurar un entorno de desarrollo en C++ con Visual Studio Code en Windows, incluyendo solución a errores de configuración JSON, depuración con GDB y compilación.

## 📚 Tabla de Contenidos
1. [Requisitos](#-requisitos)
2. [Instalación de Herramientas](#-instalación-de-herramientas)
3. [Configuración de Variables de Entorno](#-configuración-de-variables-de-entorno)
4. [Configuración del Proyecto](#-configuración-del-proyecto)
5. [Compilación y Ejecución](#-compilación-y-ejecución)
6. [Depuración](#-depuración)
7. [Estructura del Proyecto](#-estructura-del-proyecto)
8. [Solución de Errores](#-solución-de-errores)
9. [Contribuciones](#-contribuciones)

---

## ⚙️ Requisitos
- Windows 10/11
- 2 GB de espacio libre
- Conexión a internet para descargas

---

## 📥 Instalación de Herramientas

### 1. Instalar MSYS2 y GCC/GDB
```bash
# Descarga MSYS2 desde: https://www.msys2.org/
# Ejecuta en MSYS2 MinGW 64-bit:
pacman -Syu
pacman -Su
pacman -S mingw-w64-x86_64-gcc mingw-w64-x86_64-gdb
```
### 2.  Instalar Visual Studio Code
```bash
nstalar Visual Studio Code
Descarga desde code.visualstudio.com

Instala la extensión C/C++ de Microsoft.
```
### 3. Instalar Git
```bash
# Descarga Git desde: https://git-scm.com/
# Configura tu usuario:
git config --global user.name "Tu Nombre"
git config --global user.email "tu@email.com"
```
### 4. Configuración de variables de Entorno ( Es muy importante esto )
```bash
Abre Editar variables de entorno del sistema.

En Variables del sistema, edita Path:

Copy
C:\msys64\mingw64\bin
C:\msys64\usr\bin
Verifica en PowerShell:

powershell
Copy
g++ --version  # Debe mostrar GCC 14.2.0 o superior
gdb --version   # Debe mostrar GDB 13.2 o superior
```
### 5. Configuracion de proyecto
```bash
1. Clonar el Repositorio
bash
Copy
git clone https://github.com/tu-usuario/solucion-errores-cpp-vscode.git
cd solucion-errores-cpp-vscode
2. Configurar .vscode/
tasks.json:

json
Copy
{
  "version": "2.0.0",
  "tasks": [{
    "label": "build",
    "type": "shell",
    "command": "g++",
    "args": ["${file}", "-o", "${workspaceFolder}/build/${fileBasenameNoExtension}.exe"],
    "group": { "kind": "build", "isDefault": true }
  }]
}
launch.json:

json
Copy
{
  "version": "0.2.0",
  "configurations": [{
    "name": "Depurar C++",
    "type": "cppdbg",
    "request": "launch",
    "program": "${workspaceFolder}/build/${fileBasenameNoExtension}.exe",
    "miDebuggerPath": "C:/msys64/mingw64/bin/gdb.exe",
    "externalConsole": true
  }]
}
```
### 6. Compilacion y Ejecucion
```bash
Abre un archivo .cpp en VSCode.

Compila con Ctrl + Shift + B.

Ejecuta en PowerShell:

powershell
Copy
./build/tu_archivo.exe
```
### 7. Depuracion
```bash

🐞 Depuración
Establece breakpoints en tu código.

Presiona F5 para iniciar depuración.

Usa la consola externa para entrada/salida.
```
### 8. 📂 Estructura del Proyecto
```bash

solucion-errores-cpp-vscode/
├── .vscode/          # Configuraciones de VSCode
├── src/              # Código fuente (.cpp)
├── build/            # Ejecutables generados (ignorados por Git)
├── .gitignore        # Archivos a ignorar
└── README.md         # Esta documentación
```
### 9. ❗ Solución de Errores Comunes

```bash

Error: undefined reference to...
Causa: Funciones declaradas pero no definidas.
Solución:

bash
Copy
# Asegúrate de compilar todos los archivos .cpp:
g++ src/archivo1.cpp src/archivo2.cpp -o build/ejecutable.exe
Error: g++ no reconocido
Solución: Verifica las variables de entorno y reinicia VSCode.
```
