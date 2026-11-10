# Spring Security
Framework de Spring que permite gestionar la autenticación y autorización de una aplicación. Proporciona mecanismos para proteger endpoints, controlar el acceso a recursos y prevenir accesos no autorizados mediante filtros y reglas de seguridad.

# Características e importancia general
Spring Security permite implementar un sistema de seguridad robusto mediante la autenticación de usuarios, la gestión de permisos y roles, el cifrado de contraseñas y la validación de tokens. Su importancia radica en proteger la información y garantizar que cada usuario acceda únicamente a los recursos permitidos.

# Gestión de Contraseñas con BCrypt
BCrypt es un algoritmo de hashing utilizado para almacenar contraseñas de forma segura. Incorpora un salt y un factor de coste configurable, lo que dificulta los ataques de fuerza bruta. Las contraseñas se verifican comparando el hash almacenado con la contraseña introducida, sin necesidad de descifrarlas.

```java
private static final BCryptPasswordEncoder encoder = new BCryptPasswordEncoder();
```

```java
// Encodear la Contraseña (String)
encoder.encode(password);

// Verificar la Contraseña (Boolean)
encoder.matches(password, hash);
```

# Gestión de Tokens JWT
Los JSON Web Tokens (JWT) permiten gestionar la autenticación mediante tokens que contienen información y declaraciones (claims) del usuario. Se generan tras una autenticación correcta y permiten verificar la identidad del usuario en solicitudes posteriores, sin necesidad de mantener una sesión tradicional en el servidor.

```java
// Convertir la conotraseña a Bytes
private static final SecretKey key = Keys.hmacShaKeyFor(SECRET_KEY.getBytes(StandardCharsets.UTF_8));
```

### Generar el Token con `Jwts.builder()`

| Método | Argumento  | Para qué sirve  | Ejemplo |
|---|---|---|---|
| `.subject()` | `String` | Identidad principal del token | `.subject("user@example.com")` |
| `.claim()` | `String, Object` | Añadir un dato personalizado | `.claim("role", "ADMIN")` |
| `.claims()` | `Map<String,Object>` | Añadir varios datos personalizados | `.claims(data)` |
| `.issuedAt()` | `Date` | Fecha de creación | `.issuedAt(new Date())` |
| `.expiration()` | `Date` | Fecha de expiración | `.expiration(new Date(...))` |
| `.signWith()` | `SecretKey` | Firmar el JWT | `.signWith(key)` |
| `.compact()` | — | Generar el JWT final | `.compact()` |

### Obtener datos del Token

```java
// Obtener el payload de los datos
Claims claims = Jwts.parser()
            .verifyWith(key)
            .build()
            .parseSignedClaims(token)
            .getPayload();
```

```java
// Obtener el Subject
String subject = claims.getSubject();

// Obtener un claim
Type claim = claims.get("propety", Type.class);
```

# Filter JWT
Filtro encargado de interceptar las solicitudes HTTP para extraer y validar el token JWT enviado normalmente en la cabecera Authorization. Si el token es válido, establece la autenticación del usuario en el contexto de seguridad de Spring, permitiendo que las reglas de autorización determinen el acceso.

```java
// Obtener el Authorization del Header
String header = request.getHeader("Authorization");

// Verificar el header
header == null || !header.startsWith("Bearer ")

// Obtener el Token
String jwt = header.substring(7).trim();
```

```java
// Crear el Authentication
UsernamePasswordAuthenticationToken authentication = new UsernamePasswordAuthenticationToken(
        userDetails, null, userDetails.getAuthorities()
    );

// Establecer el context
SecurityContextHolder.getContext().setAuthentication(authentication);
```

## Ejemplo
```java
@Component 
public class FilterJWT extends OncePerRequestFilter {

    @Override
    protected void doFilterInternal(
        HttpServletRequest request,
        HttpServletResponse response,
        FilterChain filterChain
    ) throws ServletException, java.io.IOException {

        String header = request.getHeader("Authorization");

        if (header != null && header.startsWith("Bearer ")) {
            String token = header.substring(7);

            if (!AuthUtil.verifyToken(token)) {
                throw new badToken();
            }

            var authentication = new UsernamePasswordAuthenticationToken(
                    AuthUtil.getDataFromToken(token),
                    null,
                    Collections.emptyList()
                );

            SecurityContextHolder
                .getContext()
                .setAuthentication(authentication);
        }

        filterChain.doFilter(request, response);
    }
}
```

# Configurar Acceso
Consiste en definir las reglas de autorización para los endpoints de la aplicación mediante SecurityFilterChain. Permite establecer rutas públicas, rutas protegidas y restricciones basadas en roles o permisos, garantizando que solo los usuarios autorizados puedan acceder a determinados recursos.

```java
@Configuration
public class SecurityConfig {

    @Bean 
    SecurityFilterChain securityFilterChain(
        HttpSecurity http, FilterJWT FilterJWT
    ) throws Exception {
        http
            .csrf(csrf -> csrf.disable())
            .authorizeHttpRequests(auth -> auth
                .requestMatchers("/route/**").permitAll()
                .anyRequest().authenticated()
            )
            .addFilterBefore(
                FilterJWT,
                UsernamePasswordAuthenticationFilter.class
            );

        return http.build();
    }

}
```

- `.csrf(csrf -> csrf.disable())`: Desactiva la protección CSRF (Cross-Site Request Forgery).
- `.authorizeHttpRequests(auth -> auth)`: Crear las rutas permitidas y denegadas.
- `.requestMatchers("/route/**")`: Definir la ruta o rango de rutas.
    - `.permitAll()`: Permitir la ruta
    - `authenticated()`: Requiere autentificacion la ruta
    - `.denyAll()`: Denegar la ruta
- ``
- `.addFilterBefore( FilterJWT, UsernamePasswordAuthenticationFilter.class)`; Registro del filtro JWT

# Acceder a los Datos del Token
Una vez autenticado el usuario, los datos incluidos en el token —como el identificador, el nombre de usuario o los roles— pueden consultarse desde los controladores. Con Spring Security y JWT, una opción es recibir el token como argumento

```java
// Usando Authentication authentication
@GetMapping("/privado")
public String privado(Authentication authentication) {
    UserDetails userDetails = (UserDetails) authentication.getPrincipal();
    return userDetails.getUsername();
}
```

```java
// Usando @AuthenticationPrincipal
@GetMapping("/privado")
public String privado(@AuthenticationPrincipal UserDetails userDetails) {
    return userDetails.getUsername();
}
```