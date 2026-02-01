# Desafío 2: Codificación Base64

## 🚀 Acceso al Desafío

Para acceder al contenedor Docker de este desafío, ejecuta el siguiente comando:

```bash
docker exec -it challenge2_ctf bash
```

Una vez dentro del contenedor, podrás comenzar a explorar el sistema y buscar las flags ocultas.

## 📚 Documentación General

Para más información sobre el proyecto, instalación y configuración, consulta el [README principal del repositorio](../../README.md).

---

## 📝 Descripción
Aprende a identificar y decodificar cadenas en formato Base64 para revelar información oculta. Domina una de las técnicas de codificación más utilizadas en CTF.

## 🎯 Objetivo
Identificar y decodificar cadenas Base64 para encontrar flags.

## 💡 Tips Generales

### 1. Identifica cadenas Base64
Base64 se caracteriza por usar caracteres: `A-Z`, `a-z`, `0-9`, `+`, `/` y `=` para padding.

**Características:**
- Las cadenas Base64 suelen terminar con `=` o `==` (padding)
- Base64 aumenta el tamaño del texto original en aproximadamente 33%
- Solo usa caracteres alfanuméricos y los símbolos `+` y `/`

```bash
# Buscar posibles cadenas Base64 en archivos
grep -rE "^[A-Za-z0-9+/]+={0,2}$" /ruta/busqueda 2>/dev/null

# Buscar en archivos de texto
find / -type f -name "*.txt" -exec grep -lE "[A-Za-z0-9+/]{20,}={0,2}" {} \; 2>/dev/null
```

### 2. Decodifica Base64
Una vez identificada una cadena Base64, decodifícala:

```bash
# Método 1: Usando base64 (si está disponible)
echo "TU_CADENA_BASE64_AQUI" | base64 -d

# Método 2: Usando Python
python3 -c "import base64; print(base64.b64decode('TU_CADENA_BASE64_AQUI').decode('utf-8'))"

# Método 3: Usando openssl
echo "TU_CADENA_BASE64_AQUI" | openssl base64 -d
```

### 3. Busca en archivos comunes
```bash
# Revisar archivos de configuración
cat /etc/motd
cat /etc/hidden_config.txt

# Buscar en directorios de usuarios
find /home -type f -exec grep -lE "[A-Za-z0-9+/]{20,}" {} \; 2>/dev/null

# Revisar variables de entorno
env | grep -E "[A-Za-z0-9+/]{20,}"
```

### 4. Decodificación múltiple
A veces el texto puede estar codificado múltiples veces. Prueba decodificar varias veces hasta obtener texto legible.

## 🔍 Comandos Útiles

```bash
# Decodificar y mostrar en hexadecimal si es binario
echo "TU_CADENA_BASE64" | base64 -d | xxd

# Buscar todas las cadenas Base64 en un archivo
cat archivo.txt | grep -oE "[A-Za-z0-9+/]{20,}={0,2}"

# Decodificar desde un archivo
base64 -d archivo_base64.txt
```

## ⚠️ Recordatorios Importantes

1. **Múltiples codificaciones**: El texto puede estar codificado varias veces
2. **Formato de flag**: Busca patrones como `FLAG{...}` o `flag{...}` después de decodificar
3. **Caracteres especiales**: Si la decodificación produce caracteres extraños, puede ser binario o necesitar otra codificación
4. **Herramientas online**: Puedes usar herramientas como CyberChef o dCode.fr para verificar tus resultados

---

**¡Buena suerte resolviendo el desafío!** 🚀
