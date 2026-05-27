# Flujo Principal: Crear Usuario
1. El cliente envía un POST /users con los datos del usuario.
2. El sistema valida el payload.
3. Se verifica que el email no exista.
4. Se inserta el usuario en la base de datos.
5. Se devuelve 201 con el usuario creado.
