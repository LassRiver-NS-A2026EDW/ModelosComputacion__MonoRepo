# Tareas Completadas - 06/05/2026

## 1. Funcionalidad y Lógica de Negocio
- **Sistema de Reseñas:** Se corrigió el componente `app-rating-stars` para permitir cambiar la calificación añadiendo `[readonly]="false"`.
- **Control de Acceso:** Se implementó un `AuthModalComponent` y el método `requireAuth` en el `AppStore`. Ahora los botones de Favoritos, Notificaciones y Reservar muestran este modal si el usuario no ha iniciado sesión.
- **Reservas:** Se añadió el botón interactivo de "Reservar Libro" con simulación de feedback visual.

## 2. UX / UI y Feedback Visual
- **Disponibilidad:** Se aplicó opacidad (`opacity-70`) y escala de grises (`grayscale`) a las tarjetas de libros no disponibles en el Catálogo, con un tag rojo fuerte.
- **Micro-interacciones:** El botón de Favoritos ahora reacciona al clic con un efecto de escala (`active:scale-90`) para dar mejor feedback.
- **Modales de Confirmación:** Se creó el `ConfirmModalComponent` y se implementó para las acciones críticas: Cerrar Sesión y Eliminar Reseña.

## 3. Refinamiento del Layout
- **Buscador:** Se ajustó el padding (`pl-10`) para evitar que el ícono de lupa se superponga con el texto ingresado.
- **Buscador Condicional:** Ahora el buscador en el Topbar solo es visible en la ruta `/catalog`.
- **Iconografía:** Se reemplazaron los íconos genéricos por el logo oficial (`logo.png`) en el Sidebar y el Hero de la página de inicio.

## 4. Formularios y Validaciones (Registro)
- **Validación en Bloque:** El formulario de registro ahora muestra todos los errores a la vez usando una lista.
- **Restricciones:** 
  - `username` limitado a máximo 15 caracteres.
  - Fecha de nacimiento restringida a ser anterior o igual al 31/12/2020 (`max="2020-12-31"`).
- **Contraseña:** Se agregó un checklist dinámico que valida en tiempo real la longitud, mayúsculas, números y caracteres especiales, coloreando de verde los requisitos cumplidos.

## 5. Gestión de Assets
- El archivo `logo.png` fue movido de la raíz a `angular/public/logo.png` para su correcto acceso desde los componentes.
