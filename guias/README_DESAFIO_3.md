# Desafío 3: Cifrado César y ROT13

## 📝 Descripción
Aplica el cifrado César y ROT13 para descifrar mensajes encriptados y encontrar flags ocultas. Explora los métodos clásicos de criptografía utilizados desde la época romana.

## 🎯 Objetivo
Descifrar mensajes usando Cifrado César y ROT13.

## 💡 Tips Generales

### 1. Identifica el tipo de cifrado
```bash
# Buscar archivos que puedan contener texto cifrado
find / -type f -name "*.txt" -o -name "*cipher*" -o -name "*encrypted*" 2>/dev/null

# Revisar archivos comunes
cat /etc/motd
cat /etc/hidden_config.txt
find /home -type f -exec cat {} \; 2>/dev/null
```

### 2. ROT13 (Cifrado César con desplazamiento 13)
ROT13 es un caso especial del cifrado César donde cada letra se desplaza 13 posiciones.

**Características:**
- ROT13 es simétrico: aplicado dos veces devuelve el texto original
- Solo afecta letras (A-Z, a-z), los números y símbolos permanecen iguales

```bash
# Método 1: Usando tr (si está disponible)
echo "TU_TEXTO_CIFRADO" | tr 'A-Za-z' 'N-ZA-Mn-za-m'

# Método 2: Usando Python
python3 -c "import codecs; print(codecs.decode('TU_TEXTO_CIFRADO', 'rot13'))"
```

### 3. Cifrado César (desplazamiento variable)
Para Cifrado César, necesitas probar todos los desplazamientos posibles (0-25).

**Características:**
- El desplazamiento más común es 3 (como el original de Julio César)
- Solo afecta letras, los números y símbolos permanecen iguales
- Necesitas probar diferentes desplazamientos hasta encontrar uno que tenga sentido

```bash
# Crear un script Python para probar todos los desplazamientos
python3 << 'EOF'
def caesar_decrypt(ciphertext, shift):
    result = ""
    for char in ciphertext:
        if char.isalpha():
            ascii_offset = 65 if char.isupper() else 97
            result += chr((ord(char) - ascii_offset - shift) % 26 + ascii_offset)
        else:
            result += char
    return result

ciphertext = "TU_TEXTO_CIFRADO_AQUI"
for shift in range(26):
    print(f"Shift {shift:2d}: {caesar_decrypt(ciphertext, shift)}")
EOF
```

### 4. Busca el patrón de flag
Después de descifrar, busca patrones como `FLAG{...}` o `flag{...}`:

```bash
# Probar ROT13 primero (más común)
echo "TU_TEXTO" | tr 'A-Za-z' 'N-ZA-Mn-za-m' | grep -i "flag"

# Luego probar César con diferentes desplazamientos
```

## 🔍 Comandos Útiles

```bash
# Decodificar ROT13 desde un archivo
cat archivo.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'

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

## ⚠️ Recordatorios Importantes

1. **Solo letras**: Tanto ROT13 como César solo afectan letras, los números y símbolos permanecen iguales
2. **Análisis visual**: Después de descifrar, el texto debería tener sentido en español/inglés
3. **Múltiples capas**: El texto puede estar cifrado múltiples veces
4. **Prueba sistemática**: Si no sabes el desplazamiento, prueba todos los valores de 0 a 25

---

**¡Buena suerte resolviendo el desafío!** 🚀
