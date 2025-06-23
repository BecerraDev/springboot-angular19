# Prueba Técnica - Desarrollador Java

## Descripción

Proyecto full-stack que implementa un catálogo de productos con:

- Backend en **Java 17 + Spring Boot 3**  
- Frontend en **Angular 19**  
- Autenticación con **Keycloak 26**  
- Persistencia en **PostgreSQL**  
- Contenedores orquestados con **Docker Compose**  

Incluye autenticación basada en roles y pruebas unitarias para frontend y backend.

---

## Tecnologías utilizadas

- Java 17  
- Spring Boot 3  
- Angular 19  
- PostgreSQL  
- Keycloak 26  
- Docker / Docker Compose  
- Jasmine (Frontend)  
- JUnit 5 + Mockito (Backend)  

---

## Cómo levantar el entorno

### 1. Clonar el repositorio

```bash
git clone https://github.com/BecerraDev/springboot-angular19.git
cd springboot-angular19
```

### 2. Iniciar el entorno de desarrollo
```bash
docker-compose up --build
```
Esto levantará: 
PostgreSQL en localhost:5432
Keycloak en http://localhost:8180
Backend Spring Boot en http://localhost:8080
Frontend Angular en modo desarrollo (ng serve) en http://localhost:4200

⚠️ El frontend corre en modo desarrollo con ng serve por temas de compilación y tiempo. No se usa Nginx. 

### 3. Acceso a la aplicación

Cuando accedes a http://localhost:4200, serás redirigido automáticamente a Keycloak para autenticación.

Usuario:	usuario
Contraseña: usuario

Una vez logueado, se accede al Realm miapp y se redirige a /productos, donde se visualiza la tabla con: Paginador, Búsqueda de productos y Filtros


