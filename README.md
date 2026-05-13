# Yogurt Batch - Pedro

Este proyecto es una API REST hecha con Spring Boot para manejar la produccion de lotes de yogur.

La idea principal es poder crear recetas, iniciar lotes, consultar su estado y revisar informacion de monitoreo como temperaturas y lotes activos.

## Tecnologias

- Java 21
- Spring Boot
- Spring Data JPA
- H2 Database
- Lombok
- Swagger
- Maven

## Que hace el proyecto

- Permite gestionar recetas de yogur.
- Permite crear lotes de produccion.
- Permite buscar lotes por estado, receta o ID.
- Permite marcar un lote como fallido.
- Tiene endpoints de monitoreo para ver temperaturas y resumen general.

## Como ejecutar

Primero se debe ejecutar el proyecto con Maven:

```bash
./mvnw spring-boot:run
```

En Windows:

```bash
mvnw.cmd spring-boot:run
```

La aplicacion corre en:

```text
http://localhost:8082
```

## Swagger

Para probar los endpoints desde el navegador:

```text
http://localhost:8082/swagger-ui.html
```

## Base de datos

El proyecto usa H2 en memoria. La consola esta en:

```text
http://localhost:8082/h2-console
```

Datos:

```text
JDBC URL: jdbc:h2:mem:yogurtdb
Usuario: sa
Password:
```

## Endpoints principales

```text
/api/recipes
/api/batches
/api/monitoring
```

## Pruebas

Para correr las pruebas:

```bash
./mvnw test
```

## Autor

Pedro Lopez
