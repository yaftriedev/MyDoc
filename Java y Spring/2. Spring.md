# Spring
- **Spring**: Modulos y Funcionalidades
- **Spring Core**: Inyección de dependencias (IoC)
- **Spring Boot**: Simplifica la configuración y despliegue
- **Spring MVC**: Crea APIs REST y controladores web
- **Spring Data JPA**: Conecta con bases de datos fácilmente
- **Spring Security**: Autenticación y autorización
- **Spring Cloud**: Microservicios y configuración distribuida

# Funciones de cada capa (MVC)
- **Controller**: Recibe peticiones HTTP y responde con DTOs.
    - Usa Service o Repository, envía/recibe DTOs
    - Métodos como getUser(), createUser()
- **Service**: donde va la lógica de negocio (usa los repositorios).
    - Llama a Repository, usa DTOs y Entities
    - Validar datos, procesar información
- **Repository**: versión moderna de DAO (Spring Data JPA).
    - Devuelve o guarda Entities
    - Métodos findAll(), save(), findById()
## Datos y ORM
- **DTO**: Transfiere solo los datos necesarios entre capas o hacia el cliente.
    - Usado por Controller y Service
    - Campos como username, email (sin password, etc.)
- **Entity**: Representa las tablas de la base de datos.
    - Usada por Repository
    - Campos como id, username, email

# Arquitectura Hexagonal
| *El dominio no conoce nada del exterior. Todo acceso externo entra por puertos y sale por adaptadores.*

- **Domain (núcleo)**
    - `/domain/entities`: Representan el negocio
        - Contienen reglas invariantes Ejemplo: User, Order, Invoice Tecnologías: Clases puras Entidades DDD
    - `/domain/value_objects`: Valores inmutables
        - Validaciones propias Ejemplo: Email, Money, Identifier
    - `/domain/services`: Lógica de negocio compleja
    - `/domain/ports` (puertos de dominio): Definen interfaces
        - Expresan lo que el dominio necesita del exterior Ejemplos: UserRepositoryPort, PaymentGatewayPort Tecnologías: Interfaces, Abstract classes
- **Application (casos de uso)**
    - `/application/use_cases`: Orquestan el flujo del negocio
        - Ejecutan una acción concreta del sistema Ejemplos CreateUser, PayOrder, GenerateInvoice No contienen: HTTP, SQL, Frameworks
    - `application/ports`: Puertos de entrada
        - Definen cómo se invoca un caso de uso Ejemplos: CreateUserInputPort, PayOrderInputPort
- **Infrastructure (exterior)**
    - `/infrastructure/adapters/in (adaptadores de entrada)`: Traducen peticiones externas al sistema
        - Controllers, Listeners, CLI handlers Tecnologías: REST, GraphQL, gRPC, Mensajería

    - `/infrastructure/adapters/out` (adaptadores de salida): Conectan con sistemas externos 
        - Base de datos, APIs externas, Cache, Email Tecnologías: ORMs, SQL / NoSQL, HTTP clients, Message brokers

    - `/infrastructure/config`: Inyección de dependencias, Configuración técnica, Wiring de puertos y adaptadores

## Cuándo usar arquitectura hexagonal
- Sistemas grandes
- Microservicios
- Alta mantenibilidad
- Tests de negocio sin infraestructura
- Cambios frecuentes de tecnología