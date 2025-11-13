# 📋 DevelopWork - Sistema de Gestión de Mantenimiento y Notificaciones

<div align="center">
  <img src="https://img.shields.io/badge/Angular-16-%23DD0031?style=flat&logo=angular" alt="Angular"/>
  <p><em>Aplicación web para la gestión de órdenes de mantenimiento, notificaciones internas y administración de empleados.</em></p>
</div>

---

## 🔎 Visión general

DevelopWork es una aplicación frontend desarrollada en Angular 16 pensada para optimizar y centralizar los procesos relacionados con solicitudes de mantenimiento, la comunicación entre usuarios y la administración del personal técnico y administrativo. La aplicación facilita la creación, seguimiento y archivo de órdenes de trabajo, ofrece un sistema de notificaciones en tiempo real y proporciona herramientas de gestión de empleados con roles y permisos.

Este README documenta qué hace el proyecto, sus funcionalidades principales, estructura y cómo ponerlo en marcha y probarlo localmente.

---

## 🚀 Qué hace y cuál es su función

DevelopWork cumple la función de centralizar y automatizar el flujo de trabajo de mantenimiento dentro de una organización. Sus responsabilidades principales son:

- Recepción y registro de órdenes de mantenimiento (solicitudes).
- Gestión del ciclo de vida de una orden: estados, asignación, progreso y cierre.
- Notificaciones entre usuarios (alertas a supervisores, asignaciones a técnicos, etc.) en tiempo real.
- Mantenimiento del historial de notificaciones y órdenes.
- Administración de empleados (CRUD): creación, edición, búsqueda y filtrado.
- Gestión de roles y permisos para controlar acceso y acciones (por ejemplo, Administrador, Supervisor, Técnico).
- Implementación de eliminación lógica (soft delete) para preservar el historial de órdenes completadas.

---

## 🧩 Funcionalidades clave

### Gestión de órdenes de mantenimiento
- Crear nuevas órdenes con datos descriptivos (tipo de fallo, ubicación, prioridad, adjuntos).
- Editar y actualizar órdenes en curso.
- Seguimiento por estados: Pendiente → En Proceso → Completado → Archivado / Cancelado.
- Eliminación lógica para mantener trazabilidad histórica.

### Notificaciones en tiempo real
- Comunicación instantánea entre usuarios del sistema.
- Alertas automáticas a superiores o grupos cuando se crean órdenes críticas.
- Historial de notificaciones para seguimiento y auditoría.
- Integración pensada para utilizar servicios de mensajería en tiempo real (ej. Socket.IO).

### Gestión de empleados y permisos
- CRUD completo de empleados (registro, edición, baja lógica).
- Roles y permisos para condicionar vistas y acciones del usuario.
- Búsqueda y filtros avanzados para localizar personal según criterios.

### Seguridad y autenticación
- Autenticación basada en tokens (ej. JWT) para proteger endpoints y sesiones.
- Manejo de autorización por roles para rutas y acciones sensibles.

---

## 🛠 Tecnologías y herramientas (frontend)

- Angular 16
- TypeScript
- HTML5 / SCSS
- Tailwind CSS (configurado en el proyecto)
- Integraciones esperadas en arquitectura: JWT para autenticación y Socket.IO para notificaciones en tiempo real

> Nota: El repositorio contiene la configuración básica de Angular y Tailwind. El backend (API) se asume separado y proporciona autenticación, persistencia y endpoints para órdenes, notificaciones y empleados.

---

## 📁 Estructura general del proyecto (resumen)

Dentro de la carpeta `src/` típicamente encontrarás:
- `app/` — Módulos y componentes principales: paneles, formularios de órdenes, listas, componentes de notificación.
- `assets/` — Imágenes, íconos y recursos estáticos.
- `environments/` — Configuraciones por entorno (dev, prod).
- `styles.*` — Estilos globales (SCSS/Tailwind).

