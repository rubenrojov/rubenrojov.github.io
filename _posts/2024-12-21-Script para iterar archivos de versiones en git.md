---
layout: post
author: Ruben Rojo
---
# Script para iterar archivos de versiones en git

El script versionar_archivos.sh` es un script Bash que automatiza el proceso de versionado de tus archivos. Con este script, puedes facilmente crear nuevas versiones de tus archivos y actualizar el control de versiones de tu proyecto.

## Cómo funciona:
-----------------

El script verifica si se ha pasado el nombre del archivo como argumento. Si no se proporciona, muestra un mensaje de error y termina. Luego, asegura que estés en la rama correcta (`main`) y comienza a iterar sobre los archivos de versiones con el patrón basado en el nombre del archivo.

Por cada versión encontrada, renombra el archivo de la versión actual al nombre base, lo agrega al control de versiones, hace un commit con un mensaje adecuado y sube el cambio al repositorio remoto.

```bash 
#bin/bash

# Verificar si se ha pasado el nombre del archivo como argumento
if [ -z "$1" ]; then
    echo "Por favor, proporciona el nombre del archivo"
    exit 1
fi

# Nombre del archivo base (sin versión)
archivo_base=$1

# Asegúrate de estar en la rama correcta
git checkout main

# Iterar sobre los archivos de versiones, usando el patrón basado en el nombre del archivo
for version in $(ls ${archivo_base}*.py | sort -V); do
    # Renombrar el archivo de la versión actual a el nombre base
    mv "$version" "${archivo_base}.py"

    # Añadir el archivo al control de versiones
    git add "${archivo_base}.py"

    # Hacer el commit con el mensaje adecuado
    git commit -m "Versión de ${archivo_base}.py: $version"

    # Subir el commit al repositorio remoto
    git push origin main
done

# Mensaje final
echo "Proceso de versionado y commit completo para ${archivo_base}.py."
```
