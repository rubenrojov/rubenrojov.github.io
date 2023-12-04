---
layout: post
author: Ruben Rojo
---
# Creando Espacio en Linux: 5 Tips Útiles

Linux es conocido por su **estabilidad y rendimiento**, pero a veces el espacio en disco puede convertirse en un recurso preciado. Aquí tienes cinco consejos para liberar espacio y mantener tu sistema funcionando sin problemas.

1. Elimina archivos de registro antiguos en /var/log.
```bash
sudo find /var/log -type f -name "*.log" -exec rm -f {} \;
```
2. Limpia los cachés de paquetes descargados por APT.
```bash
sudo apt-get clean
```
3. Elimina paquetes instalados como dependencias y ya no necesarios.
```bash
sudo apt-get autoremove
```
4.Borra archivos temporales en /tmp que no se han accedido en los últimos 7 días.
```bash
sudo find /tmp -type f -atime +7 -exec rm {} \;
```
5. Y un comando que proporciona una visión general del uso de disco en los directorios de nivel superior.
```bash
du -h --max-depth=1 /
```

¡Espero que estos consejos te ayuden a liberar espacio en tu sistema Linux! Mantén tu sistema optimizado para un rendimiento máximo.
