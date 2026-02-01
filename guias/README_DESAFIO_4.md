# Desafío 4: Análisis de Frecuencia

## 🚀 Acceso al Desafío

Para acceder al contenedor Docker de este desafío, ejecuta el siguiente comando:

```bash
docker exec -it challenge4_ctf bash
```

Una vez dentro del contenedor, podrás comenzar a explorar el sistema y buscar las flags ocultas.

## 📚 Documentación General

Para más información sobre el proyecto, instalación y configuración, consulta el [README principal del repositorio](../../README.md).

---

## 📝 Descripción
Utiliza el análisis de frecuencia para descifrar mensajes encriptados y encontrar flags ocultas. Implementa técnicas de criptoanálisis basadas en patrones estadísticos del lenguaje.

## 🎯 Objetivo
Descifrar un mensaje usando análisis de frecuencia de letras.

## 💡 Tips Generales

### 1. Encuentra el texto cifrado
```bash
# Buscar archivos con texto cifrado
find / -type f -name "*.txt" -o -name "*cipher*" 2>/dev/null

# Revisar archivos comunes
cat /etc/motd
cat /etc/hidden_config.txt
find /home -type f -exec cat {} \; 2>/dev/null
```

### 2. Analiza frecuencia de letras
El análisis de frecuencia se basa en que en español/inglés, ciertas letras aparecen más frecuentemente:

- **Español**: E, A, O, S, R, N, I, D, L, C, T, U, M, P, B, G, V, Y, Q, H, F, Z, J, Ñ, X, K, W
- **Inglés**: E, T, A, O, I, N, S, H, R, D, L, U, C, M, W, F, G, Y, P, B, V, K, J, X, Q, Z

```bash
# Contar frecuencia de letras en el texto cifrado
cat archivo_cifrado.txt | tr '[:upper:]' '[:lower:]' | grep -o '[a-z]' | sort | uniq -c | sort -rn
```

### 3. Analiza bigramas y trigramas
Además de letras individuales, analiza pares y tríos de letras comunes:

**Bigramas comunes en español**: EN, DE, EL, LA, ES, SE, LO, UN
**Trigramas comunes en español**: QUE, EST, DEL, LOS, LAS, CON, POR

```bash
# Análisis de bigramas (pares de letras)
cat archivo.txt | tr '[:upper:]' '[:lower:]' | grep -oE '[a-z]{2}' | sort | uniq -c | sort -rn | head -20

# Análisis de trigramas (tríos de letras)
cat archivo.txt | tr '[:upper:]' '[:lower:]' | grep -oE '[a-z]{3}' | sort | uniq -c | sort -rn | head -20
```

### 4. Identifica palabras comunes
Identifica palabras de 1-3 letras primero (artículos, preposiciones):

- **Español**: A, EL, LA, DE, EN, UN, UNA, LOS, LAS, CON, POR
- **Inglés**: A, AN, THE, IN, ON, AT, TO, FOR, OF, WITH

```bash
# Contar palabras de longitud específica
cat archivo.txt | tr '[:space:]' '\n' | awk 'length($0)==1' | sort | uniq -c | sort -rn
cat archivo.txt | tr '[:space:]' '\n' | awk 'length($0)==2' | sort | uniq -c | sort -rn
```

### 5. Ajusta manualmente
El análisis de frecuencia da una aproximación, pero puede necesitar ajustes:

1. Identifica palabras comunes de 1-3 letras (artículos, preposiciones)
2. Busca patrones repetitivos que puedan ser palabras comunes
3. Ajusta las sustituciones basándote en el contexto
4. Verifica que el texto descifrado tenga sentido

### 6. Considera que puede ser Cifrado César
Si el análisis de frecuencia sugiere un patrón de sustitución simple, podría ser un Cifrado César. Prueba diferentes desplazamientos:

```bash
# Probar todos los desplazamientos de César
for i in {0..25}; do
    echo "=== Shift $i ==="
    cat archivo.txt | python3 -c "
import sys
text = sys.stdin.read()
for char in text:
    if char.isalpha():
        offset = 65 if char.isupper() else 97
        print(chr((ord(char) - offset - $i) % 26 + offset), end='')
    else:
        print(char, end='')
"
    echo ""
done
```

## 🔍 Comandos Útiles

```bash
# Análisis de frecuencia básico
cat archivo.txt | tr '[:upper:]' '[:lower:]' | grep -o '[a-z]' | sort | uniq -c | sort -rn

# Análisis de bigramas (pares de letras)
cat archivo.txt | tr '[:upper:]' '[:lower:]' | grep -oE '[a-z]{2}' | sort | uniq -c | sort -rn | head -20

# Análisis de trigramas (tríos de letras)
cat archivo.txt | tr '[:upper:]' '[:lower:]' | grep -oE '[a-z]{3}' | sort | uniq -c | sort -rn | head -20
```

## ⚠️ Recordatorios Importantes

1. **Frecuencias de bigramas y trigramas**: Además de letras individuales, analiza pares (TH, HE, IN) y tríos (THE, AND, ING)
2. **Palabras comunes**: Identifica palabras de 1-2 letras primero (A, EL, LA, DE, EN)
3. **Patrones repetitivos**: Las palabras comunes aparecerán múltiples veces
4. **Ajuste iterativo**: Empieza con el análisis de frecuencia y luego ajusta manualmente
5. **Herramientas online**: Puedes usar herramientas como dcode.fr para análisis de frecuencia

---

**¡Buena suerte resolviendo el desafío!** 🚀
