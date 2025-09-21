# Curso: Despliegue de aplicaciones con Docker<br/>CEC-EPN<br/><br/>Tarea 1:  Despliegue en Docker de phpMyAdmin

![Lenguaje][lngsrv-shield]
![Servidor de contenedores][cont-shield]

## Integrantes Grupo 3

- [Glenda Pallo](https://github.com/glendypallo/DespliegueContenedores-Tarea3-GP)
- [Patricia Jaramillo](https://github.com/PatyJaramillo/DespliegueContenedores-Tarea3-PJ)
- [William Ayala](https://github.com/wrayalav/DespliegueContenedores-Tarea3-WA)
- [Guillermo Cifuentes](https://github.com/guillogps/DespliegueContenedores-Tarea3-GC)
- [Ruperto Cisneros](https://github.com/srcisnerosv-star/DespliegueContenedores-Tarea3-RC)

<br/>

## Introducción

El presente flujo de trabajo en GitHub Actions tiene como objetivo automatizar el proceso de construcción, publicación y análisis de imágenes Docker dentro de un entorno de integración continua. La configuración incluye la autenticación en Docker Hub, la construcción de la imagen con docker/build-push-action, y el posterior análisis de vulnerabilidades con Docker Scout, garantizando así que las imágenes generadas sean seguras y confiables antes de ser utilizadas en entornos de despliegue.
Este pipeline implementa buenas prácticas de DevSecOps, al integrar el análisis de seguridad directamente en la cadena de construcción, permitiendo detectar vulnerabilidades desde etapas tempranas y asegurando la trazabilidad de cada versión mediante el etiquetado con el hash del commit (sha). Asimismo, se incorpora la generación y almacenamiento del reporte en formato JSON como artefacto, lo que facilita la auditoría y el seguimiento de hallazgos de seguridad.

<br/>

## Construido con

- Docker
- Docker Scout
- Docker Compose
- [Python](https://hub.docker.com/_/python)

<br/>

## Archivos

La tarea contiene los siguientes archivos:

| Archivo | Descripción |
| ---- | ---- |
| [Dockerfile](Dockerfile) | Archivo que contiene las instrucciones para crear una imagen en Docker. |
| [requirements.txt](requirements.txt) | Archivo donde se define los requisitos de la aplicación python. |
| [index.html](index.html) | Página de inicio | 
| [scout.yml](.github/workflows/scout.yml) | Archivo que define la orquestación del análisis de la imagen de fast-api. |

<br/>

## Procedimiento

1. Recopilar archivos del ejercicio `fast-api`.

2. Cargarlos a GitHub.

   ![Imagen de WhatsApp 2025-09-20 a las 22 29 23_128dd842](https://github.com/user-attachments/assets/09d340e5-f517-4ee7-aec5-3c049eeb5ecf)

4. Definir las variables de entorno con las credenciales del Git Hub de cada integrante del Grupo 3

   <img width="2560" height="1305" alt="image" src="https://github.com/user-attachments/assets/066a87f3-92f8-44f5-9d57-8cdc0f2dce2b" />

   <img width="2560" height="1305" alt="image" src="https://github.com/user-attachments/assets/217424ac-527d-4c54-bdf6-46fe85c49af7" />

5. Construir el workflow del `Docker Scout`

   <img width="2560" height="1305" alt="image" src="https://github.com/user-attachments/assets/765195e2-51ad-49da-82d7-ffe8f8248f51" />

5. Definir la orquestación para analizar la imagen de fast-api indicando el nombre de la imagen con la cual se creará el repositorio en el Docker Hub

   <img width="2560" height="1305" alt="image" src="https://github.com/user-attachments/assets/2db20e34-8df8-4221-88dd-1c4848e571be" />

   <img width="2560" height="1305" alt="image" src="https://github.com/user-attachments/assets/5ea3d780-62ff-4cb9-994d-b10e5269d9e4" />

6. Validar la ejecución del workflow

   <img width="2560" height="1305" alt="image" src="https://github.com/user-attachments/assets/bd0c2e3a-34a7-4a7e-af22-1044f4445011" />

   <img width="2560" height="1305" alt="image" src="https://github.com/user-attachments/assets/9f392fd0-ba39-44c4-aaf8-a2d7dcca44ee" />

7. Resultado del análisis del Docker Scout

   ```
   ...Storing image for indexing
    ✓ Image stored for indexing
    ...Indexing
    ✓ Indexed 147 packages
    ✗ Detected 11 vulnerable packages with a total of 23 vulnerabilities
    ✓ Report written to json
   ```

8. Validar la creación de la imagen en el Docker Hub

   <img width="2560" height="1305" alt="image" src="https://github.com/user-attachments/assets/45c1d5d3-71f5-42ef-9b8e-e03b9dc98e8a" />

<br/>

## Conclusiones

- La integración de Docker Scout dentro del flujo de GitHub Actions representa un paso estratégico hacia la consolidación de un ciclo de vida seguro para las aplicaciones contenerizadas. Gracias a este proceso automatizado:

- Se asegura la consistencia en la construcción de imágenes, al centralizar la definición del Dockerfile y los parámetros de compilación.

- Se fortalecen los controles de seguridad preventiva, al identificar vulnerabilidades en librerías y dependencias antes de llegar a entornos productivos.

- Se mejora la trazabilidad y gobernanza, ya que los reportes JSON almacenados como artefactos permiten un análisis posterior y la integración con sistemas de gestión de seguridad.

- Se potencia la eficiencia operativa, al reducir riesgos de fallas o brechas de seguridad en fases posteriores del despliegue.

<!-- MARKDOWN LINKS & IMAGES -->
[lngsrv-shield]: https://img.shields.io/badge/LNG-PYTHON-9cf?style=for-the-badge&logo=python&logoColor=red
[cont-shield]: https://img.shields.io/badge/CONTAINER-DOCKER-red?style=for-the-badge&logo=docker
