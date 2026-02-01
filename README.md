# CTF Intro a Cifrados

<a id="readme-top"></a>

## 📜 Descripción

**CTF Intro a Cifrados** es un repositorio educativo diseñado para introducir a los estudiantes en conceptos fundamentales de criptografía y seguridad informática a través de desafíos prácticos tipo CTF (Capture The Flag).

Este proyecto incluye 4 desafíos progresivos que enseñan:

- **Desafío 1**: Fundamentos de Linux y exploración de sistemas
- **Desafío 2**: Codificación Base64
- **Desafío 3**: Cifrado César y ROT13
- **Desafío 4**: Análisis de frecuencia para criptoanálisis

Cada desafío está diseñado para construir sobre los conocimientos adquiridos en el anterior, creando una experiencia de aprendizaje progresiva.

## 🎯 Objetivos de Aprendizaje

Al completar estos desafíos, los estudiantes aprenderán:

- Navegación y exploración de sistemas Linux
- Identificación y decodificación de diferentes tipos de codificación
- Comprensión de cifrados clásicos (César, ROT13)
- Técnicas básicas de criptoanálisis mediante análisis de frecuencia
- Resolución de problemas de seguridad mediante metodología CTF

## 📦 Requisitos

- Conocimientos básicos de Linux
- Docker instalado
- Docker Compose instalado
- Terminal/consola de comandos

## 🚀 Instalación y Ejecución

### 1. Clonar el repositorio

```bash
git clone https://github.com/locano-uvg/ctf_intro_ciphers.git
cd ctf_intro_ciphers
```

### 2. Ejecutar Docker Compose

```bash
docker compose up -d
```

### 3. Verificar que los contenedores estén activos

```bash
docker ps
```

Deberías ver 4 contenedores ejecutándose:
- `challenge1_ctf`
- `challenge2_ctf`
- `challenge3_ctf`
- `challenge4_ctf`

### 4. Acceder a los desafíos

Cada desafío se ejecuta en su propio contenedor. Para acceder a un desafío específico:

```bash
docker exec -it challenge1_ctf bash
docker exec -it challenge2_ctf bash
docker exec -it challenge3_ctf bash
docker exec -it challenge4_ctf bash
```

## 📚 Estructura del Proyecto

```
ctf_intro_cifrados/
├── docker-compose.yml      # Configuración de los contenedores
├── README.md               # Este archivo
├── Student_Guide.md        # Guía para estudiantes (tips sin respuestas)
├── guias/                  # Guías detalladas por desafío
│   ├── README_DESAFIO_1.md # Guía del Desafío 1: Logs y Configuración
│   ├── README_DESAFIO_2.md # Guía del Desafío 2: Codificación Base64
│   ├── README_DESAFIO_3.md # Guía del Desafío 3: Cifrado César y ROT13
│   └── README_DESAFIO_4.md # Guía del Desafío 4: Análisis de Frecuencia
└── docs/                   # Documentación y recursos visuales
```

## 🎓 Guía para Estudiantes

Para obtener ayuda y tips sobre cómo resolver los desafíos (sin spoilers), consulta el archivo **[Student_Guide.md](Student_Guide.md)**.

## 🔗 Recursos Adicionales

### Herramientas Online Útiles

- [CyberChef](https://gchq.github.io/CyberChef/) - Herramienta online para múltiples codificaciones
- [dCode.fr](https://www.dcode.fr/) - Herramientas de criptoanálisis online
- [Base64 Decoder](https://www.base64decode.org/) - Decodificador Base64 online
- [ROT13 Decoder](https://rot13.com/) - Decodificador ROT13 online

### Documentación de Referencia

- [Docker Documentation](https://docs.docker.com/)
- [Linux Command Reference](https://www.linux.org/docs/)
- [Cryptography Basics](https://en.wikipedia.org/wiki/Cryptography)

## 📝 Notas Importantes

- Los desafíos están diseñados para resolverse en orden (cada uno depende del anterior)
- Cada desafío requiere encontrar un flag en formato `FLAG{...}`
- Los flags encontrados en un desafío pueden ser necesarios para el siguiente
- No hay límite de tiempo para resolver los desafíos
- Se recomienda documentar los pasos seguidos para aprendizaje

## 👥 Contribuciones

Si deseas contribuir al proyecto, por favor sigue los siguientes pasos:

1. Realiza un fork del repositorio
2. Crea una nueva rama para tu funcionalidad (`git checkout -b feature/nueva-funcionalidad`)
3. Haz commit de tus cambios (`git commit -m 'Añadir nueva funcionalidad'`)
4. Haz push a la rama (`git push origin feature/nueva-funcionalidad`)
5. Abre un Pull Request

## 👨‍💻 Developer

<a href="https://github.com/locano">
  <img width='75' src="https://avatars.githubusercontent.com/u/16949087?v=4" alt="Ludwing Cano" />
</a>

* [![Linkedin][Linkedin]][Linkedin-lud]
* [![GitHub][GitHub]][GitHub-lud]

<p align="right">(<a href="#readme-top">Ir al inicio</a>)</p>

## 📞 Contacto

Si tienes preguntas o comentarios, puedes contactarnos a través de nuestras redes sociales:

* [![Instagram][Instagram]][Instagram-url]
* [![Website][Website]][Website-url]

<p align="right">(<a href="#readme-top">Ir al inicio</a>)</p>

<!-- MARKDOWN LINKS & IMAGES -->
[Linkedin-lud]: https://www.linkedin.com/in/ludwing-cano238
[Linkedin]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[Github-lud]: https://github.com/locano
[GitHub]: https://img.shields.io/badge/github-%23121011.svg?style=for-the-badge&logo=github&logoColor=white
[Instagram]: https://img.shields.io/badge/Instagram-E4405F?style=flat&logo=instagram&logoColor=white
[Instagram-url]: https://www.instagram.com/ludwing238/
[Website]: https://img.shields.io/website?url=https://lc2tech.com/
[Website-url]: https://lc2tech.com/
