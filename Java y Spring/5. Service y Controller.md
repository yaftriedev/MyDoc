# Service

> La capa **Service** contiene la **lógica de negocio**. Utiliza los repositorios (o DAOs) para obtener o modificar datos, y aplica reglas, validaciones o cálculos antes de devolver el resultado al controlador.

## Características

- Se anota con `@Service`.
- No accede directamente a la base de datos, sino a través del repositorio.
- Puede llamar a varios repositorios o servicios externos.
- Se comunica con los **controladores** y los **repositorios**.


```java
import org.springframework.stereotype.Service;

@Service
public class UserService {

    private final UserRepository userRepository;

    public UserService(UserRepository userRepository) {
        this.userRepository = userRepository;
    }

    public UserEntity createUser(UserEntity user) {
        if (user.getUsername().isEmpty()) {
            throw new IllegalArgumentException("El nombre no puede estar vacío");
        }
        return userRepository.save(user);
    }

    public UserEntity getUserById(Long id) {
        return userRepository.findById(id)
                .orElseThrow(() -> new RuntimeException("Usuario no encontrado"));
    }
}
```

# Estrcutura del Controller y Métodos Básicos

```java
@RestController
@RequestMapping("/url")
public class TasksRestController {
    
    // Import Repos
    
    @GetMapping
    public List<TasksModel> getTasks() {
        return Repo.findAll();
    }
    
    @PostMapping
    public TasksModel createTask(@RequestBody TasksModel task) {
        return tasksRepo.save(task);
    }
    
}
```
| Anotación | Significado |
|---|---|
| `@RestController` | Indica que esa clase es un controller |
| `@RequestMapping("/url")` |  Prefijo url para esa clase |
| `@GetMapping(url)`, `@PostMappin(url)`, … | Decoradores para metodos |
| `@ResponseStatus(HttpStatus.CODE)` | Permite definir el código http que se devolverá |
| `@RequestBody Type name` | Obtener json del body como una clase |
| `@RequestParam Type name` | Obtener argumentos  `?`  de la url |
| `@PathVariable Type name` | Permite obtener parametros url, en la url se indican con `{name}` |

# Response Entity
El término **`ResponseEntity`** se usa principalmente en **Spring Framework** (Java), dentro del módulo **Spring Web (Spring MVC)**.

> `public class ResponseEntity<T> extends HttpEntity<T>` es una clase genérica (`<T>`) que hereda de `HttpEntity`, y permite **personalizar completamente la respuesta HTTP** que un controlador envía al cliente.

### Sirve para **representar toda la respuesta HTTP**, incluyendo:
- El **código de estado HTTP → status code**
- Los **encabezados → headers**
- El **cuerpo → body**

### Usas `ResponseEntity` cuando necesitas **control total sobre la respuesta HTTP**.
- Personalizar códigos de estado (`201`, `404`, `500`, etc.)
- Agregar encabezados personalizados
- Devolver tipos de contenido específicos (`JSON`, `PDF`, `XML`, etc.)
- Controlar respuestas de errores o validaciones

| Contructores | Para que sirve |
|---|---|
| `ResponseEntity` | Crea la respuesta vacía, se define por métodos. |
| `ResponseEntity(HttpStatus status)` | Crea una respuesta sin cuerpo, solo con estado. |
| `ResponseEntity(T body, HttpStatus status)` | Crea una respuesta con cuerpo y estado. |

| Metodos | Para que sirve |
|---|---|
| `.status(HttpStatus status)` | Define el status |
| `.body(T body)` | Añade cuerpo a la respuesta y la construye. |
| `.build()` | Construye la respuesta sin cuerpo. |
| `.header(String name, String... values)` | Agrega encabezados personalizados. |
| `.headers(HttpHeaders headers)` | Agrega un objeto `HttpHeaders` completo. |

### **Códigos de estado HTTP**
Hay codigos que tienen su **propio método** para `ResponseEntity`
- 200 → `ResponseEntity.ok(body)`
- 202 → `ResponseEntity.accepted()`
- 204 → `ResponseEntity.noContent()`
- 400 → `ResponseEntity.badRequest()`
- 404 → `ResponseEntity.notFound()`