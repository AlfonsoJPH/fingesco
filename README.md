# Fingesco

Este proyecto planea hacer un software de gestión y control de fincas agrarias que permita registrar distintas fincas y monitorizar los recursos de estas, asi como comprobar distintos sensores (temperatura, humedad, camaras, etc.) y controlar distintos actuadores (sistemas de riego, luces, etc.) mediante el uso de distintos modulos.

**DISCLAMER**
Actualmente esto solo se usara como plantilla de un posible TFM para probar y desarrollar distintas herramientas que pueden (o no) ser usadas en el proyecto final, mientras tanto tambien se usará como repositorio para la asignatura Cloud Computing para probar el despliegue de dichas herramientas/pruebas en la nube.

## Hito 2

Para este hito, he decidido introducir al proyecto principal un nuevo submódulo que se encargará de la gestión de la lógica de los endpoints. He usado `npm test`, `Supertest` y `Jenkins` para configurar y ejecutar las pruebas en un flujo de integración continua.

### Elección y configuración del gestor de tareas
He elegido `npm scripts` como gestor de tareas, ya que utilizo Node.js como base del proyecto. `npm` permite ejecutar tareas de manera directa sin herramientas adicionales, como `npm test` para ejecutar pruebas, `npm start` para arrancar la aplicación, entre otros. Además, su integración con servicios de CI/CD como GitHub Actions y Jenkins facilita la automatización de las pruebas en entornos de integración continua.

### Elección de la biblioteca de aserciones
He optado por `Supertest` como biblioteca de aserciones. Esta herramienta me permite realizar pruebas de endpoints de manera sencilla y facilita la comparación entre los resultados esperados y los obtenidos. Además, se ajusta a un estilo de desarrollo orientado al comportamiento (**BDD**) porque permite escribir pruebas que simulan la interacción del usuario con los endpoints.

### Elección del marco de pruebas
Para gestionar y ejecutar las pruebas, utilizo `Supertest` en combinación con `Jest` como test runner, que permiten localizar y ejecutar las pruebas y ofrecen informes detallados de resultados. Estas herramientas son compatibles con Jenkins, lo cual facilita la generación de reportes y la integración en un flujo de CI/CD.

### Configuración de la Integración Continua
He configurado **Jenkins** como sistema de integración continua. Esta herramienta me permite automatizar la ejecución de las pruebas en cada cambio del código y asegura que cualquier error se detecte rápidamente.
Para ello, he desplegado un contenedor de Jenkins en la nube y creado una pipeline que se encarga de ejecutar las pruebas en cada cambio del código. Además, he configurado un webhook en GitHub para que Jenkins se ejecute automáticamente al recibir un nuevo push en el repositorio.

### Implementación y ejecución de pruebas
Para implementar y ejecutar los tests, me aseguro de verificar la lógica de negocio clave en los endpoints usando `Supertest` para simular solicitudes HTTP. De esta manera, ejecuto todas las pruebas de forma centralizada con `npm test`, tanto en local como en Jenkins.

Todo lo relacionado con la configuración de Jenkins y la ejecución de las pruebas se encuentra en la carpeta [fingesco-endpoint/tests](https://github.com/AlfonsoJPH/fingesco-endpoint/tree/19b9a051ecf9d540419668748e78b12ee53dda9c/tests)


## Índice
- [Características](#características)
- [Estructura del Repositorio](#estructura-del-repositorio)
- [Requisitos](#requisitos)
- [Instalación](#instalación)
- [Uso](#uso)
- [Contribución](#contribución)
- [Licencia](#licencia)

## Características
- Registro de usuarios
- Registro de finca
- Monitorización en tiempo real de los recursos


## Estructura del Repositorio
Este repositorio incluye los siguientes submódulos:
- **Backend**: Contiene la lógica del servidor y la API. (Ruta: `fingesco-backend/`)
- **Frontend**: Interfaz de usuario construida con React. (Ruta: `fingesco-frontend/`)
- **Módulos**: Carpeta que contiene módulos reutilizables y utilidades. (Ruta: `modules/`)

## Requisitos
Asegúrate de tener instalados los siguientes requisitos antes de ejecutar el proyecto:
TODO
- [Cualquier otro requisito necesario]

## Instalación
Para instalar el proyecto, sigue estos pasos:

1. **Clonar el repositorio**:
   ```bash
   git clone https://github.com/AlfonsoJPH/fingesco.git
   cd fingesco

2. **Inicializar submódulos**:

   ```bash
   git submodule init
   git submodule update

3. **Instalar dependencias del Backend**:

TODO

4. **Instalar dependencias del Frontend**:

TODO


## Uso

TODO

# Contribución

Si deseas contribuir a este proyecto, sigue estos pasos:

    Realiza un fork del repositorio.
    Crea una nueva rama (git checkout -b feature/nueva-caracteristica).
    Realiza tus cambios y haz commit (git commit -m 'Agrega nueva característica').
    Envía un pull request.

# Licencia

Este proyecto está bajo la GNU Affero General Public License v3.0 - consulta el archivo LICENSE para más detalles.
