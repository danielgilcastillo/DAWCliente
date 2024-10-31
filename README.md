1. Archivo login.html
Este archivo maneja el formulario de inicio de sesión y la validación de usuario.
Cambios realizados:
Formulario de Inicio de Sesión:
Se ha creado un formulario con campos para username y password, además de un botón que llama a la función login() al hacer clic.
Cada campo de entrada es obligatorio (required) para asegurar que se envíen los datos necesarios.
Función login:
Se creó la función login() en JavaScript para capturar el nombre de usuario y la contraseña ingresados y enviarlos al servidor usando fetch.
Fetch POST: El método POST envía los datos en formato JSON a api.php?action=login para su autenticación.
Validación de Respuesta: La función procesa la respuesta JSON del servidor. Si el inicio de sesión es exitoso, redirige al usuario a dashboard.html. En caso de error, se muestra un mensaje de alerta.
JSDoc: La función login está documentada con JSDoc para explicar su propósito y los datos de entrada.

2. Archivo dashboard.html
Este archivo gestiona las funciones del tablero principal, como la visualización, adición y eliminación de usuarios y clientes.
Cambios realizados:
Sección para Listado de Usuarios y Clientes:
Se agregaron secciones de encabezado y botones de agregar usuario/cliente en la interfaz del tablero.
Dos áreas se definen para mostrar listas de usuarios y clientes, donde cada listado se genera dinámicamente.
Modales para Agregar Usuarios y Clientes:
Se añadieron dos modales de Bootstrap para agregar usuarios y clientes. Estos formularios incluyen campos de nombre, dirección y otros datos específicos de cada entidad.
Funciones para Manejo de Usuarios:
fetchUsuarios(): Realiza una llamada a la API para obtener la lista de usuarios y muestra cada usuario en el DOM con un botón de eliminación.
addUser(): Envía los datos de usuario al servidor para crear un nuevo usuario, llama a fetchUsuarios para actualizar la lista y cierra el modal.
deleteUser(id): Envía una solicitud DELETE al servidor con el ID del usuario para eliminarlo y actualiza la lista de usuarios tras una respuesta exitosa.
Funciones para Manejo de Clientes:
fetchClientes(): Solicita al servidor la lista de clientes y actualiza el DOM con la lista de clientes.
addClient(): Envía los datos del nuevo cliente a la API, actualiza la lista de clientes y cierra el modal.
deleteClient(id): Envía una solicitud DELETE para eliminar un cliente usando su ID y actualiza la lista de clientes.
JSDoc:
Cada función de JavaScript está documentada usando JSDoc para explicar su objetivo y los parámetros que utiliza. Esto ayuda a mejorar la comprensión del código y facilita su mantenimiento.

3. Archivo api.php
Este archivo es la API que maneja el backend y proporciona soporte para el login, agregar, listar y eliminar usuarios y clientes.
Cambios realizados:
Estructura de Datos de Ejemplo:
Usuarios y Clientes: Se crearon arrays usuarios y clientes con datos de ejemplo para simular una base de datos de usuarios y clientes. Estos arrays permiten probar la funcionalidad sin una base de datos real.
Inicio de Sesión:
La API maneja el inicio de sesión mediante el endpoint POST en api.php?action=login.
Autenticación Básica: Se verifica que los datos enviados coincidan con credenciales específicas (username y password). Si coinciden, se inicia una sesión en PHP usando $_SESSION['loggedin'].
Operaciones de Usuario:
GET: Si la sesión está activa ($_SESSION['loggedin']), devuelve el listado de usuarios como JSON.
POST (Add): Cuando action=add en el endpoint, se agrega un nuevo usuario usando los datos enviados, y se actualiza el array usuarios.
DELETE: Elimina un usuario específico del array usuarios si se pasa su id en la solicitud.
Operaciones de Cliente:
GET: Cuando action=fetchClients, devuelve la lista de clientes.
POST (AddClient): Cuando action=addClient, agrega un nuevo cliente a la lista usando los datos enviados.
DELETE: Cuando action=deleteClient, elimina un cliente específico del array clientes según el id recibido.
JSDoc:
Se añadió documentación JSDoc en la API para cada endpoint y en el bloque switch. Explica cómo cada caso maneja una operación particular: creación, eliminación o autenticación de usuarios y clientes.
Esto facilita entender las responsabilidades de cada sección de código, incluso sin analizar cada línea.

Resumen Final
Con estos cambios:
Front-end (login.html, dashboard.html): Se han añadido formularios y botones necesarios, y se ha mejorado la experiencia del usuario con una interfaz sencilla. Además, cada acción está claramente documentada usando JSDoc, facilitando la comprensión de sus propósitos.
Back-end (api.php): La API simula la funcionalidad de un sistema de gestión de usuarios y clientes mediante arreglos. Las acciones para login, adición, eliminación y recuperación de datos están bien definidas, con mensajes claros y documentación de cada endpoint.
Este enfoque asegura un código mantenible, claro y escalable en el futuro, además de facilitar la comprensión gracias a la documentación en JSDoc en cada archivo.
