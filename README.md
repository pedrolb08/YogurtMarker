# Yogurt Batch - Pedro

API REST desarrollada con Spring Boot para gestionar la produccion de lotes de yogur. El proyecto permite crear recetas, iniciar lotes de produccion, consultar estados, registrar fallos y monitorear temperaturas durante el proceso.

## Tecnologias usadas

- Java 21
- Spring Boot 4
- Spring Web
- Spring Data JPA
- H2 Database
- Lombok
- Swagger / OpenAPI
- Maven

## Funcionalidades principales

- Gestion de recetas de yogur.
- Inicio de nuevos lotes usando una receta existente.
- Consulta de lotes por ID, estado o receta.
- Cambio y seguimiento del estado de produccion.
- Registro de lotes fallidos con motivo.
- Monitoreo de temperaturas y dashboard general.
- Documentacion interactiva con Swagger UI.

## Como ejecutar el proyecto

1. Clonar el repositorio:

```bash
git clone <url-del-repositorio>
cd <nombre-del-proyecto>
```

2. Ejecutar la aplicacion:

```bash
./mvnw spring-boot:run
```

En Windows:

```bash
mvnw.cmd spring-boot:run
```

3. Abrir la API en:

```text
http://localhost:8082
```

## Documentacion Swagger

La documentacion interactiva esta disponible en:

```text
http://localhost:8082/swagger-ui.html
```

Tambien se puede consultar el JSON de OpenAPI en:

```text
http://localhost:8082/v3/api-docs
```

## Base de datos H2

El proyecto usa una base de datos en memoria H2. La consola esta disponible en:

```text
http://localhost:8082/h2-console
```

Datos de conexion:

```text
JDBC URL: jdbc:h2:mem:yogurtdb
User: sa
Password:
```

## Endpoints principales

### Recetas

```http
GET    /api/recipes
GET    /api/recipes/{id}
POST   /api/recipes
PUT    /api/recipes/{id}
DELETE /api/recipes/{id}
GET    /api/recipes/active
GET    /api/recipes/search?keyword=natural
```

### Lotes

```http
GET  /api/batches
GET  /api/batches/{id}
POST /api/batches/start
GET  /api/batches/status/{status}
GET  /api/batches/recipe/{recipeId}
PUT  /api/batches/{id}/status
POST /api/batches/{id}/fail
```

Estados disponibles para un lote:

```text
PREPARING
HEATING
INNOCULATION
INCUBATING
COOLING
REFRIGERATING
COMPLETED
FAILED
```

### Monitoreo

```http
GET /api/monitoring/batches/active
GET /api/monitoring/batches/{batchId}/temperature
GET /api/monitoring/batches/{batchId}/temperature-logs
GET /api/monitoring/dashboard
```

## Ejemplo para iniciar un lote

```http
POST /api/batches/start
Content-Type: application/json
```

```json
{
  "recipeId": 1,
  "customMilkVolume": 10.0,
  "customStarterAmount": 0.5
}
```

## Ejemplo para marcar un lote como fallido

```http
POST /api/batches/1/fail
Content-Type: application/json
```

```json
{
  "reason": "Temperatura fuera del rango esperado"
}
```

## Pruebas

Para ejecutar las pruebas del proyecto:

```bash
./mvnw test
```

## Autor

Pedro Lopez
