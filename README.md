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

  <img width="886" height="467" alt="image" src="https://github.com/user-attachments/assets/f124ef7e-97d9-4a72-9b38-a513a41acdc2" />


3. Definir las variables de entorno con las credenciales del Git Hub de cada integrante del Grupo 3

   <img width="886" height="498" alt="image" src="https://github.com/user-attachments/assets/2264aff2-8c1c-4871-ba1e-1a3118d6ccf3" />


4. Construir el workflow del `Docker Scout`

   <img width="886" height="449" alt="image" src="https://github.com/user-attachments/assets/a01afc9c-674b-4cc7-aec3-138a07388602" />


5. Definir la orquestación para analizar la imagen de fast-api indicando el nombre de la imagen con la cual se creará el repositorio en el Docker Hub

   <img width="886" height="561" alt="image" src="https://github.com/user-attachments/assets/45c42256-18c7-41d9-a152-1ebe9286e65b" />


6. Validar la ejecución del workflow

  <img width="886" height="358" alt="image" src="https://github.com/user-attachments/assets/268c5329-478d-433c-a4fd-0467c2ec397f" />

 

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

   <img width="1342" height="520" alt="image" src="https://github.com/user-attachments/assets/4d313a5f-c172-40dd-937e-b931d8176acb" />


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
