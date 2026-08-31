# Práctica 3: Configuración Controlada - Práctica de Alias (Diapositiva 15)
**Universidad Autónoma de Zacatecas**  
**Ingeniería de Software**  

---

## 1. Investigación del Comando para Listar Todos los Alias

En entornos basados en sistemas Unix/Linux (como Bash), el comando nativo utilizado para mostrar todos los alias activos definidos en la sesión actual es simplemente:

```bash
alias

Paso 01: Búsqueda previa de duplicados en ~/.bashrc
Antes de agregar un nuevo alias de forma arbitraria, es una buena práctica comprobar si ya existe una definición previa para evitar redundancias o conflictos en la configuración. Para ello, utilizamos grep

grep -n "alias ll=" ~/.bashrc

Paso 02 y 03: Inserción controlada y recarga de configuración
Una vez verificado el archivo, agregamos la nueva definición del alias ll con soporte de formato extendido y color (ls -lah --color=auto) al final del archivo ~/.bashrc, aplicando enseguida el comando source para recargar la sesión actual sin necesidad de abrir una nueva terminal

printf "%s\\n" "alias ll='ls -lah --color=auto'" >> ~/.bashrc
source ~/.bashrc

Paso 04: Verificación del tipo y expansión del alias
Para confirmar que el alias se ha cargado correctamente y verificar su comportamiento actual, utilizamos el comando type

type ll


Como complemento práctico propuesto en la interfaz de la diapositiva, se estructuró un alias personalizado llamado cduaz para navegación rápida hacia el directorio de trabajo del laboratorio:

Nombre: cduaz

Expansión: cd ~/laboratorio-cli

printf "%s\\n" "alias cduaz='cd ~/laboratorio-cli'" >> ~/.bashrc
source ~/.bashrc
cduaz
pwd