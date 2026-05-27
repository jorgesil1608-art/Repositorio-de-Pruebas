# Caso de Prueba: Crear Usuario Correctamente

## ID
TC-001

## Descripción
Validar que el sistema permita crear un usuario válido cumpliendo los requerimientos REQ-01 y CA1.

## Precondiciones
- Token JWT válido.
- El email no debe existir en la BD.

## Pasos
1. Enviar POST /users con:
   {
     "email": "nuevo@example.com",
     "password": "12345678"
   }
2. Validar que el sistema procese la solicitud.
3. Validar que el usuario se inserte en la BD.
4. Validar que se genere un log de auditoría.

## Resultado Esperado
- Código 201.
- Respuesta contiene:
  {
    "id": "uuid",
    "email": "nuevo@example.com",
    "created_at": "timestamp"
  }
- Registro creado en la tabla users.
- Log generado.

## Criterios de Aceptación Cubiertos
- CA1
