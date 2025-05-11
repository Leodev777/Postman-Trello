# Postman-Trello

# 🧪 API Testing con Postman – Flujo Trello

Este proyecto simula un flujo completo de gestión de tareas en un tablero de Trello mediante una colección de API tests en **Postman**. Está orientado a la validación funcional de historias de usuario, automatizando las operaciones clave como creación, consulta, actualización, cambio de estado y eliminación de tarjetas.

📹 **Video del CRUD funcionando:**  
[🔗 Ver video en Google Drive](https://drive.google.com/file/d/1NkLBx4ahmYxwRwyYrqwuMhPyqt4-2akh/view?usp=sharing)

---

## 🚀 Objetivo del Proyecto

> Diseñar y automatizar un flujo de trabajo tipo Kanban utilizando la API pública de Trello.  
El objetivo es simular el ciclo de vida completo de una tarjeta, desde su creación hasta su eliminación, asegurando que todas las validaciones funcionales pasen exitosamente.

---

## 🧩 Funcionalidades Automatizadas

| Etapa                     | Método | Descripción                                         |
|--------------------------|--------|-----------------------------------------------------|
| ① Crear tarjeta          | POST   | Crea una nueva tarjeta en una lista específica.     |
| ② Verificar tarjeta      | GET    | Consulta y valida la existencia de la tarjeta.      |
| ③ Actualizar contenido   | PUT    | Agrega Historia de Usuario y Criterios de Aceptación. |
| ④ Validar actualización  | GET    | Verifica que los datos modificados sean correctos.  |
| ⑤ Cambiar de estado      | PUT    | Mueve la tarjeta a otra lista (posición).           |
| ⑥ Eliminar tarjeta       | DELETE | Elimina la tarjeta creada.                          |

---

## ⚙️ Variables de Entorno Necesarias

Configurar un ambiente en Postman con las siguientes variables antes de ejecutar:

| Variable     | Descripción                        | Ejemplo                                  |
|--------------|------------------------------------|------------------------------------------|
| `key`        | API Key de Trello                  | (requerido, pedir manualmente)           |
| `token`      | Token de autenticación personal    | (requerido, pedir manualmente)           |
| `URLBase1`   | URL base de la API de Trello       | `https://api.trello.com/1`               |
| `cards`      | Path del endpoint de tarjetas      | `cards`                                  |
| `IdList`     | ID de la lista destino             | `68001f9be7a5813a0f4df920`               |
| `idCard`     | ID de tarjeta dinámico             | Se asigna automáticamente al crear       |

---

## 📄 Validaciones en los Test

Ejemplos de test incluidos en la colección:

```javascript
pm.test("Status 200", () => {
    pm.response.to.have.status(200);
});

pm.test("La tarjeta contiene la palabra 'leonardo'", () => {
    const body = pm.response.json();
    pm.expect(body.desc).to.include("leonardo");
});
