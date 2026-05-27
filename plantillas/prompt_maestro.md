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
