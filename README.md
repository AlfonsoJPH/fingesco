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

## Hito 3: Diseño de microservicios

Para este hito, he creado un microservicio sobre la base de la funcionalidad desarrollada en el hito anterior. He diseñado una API consistente en una serie de rutas, añadido un sistema de logs, y testeado la API exhaustivamente usando bibliotecas específicas.

### Justificación técnica del framework elegido

He elegido **Express.js** como framework para el microservicio debido a su simplicidad y flexibilidad. Express.js es un framework minimalista y robusto para Node.js que facilita la creación de aplicaciones web y APIs REST. Su amplia comunidad y ecosistema de middleware lo hacen ideal para este tipo de proyectos.

### Diseño de la API

La API se ha diseñado con un enfoque REST, separando la lógica de negocio de la lógica del API. Las rutas principales incluyen:

- **GET /recursos**: Obtiene todos los recursos.
- **GET /sensores**: Obtiene todos los sensores.

### Sistema de logs

Se ha elegido **winston** como biblioteca de logging debido a su flexibilidad y capacidad para manejar múltiples transportes (consola, archivos, etc.). Winston permite configurar diferentes niveles de logs (info, error, warning) y formatear los mensajes de log de manera personalizada. Los logs se registran tanto en la consola como en un archivo `combined.log`.

### Configuración

El proyecto utiliza variables de entorno para la configuración. Las variables de entorno se definen en un archivo `.env`. Aquí está un ejemplo de las variables de entorno necesarias:

```
REDIS_HOST=localhost
REDIS_PORT=6379
SERVER_PORT=3001
API_KEY=pcldETTDtJ4CQVz9FqlJYHgIvdYP1iXU
```

### Estructura del Proyecto

```
.
├── src
│   ├── controllers
│   │   ├── recursosController.js
│   │   └── sensoresController.js
│   ├── middlewares
│   │   └── apiKey.js
│   ├── services
│   │   └── redisService.js
│   ├── app.js
│   ├── redisClient.js
│   └── server.js
├── tests
│   └── redisApi.test.js
├── .env
├── index.js
└── package.json
```

### Ejecución de tests

Para implementar y ejecutar los tests, he utilizado `Supertest` para simular solicitudes HTTP y verificar la lógica de negocio clave en los endpoints. Los tests se ejecutan de forma centralizada con `npm test`, tanto en local como en Jenkins.


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
