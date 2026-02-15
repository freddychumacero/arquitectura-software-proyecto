# Diagrama de Arquitectura del Sistema

## Vista General
```
┌─────────────────────────────────────────────┐
│              CLIENTES                        │
│  ┌─────────────┐    ┌─────────────┐         │
│  │  App Web     │    │  App Móvil  │         │
│  │  (React)     │    │(React Native)│        │
│  └──────┬───────┘    └──────┬──────┘         │
└─────────┼───────────────────┼────────────────┘
          │                   │
          ▼                   ▼
┌─────────────────────────────────────────────┐
│              API GATEWAY                     │
│  - Autenticación JWT                         │
│  - Rate Limiting                             │
│  - Logging y Monitoreo                       │
└──────────┬──────────────────┬────────────────┘
           │                  │
           ▼                  ▼
┌──────────────────┐ ┌──────────────────┐
│   REST API       │ │  GraphQL API     │
│  /api/v1/        │ │  /graphql        │
│  - Endpoints CRUD│ │  - Queries       │
│  - Validación    │ │  - Mutations     │
└────────┬─────────┘ └────────┬─────────┘
         │                    │
         ▼                    ▼
┌─────────────────────────────────────────────┐
│           BASE DE DATOS                      │
│           PostgreSQL                         │
│  - Tabla: usuarios                           │
│  - Tabla: productos                          │
│  - Tabla: pedidos                            │
└─────────────────────────────────────────────┘
```

## Componentes

### 1. Capa de Presentación
- **App Web (React):** Interfaz para usuarios de escritorio
- **App Móvil (React Native):** Interfaz optimizada para dispositivos móviles

### 2. API Gateway
- Punto de entrada único para todas las solicitudes
- Maneja autenticación mediante tokens JWT
- Implementa rate limiting para proteger los servicios
- Registra logs de todas las peticiones

### 3. Capa de Servicios
- **REST API:** Endpoints tradicionales para operaciones CRUD estándar
- **GraphQL API:** Consultas flexibles que permiten al cliente solicitar solo los datos necesarios

### 4. Capa de Datos
- **PostgreSQL:** Base de datos relacional para persistencia de información

## Flujo de Datos
1. El cliente envía una solicitud al API Gateway
2. El Gateway valida el token JWT y aplica rate limiting
3. La solicitud se enruta al servicio correspondiente (REST o GraphQL)
4. El servicio consulta la base de datos y devuelve la respuesta
5. La respuesta viaja de vuelta al cliente
