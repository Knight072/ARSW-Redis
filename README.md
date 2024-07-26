### Aplicación Pizarra Interactiva

Este repositorio contiene una aplicación web que simula una pizarra interactiva, permitiendo a los usuarios dibujar en un lienzo y ver actualizaciones en tiempo real utilizando comunicación WebSocket. La aplicación está dividida en componentes de backend y frontend.

### Visión General de la Arquitectura

#### Backend

El backend está desarrollado con Spring Boot y la API Java WebSocket. Incluye los siguientes componentes:

- **BBAppStarter**: Clase principal para iniciar la aplicación Spring Boot. Configura dinámicamente el puerto del servidor basado en la variable de entorno `PORT` o por defecto en 8080.
  
- **BBConfigurator**: Clase de configuración que habilita los endpoints WebSocket y la programación de tareas.

- **BBEndpoint**: Endpoint WebSocket (`/bbService`) que gestiona las conexiones y transmite puntos de dibujo a los clientes conectados.

- **DrawingServiceController**: Controlador REST que proporciona un endpoint de estado (`/status`) con información básica del servidor.

#### Frontend 

El frontend está implementado con React y P5.js para capacidades de dibujo. Incluye los siguientes componentes:

- **Editor**: Componente React que renderiza la interfaz principal, incluyendo el lienzo de dibujo (`BBCanvas`).
  
- **BBCanvas**: Componente que utiliza P5.js para crear un lienzo interactivo de dibujo. Envía coordenadas de dibujo al servidor WebSocket (`WSBBChannel`) para actualizaciones en tiempo real.
  
- **WSBBChannel**: Clase JavaScript que maneja la comunicación WebSocket con el backend. Establece la conexión y envía/recibe coordenadas de dibujo.

### Inicio Rápido

Para ejecutar la aplicación localmente:

1. **Configuración del Backend**:
   - Asegúrate de tener Java y Maven instalados.
   - Abre el proyecto en tu IDE y ejecuta `BBAppStarter.java`.
   - El backend se iniciará en `https://localhost:8443`.

2. **Configuración del Frontend**:
   - Abre `index.html` en un navegador web moderno.
   - El frontend se conectará al servicio WebSocket del backend que corre en `wss://localhost:8443/bbService`.

### Tecnologías Utilizadas

- **Backend**:
  - Java
  - Spring Boot
  - API WebSocket
  
- **Frontend**:
  - React
  - P5.js (para dibujo en lienzo)
  
- **Otros**:
  - Maven (para gestión de dependencias)
  - Babel (para compilación de JSX a JavaScript)
  
### Uso

- Visita la página de inicio segura (`https://localhost:8443`) y haz clic en el enlace para ver el saludo.
- Inicia sesión con el usuario predeterminado (usuario: "user", contraseña: "password").
- Asegurate de tener corriendo el contenedor docker con la imagen de Redis.
- Abre la aplicación en un navegador después de iniciar tanto el backend como el frontend.
- Usa el ratón para dibujar en el lienzo en el frontend.
- Los cambios se transmitirán en tiempo real a todos los clientes conectados a través de WebSocket.

### Despliegue AWS

![image](https://github.com/Knight072/TableroInt2/assets/116401447/66577cba-68b8-4e03-a3a7-f89f16866639)

---
