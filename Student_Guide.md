# Guía para Estudiantes

Bienvenidos a la guía para CTF Intro a Cifrados, aquí encontrarán tips y pasos generales para resolver los desafíos **sin revelar las respuestas, eso les toca a ustedes**. Úsenla como referencia cuando se sientan atascados.

## 📋 Índice

- [Desafío 1: Logs y Configuración](guias/README_DESAFIO_1.md)
- [Desafío 2: Codificación Base64](guias/README_DESAFIO_2.md)
- [Desafío 3: Cifrado César y ROT13](guias/README_DESAFIO_3.md)
- [Desafío 4: Análisis de Frecuencia](guias/README_DESAFIO_4.md)

---

## Desafío 1: Logs y Configuración

### 📝 Descripción
Revisa archivos del sistema y logs para encontrar información oculta y flags. Aprende a navegar por directorios y descubrir secretos escondidos en archivos de configuración.

### 📖 Guía Completa
Para ver la guía completa con todos los tips, comandos y ejemplos, consulta: **[README_DESAFIO_1.md](guias/README_DESAFIO_1.md)**

### 🎯 Objetivo
Encontrar flags ocultas en archivos del sistema, logs y configuraciones.

### 💡 Resumen Rápido

- Explora archivos del sistema (`/etc/motd`, `/var/log/auth.log`)
- Identifica usuarios del sistema (`/etc/passwd`)
- Busca archivos ocultos (comienzan con `.`)
- Revisa directorios de usuarios (`/home/`)
- Busca archivos con nombres sospechosos



---


## Desafío 2: Codificación Base64

### 📝 Descripción
Aprende a identificar y decodificar cadenas en formato Base64 para revelar información oculta. Domina una de las técnicas de codificación más utilizadas en CTF.

### 📖 Guía Completa
Para ver la guía completa con todos los tips, comandos y ejemplos, consulta: **[README_DESAFIO_2.md](guias/README_DESAFIO_2.md)**

### 🎯 Objetivo
Identificar y decodificar cadenas Base64 para encontrar flags.

### 💡 Resumen Rápido

- Identifica cadenas Base64 (caracteres: `A-Z`, `a-z`, `0-9`, `+`, `/`, `=`)
- Decodifica usando `base64 -d`, Python o `openssl`
- Busca en archivos comunes (`/etc/motd`, `/etc/hidden_config.txt`)
- Considera múltiples codificaciones (decodifica varias veces)



---


## Desafío 3: Cifrado César y ROT13

### 📝 Descripción
Aplica el cifrado César y ROT13 para descifrar mensajes encriptados y encontrar flags ocultas. Explora los métodos clásicos de criptografía utilizados desde la época romana.

### 📖 Guía Completa
Para ver la guía completa con todos los tips, comandos y ejemplos, consulta: **[README_DESAFIO_3.md](guias/README_DESAFIO_3.md)**

### 🎯 Objetivo
Descifrar mensajes usando Cifrado César y ROT13.

### 💡 Resumen Rápido

- **ROT13**: Usa `tr 'A-Za-z' 'N-ZA-Mn-za-m'` o Python `codecs.decode(text, 'rot13')`
- **César**: Prueba todos los desplazamientos (0-25), el más común es 3
- Solo afecta letras, números y símbolos permanecen iguales
- Puede estar cifrado múltiples veces



---


## Desafío 4: Análisis de Frecuencia

### 📝 Descripción
Utiliza el análisis de frecuencia para descifrar mensajes encriptados y encontrar flags ocultas. Implementa técnicas de criptoanálisis basadas en patrones estadísticos del lenguaje.

### 📖 Guía Completa
Para ver la guía completa con todos los tips, comandos y ejemplos, consulta: **[README_DESAFIO_4.md](guias/README_DESAFIO_4.md)**

### 🎯 Objetivo
Descifrar un mensaje usando análisis de frecuencia de letras.

### 💡 Resumen Rápido

- Analiza frecuencia de letras (E, A, O más comunes en español)
- Analiza bigramas (EN, DE, EL) y trigramas (QUE, EST, DEL)
- Identifica palabras comunes de 1-3 letras (A, EL, LA, DE, EN)
- Ajusta manualmente basándote en el contexto
- Considera que puede ser Cifrado César si el patrón es simple



---



## 📖 Recursos Adicionales

- [CyberChef](https://gchq.github.io/CyberChef/) - Herramienta online para múltiples codificaciones
- [dCode.fr](https://www.dcode.fr/) - Herramientas de criptoanálisis online
- [Base64 Decoder](https://www.base64decode.org/) - Decodificador Base64 online
- [ROT13 Decoder](https://rot13.com/) - Decodificador ROT13 online



---


## ✅ Checklist de Resolución

Para cada desafío, asegúrate de:

- [ ] Acceder correctamente al contenedor Docker
- [ ] Explorar todos los archivos del sistema mencionados
- [ ] Buscar archivos ocultos y con nombres sospechosos
- [ ] Aplicar las técnicas de decodificación apropiadas
- [ ] Verificar que el resultado tenga sentido
- [ ] Buscar el patrón de flag (`FLAG{...}` o `flag{...}`)
- [ ] Documentar los pasos seguidos

---

**¡Buena suerte resolviendo los desafíos!** 🚀

*Recuerda: La persistencia y la atención al detalle son clave para resolver CTFs.*
