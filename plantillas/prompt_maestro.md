
# Caso de Prueba: Crear Usuario Correctamente

## ID
TC-001

## Descripción
Validar que el sistema permita crear un usuario válido cumpliendo los requerimientos REQ-01 y los criterios de aceptación CA1.

## Precondiciones
- Token JWT válido.
- El email no debe existir en la base de datos.
- Conexión estable con PostgreSQL.

## Datos de Entrada
POST /users  
Payload:
{
  "email": "nuevo@example.com",
  "password": "12345678"
}

## Pasos
1. Autenticarse y obtener un token JWT válido.
2. Enviar una solicitud POST /users con el payload válido.
3. Verificar que el sistema valide el payload.
4. Verificar que el email no exista previamente.
5. Validar que el usuario sea insertado en la base de datos.
6. Validar que se genere un log de auditoría.
7. Validar que la API responda con código 201.
8. Validar que la respuesta contenga id, email y created_at.

## Resultado Esperado
- Código HTTP 201.
- Respuesta:
  {
    "id": "uuid",
    "email": "nuevo@example.com",
    "created_at": "timestamp"
  }
- Registro creado en la tabla users.
- Log de auditoría generado.

## Criterios de Aceptación Cubiertos
- CA1

## Notas Técnicas
- Validar formato del timestamp.
- Validar que el password no se retorne en la respuesta.

---

# Caso de Prueba: Email Duplicado

## ID
TC-002

## Descripción
Validar que el sistema no permita crear un usuario con un email ya registrado, cumpliendo REQ-02 y CA2.

## Precondiciones
- Token JWT válido.
- El email ya existe en la base de datos.
- Conexión estable con PostgreSQL.

## Datos de Entrada
POST /users  
Payload:
{
  "email": "existente@example.com",
  "password": "12345678"
}

## Pasos
1. Autenticarse y obtener un token JWT válido.
2. Enviar una solicitud POST /users con un email ya registrado.
3. Verificar que el sistema valide el payload.
4. Verificar que el email ya existe en la base de datos.
5. Validar que la API responda con código 409.

## Resultado Esperado
- Código HTTP 409.
- No se crea registro en la tabla users.
- No se genera log de auditoría de creación.

## Criterios de Aceptación Cubiertos
- CA2

## Notas Técnicas
- Validar que el mensaje de error sea claro.

---

# Caso de Prueba: Payload Inválido

## ID
TC-003

## Descripción
Validar que el sistema rechace la creación de usuario si falta un campo obligatorio, cumpliendo REQ-01 y CA3.

## Precondiciones
- Token JWT válido.
- Conexión estable con PostgreSQL.

## Datos de Entrada
POST /users  
Payload:
{
  "email": "sinpassword@example.com"
}

## Pasos
1. Autenticarse y obtener un token JWT válido.
2. Enviar una solicitud POST /users con un campo obligatorio faltante.
3. Verificar que el sistema valide el payload.
4. Validar que la API responda con código 400.

## Resultado Esperado
- Código HTTP 400.
- No se crea registro en la tabla users.
- No se genera log de auditoría de creación.

## Criterios de Aceptación Cubiertos
- CA3

## Notas Técnicas
- Validar que el mensaje de error sea claro.

---

# Caso de Prueba: Error en Base de Datos

## ID
TC-004

## Descripción
Validar que el sistema responda correctamente ante un error inesperado en la base de datos.

## Precondiciones
- Token JWT válido.
- Conexión inestable o error simulado en PostgreSQL.

## Datos de Entrada
POST /users  
Payload:
{
  "email": "nuevo2@example.com",
  "password": "12345678"
}

## Pasos
1. Autenticarse y obtener un token JWT válido.
2. Simular un error en la base de datos.
3. Enviar una solicitud POST /users con el payload válido.
4. Validar que la API responda con código 500.

## Resultado Esperado
- Código HTTP 500.
- No se crea registro en la tabla users.
- No se genera log de auditoría de creación.

## Criterios de Aceptación Cubiertos
- N/A

## Notas Técnicas
- Validar que el mensaje de error sea claro y no exponga detalles sensibles.