(La estructura exacta puede variar; revisa `src/` en el repositorio para ver archivos y módulos concretos.)

---

## 📥 Instalación y puesta en marcha (desarrollo)

Estos pasos son para ejecutar el frontend localmente. Se asume que tienes Node.js y Angular CLI instalados.

1. Clona el repositorio:
   - git clone https://github.com/KadirQuintero03/Developwork.git

2. Entra en la carpeta del proyecto:
   - cd Developwork

3. Instala dependencias:
   - npm install

4. Configura variables de entorno / endpoints:
   - Revisa `src/environments/` y ajusta las URLs del backend (API) y de sockets si es necesario.

5. Ejecuta la aplicación en modo desarrollo:
   - ng serve
   - Abre http://localhost:4200 en tu navegador.

---

## ✅ Pruebas y testeo

El proyecto fue desarrollado con soporte para pruebas de funcionalidades. Dependiendo de la configuración del proyecto (herramientas usuales en Angular: Karma + Jasmine para unit tests, y Cypress o Protractor para E2E), los comandos habituales son:

- Ejecutar pruebas unitarias:
  - npm run test
  - o bien: ng test

- Ejecutar pruebas end-to-end (si están configuradas):
  - npm run e2e
  - o bien: ng e2e

- Ejecutar linter / verificación de estilos (si está configurado):
  - npm run lint

Revisa `package.json` para ver los scripts disponibles y las dependencias de testing concretas (Karma, Jasmine, Jest, Cypress, etc.). Si necesitas que adapte o añada scripts concretos, indícamelo y puedo sugerir cambios.

---

## 🧭 Flujo de trabajo recomendado para desarrollo

- Crea una rama por característica o bug:
  - git checkout -b feature/mi-nueva-funcionalidad
- Haz commits pequeños y descriptivos:
  - git commit -m "feat(orden): añadir campo prioridad"
- Mantén la rama sincronizada con main y crea un Pull Request cuando esté lista.

---

## 🔧 Buenas prácticas y consideraciones técnicas

- Mantener la lógica de negocio en servicios de Angular para favorecer testabilidad y separación de responsabilidades.
- Usar Guards y Roles para proteger rutas y componentes sensibles.
- Persistir cambios críticos mediante soft delete para conservar historial y auditoría.
- Implementar manejo de errores y feedback al usuario (toasts, modales) en cada flujo de interacción.
- Para notificaciones en tiempo real, usar mecanismos que reconozcan reconexiones y reintentos (p. ej. Socket.IO con lógica de reintento).

---

## 📦 Despliegue

- Construir la aplicación para producción:
  - ng build --prod
- El contenido resultante en `dist/` puede servirse desde cualquier servidor estático (Nginx, Apache, CDN) o integrarse en un pipeline con un backend que sirva los archivos estáticos.
- Asegúrate de configurar variables de entorno de la API y de cualquier servicio de sockets en el entorno de producción.

---

## 🤝 Contribuciones

¡Las contribuciones son bienvenidas! Para contribuir:

1. Haz un fork del repositorio.
2. Crea una rama para tu cambio: git checkout -b feature/nombre.
3. Haz commits claros y descriptivos.
4. Empuja tu rama y abre un Pull Request describiendo el cambio y por qué es necesario.
5. Añade pruebas si agregas o cambias lógica importante.

---

## ✉️ Contacto

- Frontend: kadireq1928@gmail.com  
- Backend: juandavidperaltafuentes@gmail.com

---

## 📜 Licencia

Incluye aquí la información de licencia del proyecto (si aplica). Si no hay licencia, considera añadir una (por ejemplo MIT) para aclarar el permiso de uso y contribución.

---

Si deseas, puedo:
- Actualizar el README.md en el repositorio con este contenido.
- Añadir secciones adicionales (docs para la API esperada, ejemplos de payloads para las órdenes, o guías de despliegue más detalladas).
- Generar ejemplos de pruebas unitarias o e2e para los flujos principales.
