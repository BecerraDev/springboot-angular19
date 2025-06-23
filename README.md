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

```bash
PostgreSQL en 
localhost:5432

Keycloak en 
http://localhost:8180

Backend Spring Boot en
http://localhost:8080

Frontend Angular en modo desarrollo (ng serve) en h
http://localhost:4200 -> entrar aquí.
```

⚠️ El frontend corre en modo desarrollo con ng serve por temas de compilación y tiempo. No se usa Nginx. 
⚠️ Recordar tener docker corriendo en segundo plano.

### 3. Acceso a la aplicación

Cuando accedes a http://localhost:4200, serás redirigido automáticamente a Keycloak para autenticación.

```bash
Usuario:	usuario
Contraseña: usuario
```

Una vez logueado, se accede al Realm miapp y se redirige a /productos, donde se visualiza la tabla con: Paginador, Búsqueda de productos y Filtros


### 4. Iniciar el entorno de test
```bash
docker-compose -f docker-compose-test.yml up --build
```
Para acceder al test manual de frontend> comando : ng test
Para acceder al test manual de backend> comando : mvn clean test

### 5. 

### Nota sobre tiempos de generación de imágenes

Tener en cuenta que la primera vez que ejecutes los comandos `docker-compose up --build` o `docker-compose -f docker-compose-test.yml up --build`, la construcción de las imágenes puede tardar varios minutos. 

Esto se debe a que:

- Se instalan las dependencias de backend y frontend desde cero.
- El frontend Angular ejecuta la compilación en modo desarrollo (ng serve), lo cual puede consumir más tiempo.
- Descarga y configuración de las imágenes base (PostgreSQL, Keycloak, etc.)

Una vez que veas en los logs que Keycloak ha terminado de cargar y se puede acceder, significa que el servicio está listo y la aplicación está disponible para usarse.




### SI SURGEN ERRORES ###
Contactarme por este medio 
. Contacto: (+56) 9 5606 4816 (Móvil)
. Correo: byron.becerra.aravena@gmail.com

## 1. Si miapp no funciona, o no se puede acceder a localhost:4200
  
Abrir en el navegador: http://localhost:8180/admin/master/console/
Iniciar sesión con las credenciales admin (por defecto admin/admin si no cambiaste). En el panel de administración, crear un nuevo realm con el nombre "miapp" y el cliente "frontend".

## 2. Base de datos no conecta local.

Se implemento H2 para realizar test unitarios y no tener que cambiar la base de datos durante pruebas. Si POSTGRESQL falla, corregir los datos de application-dev.yml (backend) con los datos correctos de tú usuario.  

## 3. Migraciones fallan.

El script de Docker debería ejecutar las migraciones según el orden del db.changelog-master.yml. A veces puede pasar que Docker corrompa las migraciones, dejando alguna en proceso y bloqueando las siguientes.

Para solucionarlo, borra la caché de la base de datos local, baja los contenedores con docker-compose down y luego levanta todo de nuevo con docker-compose up --build.

## 4. Backend no funciona (problema target). 

Para que el backend funcione, necesitas el JAR en target/ (ej: catalog-0.0.1-SNAPSHOT.jar).
Ejecuta dentro de backend: mvn clean package


