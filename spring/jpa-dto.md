# Entity
Una **Entity** representa una **tabla de la base de datos**. Se usa con **JPA (Java Persistence API)** y está **mapeada directamente** a una tabla relacional.

## Características
- Se anota con `@Entity`.
- Suele tener una clave primaria (`@Id`).
- Puede tener relaciones (`@OneToMany`, `@ManyToOne`, etc.).
- Se usa **solo en la capa de persistencia**.

```java
import jakarta.persistence.*;

import lombok.*;

@Entity
@Table(name = "users")
@NoArgsConstructor 
@AllArgsConstructor 
@Setter 
@Getter
public class UserEntity {
	@Id
	@GeneratedValue(strategy = GenerationType.IDENTITY)
	private Long id;
	
	private String username;
	private String email;

}
```

# DTO (Data Transfer Object)

Un **DTO** es un **objeto de transferencia de datos. S**irve para **enviar o recibir información** entre capas (por ejemplo, entre el backend y el frontend).

## Características

- **No está mapeado a la base de datos.**
- Se usa para **exponer solo los datos necesarios**.
- Mejora la **seguridad**, **rendimiento** y **mantenibilidad**.
- Puede ser diferente a la entidad (por ejemplo, incluir datos combinados o calculados).

```java
import lombok.*;

@NoArgsConstructor 
@AllArgsConstructor 
@Setter 
@Getter
public class UserDTO {
    private String username;
    private String email;
}
```

# Repository

Un **Repository** es una **abstracción moderna del patrón DAO**, proporcionada por **Spring Data JPA**. Se encarga de acceder a la base de datos **sin necesidad de escribir SQL o código repetitivo**.

## Características

- Define una **interfaz**, no una clase.
- Hereda de `JpaRepository`, `CrudRepository` o similares.
- Spring genera automáticamente la implementación.
- Permite definir métodos personalizados (por nombre o con `@Query`).

```java
import org.springframework.data.jpa.repository.JpaRepository;
import org.springframework.stereotype.Repository;

@Repository
public interface EntityNameRepository extends JpaRepository<EntityName, Long> {
    // Funciones extra
    Optional<EntityName> findByField(Type field);
}
```