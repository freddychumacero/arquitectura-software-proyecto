# Diseño de Endpoints REST

## Base URL
`https://api.misistema.com/v1`

## Recursos y Endpoints

### Usuarios

| Método | Endpoint | Descripción |
|--------|----------|-------------|
| GET | /usuarios | Obtiene la lista de usuarios |
| GET | /usuarios/:id | Obtiene un usuario por ID |
| POST | /usuarios | Crea un nuevo usuario |
| PUT | /usuarios/:id | Actualiza un usuario existente |
| DELETE | /usuarios/:id | Elimina un usuario |

### Ejemplo de Respuesta GET /usuarios/:id
```json
{
  "id": 1,
  "nombre": "Juan Pérez",
  "email": "juan@email.com",
  "rol": "admin",
  "createdAt": "2026-01-15T10:30:00Z"
}
```

## Códigos de Respuesta

| Código | Significado |
|--------|-------------|
| 200 | OK - Solicitud exitosa |
| 201 | Created - Recurso creado |
| 400 | Bad Request - Error en la solicitud |
| 404 | Not Found - Recurso no encontrado |
| 500 | Internal Server Error |

## Autenticación
La API utiliza tokens JWT en el header Authorization: `Bearer <token>`
