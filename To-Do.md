# Tareas Pendientes (Actualizado 06/05/2026)

*Se han completado todas las tareas previas relacionadas a la lógica de negocio, UX/UI, layouts y validaciones de formulario. Ver `DOCS.md` para el detalle de las implementaciones.*

## Sugerencias para Próximos Pasos:

1. **Pruebas E2E (End to End):**
   - Configurar Cypress o Playwright en el proyecto Angular.
   - Crear un flujo de prueba automatizado para el registro, login y la reserva de un libro.

2. **Paginación y Carga Diferida:**
   - Implementar carga infinita (Infinite Scroll) o paginación tradicional en el componente Catálogo (`catalog.component.ts`), ya que actualmente renderiza todos los libros de una vez.

3. **Panel de Administración:**
   - Crear una interfaz administrativa (solo visible para roles "admin" o "librarian") para poder añadir, editar y eliminar libros del sistema sin tener que usar directamente Django Admin.

4. **Mejora del Perfil de Usuario:**
   - Permitir a los usuarios subir una foto de perfil y editar sus datos básicos (nombre, apellido).
   - Mostrar el historial de libros leídos/reservados con fechas.

5. **Notificaciones Reales:**
   - Sustituir el actual mock de "Bandeja de Notificaciones" por un sistema real utilizando un endpoint del backend (ej. Django Channels para websockets o short-polling).