# Definición de Esquema GraphQL

## Descripción
Este documento define el esquema GraphQL del sistema, incluyendo los tipos de datos, consultas disponibles y mutaciones para la gestión de usuarios y productos.

## Types

### Usuario
```graphql
type Usuario {
  id: ID!
  nombre: String!
  email: String!
  rol: String!
  createdAt: String!
}
```

### Producto
```graphql
type Producto {
  id: ID!
  nombre: String!
  precio: Float!
  stock: Int!
  categoria: String!
}
```

## Queries
```graphql
type Query {
  usuarios: [Usuario!]!
  usuario(id: ID!): Usuario
  productos: [Producto!]!
  producto(id: ID!): Producto
  productosPorCategoria(categoria: String!): [Producto!]!
}
```

## Mutations
```graphql
type Mutation {
  crearUsuario(nombre: String!, email: String!, rol: String!): Usuario!
  actualizarUsuario(id: ID!, nombre: String, email: String): Usuario!
  eliminarUsuario(id: ID!): Boolean!
  crearProducto(nombre: String!, precio: Float!, stock: Int!, categoria: String!): Producto!
  actualizarStock(id: ID!, stock: Int!): Producto!
}
```

## Ventajas sobre REST
- El cliente solicita exactamente los campos que necesita
- Una sola petición puede obtener datos relacionados
- Elimina el problema de over-fetching y under-fetching
