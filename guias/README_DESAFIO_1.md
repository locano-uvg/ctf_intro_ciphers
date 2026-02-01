# Desafío 1: Logs y Configuración

## 🚀 Acceso al Desafío

Para acceder al contenedor Docker de este desafío, ejecuta el siguiente comando:

```bash
docker exec -it challenge1_ctf bash
```

Una vez dentro del contenedor, podrás comenzar a explorar el sistema y buscar las flags ocultas.

## 📚 Documentación General

Para más información sobre el proyecto, instalación y configuración, consulta el [README principal del repositorio](../../README.md).

---

## 📝 Descripción
Revisa archivos del sistema y logs para encontrar información oculta y flags. Aprende a navegar por directorios y descubrir secretos escondidos en archivos de configuración.

## 🎯 Objetivo
Encontrar flags ocultas en archivos del sistema, logs y configuraciones.

## 💡 Tips Generales

### 1. Explora los archivos del sistema
Muchas pistas pueden estar escondidas en lugares comunes:

- **Mensajes del sistema**: Los administradores a veces dejan mensajes útiles o pistas
  - Revisa el archivo `/etc/motd` (Mensaje del Día)
  
- **Logs de autenticación**: Pueden contener información histórica útil
  - Examina `/var/log/auth.log` para identificar intentos de acceso o información sospechosa
  
- **Archivos de configuración ocultos**: Busca en directorios como `/etc` o carpetas específicas de usuarios
  - Los archivos que comienzan con punto (`.`) son ocultos y no se muestran con `ls` normal

### 2. Identifica usuarios del sistema
```bash
# Ver todos los usuarios
cat /etc/passwd

# Identificar usuarios con shell de acceso
cat /etc/passwd | grep -E "/bin/(bash|sh)"
```

### 3. Explora directorios de usuarios
```bash
# Listar directorios en /home
ls -la /home/

# Para cada usuario encontrado, explorar su directorio
ls -la /home/<usuario>/

# Buscar archivos ocultos
find /home -name ".*" -type f 2>/dev/null
```

### 4. Busca archivos con nombres sospechosos
```bash
# Buscar archivos que puedan contener flags
find / -name "*flag*" -o -name "*.flag" -o -name ".hidden" -o -name ".instrucciones" 2>/dev/null
```

### 5. Revisa archivos de configuración
```bash
# Buscar en directorios comunes
cat /etc/hostname
cat /etc/hosts
cat /etc/resolv.conf

# Buscar archivos de configuración ocultos
find /etc -name ".*" -type f 2>/dev/null
```

## 🔍 Comandos Útiles

```bash
# Buscar texto en archivos
grep -r "flag" /etc/ 2>/dev/null
grep -r "FLAG" /home/ 2>/dev/null

# Ver historial de comandos (si existe)
cat ~/.bash_history

# Ver permisos de archivos
ls -l /ruta/al/archivo
```

## ⚠️ Recordatorios Importantes

1. **Archivos ocultos**: Los archivos que comienzan con punto (`.`) no se muestran con `ls` normal, usa `ls -la`
2. **Permisos**: Si no puedes leer un archivo, verifica los permisos con `ls -l`
3. **Búsqueda recursiva**: Usa `find` con `2>/dev/null` para evitar errores de permisos
4. **Logs**: Los logs pueden contener información histórica útil

---

**¡Buena suerte resolviendo el desafío!** 🚀
