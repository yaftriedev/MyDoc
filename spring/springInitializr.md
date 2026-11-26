# Crear Proyecto Spring initializr

> [**Spring Initializr**](https://start.spring.io/) es un generador de proyectos que te permite crear la estructura base de una aplicación **Spring Boot**. Su objetivo es que empieces rápido, sin tener que configurar todo manualmente.

# **Lenguaje**

### **Java**
- Lenguaje base de la JVM, maduro y ampliamente soportado.
- Sintaxis más extensa, pero estable y con abundante documentación.
- Perfecto para proyectos grandes, empresas o principiantes.
- Es el **estándar por defecto** en Spring Boot.

### **Kotlin**
- Lenguaje moderno creado por JetBrains, totalmente compatible con Java.
- Más conciso, seguro frente a `NullPointerException` y expresivo.
- Funciona tanto para **Spring Boot** como para **Android**.
- Ideal para nuevos proyectos o equipos que buscan productividad.
- **Recomendado actualmente** junto con Java.

### **Groovy**
- Lenguaje dinámico sobre la JVM, más flexible y con sintaxis tipo script.
- Muy usado para **scripts y configuración de Gradle**.
- Menos común para aplicaciones grandes.
- Recomendado solo para tareas de automatización o scripts de build.

# **Sistema de construcción**

### **Maven**
- El sistema más clásico y extendido.
- Usa archivos XML (`pom.xml`) para definir dependencias y configuraciones.
- Muy estable, con excelente soporte en IDEs.
- Ideal para **proyectos estándar y principiantes**.
- Ejemplo de ejecución: `./mvnw spring-boot:run`

### **Gradle Kotlin**
- Igual que el anterior, pero usa **Kotlin** en lugar de Groovy (`build.gradle.kts`).
- Proporciona **autocompletado y chequeo de tipos** en IDEs.
- Recomendado para proyectos **en Kotlin** o para quienes prefieren tipado fuerte.
- Más moderno, aunque menos documentado que la versión Groovy.

### **Gradle Groovy**
- Usa el lenguaje **Groovy** para su archivo de configuración (`build.gradle`).
- Más compacto y flexible que Maven.
- Sintaxis menos rígida y más fácil de automatizar.
- Recomendado para quienes quieren **velocidad y personalización**.

# Packaging

### **`.jar` (Java ARchive)**
- Es un archivo ejecutable que **contiene todo el proyecto**, incluyendo un servidor embebido (Tomcat o Jetty).
- Permite ejecutar la app con un simple comando: `java -jar miapp.jar`
- Ideal para **microservicios**, **Spring Boot moderno** y despliegue sencillo.
- **Recomendado actualmente**.

### **`.war` (Web Application Archive)**
- Se usa para **desplegar en servidores de aplicaciones externos**, como Tomcat, WildFly o GlassFish.
- Requiere instalar y configurar el servidor por separado.
- Útil en **entornos empresariales antiguos** o donde ya se usa un servidor corporativo.
- Menos flexible y más pesado que `.jar`.

# **Dependencias**

| Tipo de aplicación | Dependencias recomendadas |
| --- | --- |
| **API REST / Web** | `Spring Web`, `Spring Boot DevTools` |
| **Con base de datos** | `Spring Data JPA`, `H2 Database` (o `MySQL Driver`) |
| **Seguridad / Login** | `Spring Security` |
| **Frontend y vistas** | `Thymeleaf` |
| **Pruebas** | `Spring Boot Starter Test` |

# Estructura generada
Al descargar el `.zip`, verás algo como esto:
- miapp/
    - src/
        - main/
            - java/com/ejemplo/miapp/
                - **`MiappApplication.java`** → clase principal con `@SpringBootApplication`, punto de entrada de la app.
            - resources/
                - **`application.properties`** → configuración general (puertos, base de datos, etc.).
                - static/
                - templates/
        - test/
            - java/com/ejemplo/miapp/
    - **`pom.xml` / `build.gradle`** → lista dependencias y configuración del proyecto.