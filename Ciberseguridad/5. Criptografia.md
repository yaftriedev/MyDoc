# Criptografía

## Criptosistemas simétricos

El cifrado simétrico usa **la misma clave** para cifrar y descifrar. Es rápido y sirve para proteger datos almacenados y comunicaciones; el reto principal es compartir y proteger la clave.

### Tipos

| Tipo | Cómo funciona | Ventajas | Cuidados |
|---|---|---|---|
| **Cifrador de flujo** | Combina el texto con un flujo de bits mediante XOR. | Eficiente para datos continuos. | Emisor y receptor deben sincronizarse; no se debe reutilizar el mismo flujo con la misma clave. |
| **Cifrador de bloque** | Cifra bloques de datos de tamaño fijo mediante modos de operación. | Flexible y ampliamente utilizado. | Algunos modos requieren *padding*; hay que elegir bien el modo y gestionar correctamente el IV o *nonce*. |

### Modos de operación frecuentes

- **ECB:** cifra cada bloque por separado; revela patrones y debe evitarse.
- **CBC:** encadena bloques y utiliza un IV; requiere *padding*.
- **CTR:** combina un contador con un *nonce* y funciona como un cifrador de flujo.
- **AES-GCM:** modo moderno que ofrece confidencialidad e integridad.

### Algoritmos conocidos

| Algoritmo | Situación general |
|---|---|
| **AES** | Algoritmo de bloque moderno y ampliamente utilizado. |
| **ChaCha20** | Cifrador de flujo moderno; suele combinarse con Poly1305 para autenticar los datos. |
| **RC4, A5/1 y E0** | Algoritmos antiguos que no se recomiendan para usos nuevos. |
| **DES y 3DES** | Algoritmos obsoletos; se prefieren alternativas modernas como AES. |

### Ideas clave

- La clave secreta debe mantenerse protegida.
- Un **IV** o *nonce* ayuda a evitar que cifrar datos repetidos produzca siempre el mismo resultado.
- Los requisitos del IV o *nonce* dependen del modo: en muchos casos, como CTR y GCM, es fundamental **no reutilizarlo con la misma clave**.
- Para proteger comunicaciones modernas conviene usar cifrado autenticado, que protege tanto la confidencialidad como la integridad.

## Criptosistemas asimétricos

Utilizan un **par de claves relacionadas**: una pública, que puede compartirse, y una privada, que debe mantenerse secreta. No todas las operaciones son intercambiables: el cifrado, el intercambio de claves y las firmas son usos distintos.

| Técnica | Función principal | Idea básica |
|---|---|---|
| **Diffie–Hellman (DH)** | Acordar un secreto compartido | Dos partes intercambian valores públicos y calculan el mismo secreto sin enviarlo directamente. |
| **RSA** | Cifrado y firmas digitales | Se basa en operaciones con una clave pública y otra privada; su seguridad depende de la dificultad de factorizar ciertos números grandes. |
| **ECC** | Intercambio de claves y firmas | Usa operaciones sobre curvas elípticas para ofrecer seguridad comparable con claves más pequeñas. |

### Usos principales

- **Intercambio de claves:** establecer un secreto para luego cifrar la comunicación con criptografía simétrica, que suele ser más rápida.
- **Firmas digitales:** comprobar la autenticidad e integridad de un mensaje o documento.
- **Autenticación:** ayudar a verificar la identidad de servidores o usuarios, a menudo mediante certificados.

### Ejemplos de algoritmos

- **DH y ECDH:** acuerdos de claves; ECDH usa curvas elípticas.
- **RSA:** puede usarse para firmas y ciertos mecanismos de cifrado, siempre con esquemas seguros de implementación.
- **ECDSA:** firmas digitales basadas en curvas elípticas.
- **X25519:** intercambio de claves basado en curvas elípticas.
- **Curve25519 y secp256r1:** ejemplos de curvas usadas en distintos protocolos y aplicaciones.

### Ventajas y límites

- **Ventajas:** no hace falta compartir la clave privada; permite firmas y facilita establecer claves compartidas.
- **Límites:** suele ser más lento que el cifrado simétrico y requiere autenticar las claves públicas, por ejemplo mediante certificados.
- **En la práctica:** los protocolos suelen combinar técnicas asimétricas para establecer claves con cifrado simétrico para proteger los datos.

>**Nota:** Diffie–Hellman por sí solo no cifra mensajes ni confirma la identidad de las partes; necesita autenticación para evitar que un intermediario se haga pasar por una de ellas.

## Hashes, MAC, checksums y códigos correctores

| Mecanismo | Qué produce o utiliza | Para qué sirve | ¿Corrige errores? | ¿Da seguridad criptográfica? |
|---|---|---|---|---|
| **Hash criptográfico** | Resumen de longitud fija, sin clave | Comprobar integridad o identificar datos | No | Sí, si se usa un algoritmo vigente |
| **MAC** | Código calculado con una clave secreta compartida | Comprobar integridad y autenticidad del mensaje | No | Sí |
| **Checksum / CRC** | Valor calculado sobre los datos, normalmente sin clave | Detectar errores accidentales | No | No |
| **Código corrector de errores (ECC)** | Datos redundantes | Detectar y corregir ciertos errores | Sí, hasta cierto límite | No |

### Hashes

- Aceptan datos de cualquier tamaño y generan un resumen de tamaño fijo.
- Deben ser eficientes de calcular, pero difíciles de invertir y de encontrar colisiones.
- **SHA-256, SHA-384, SHA-512 y SHA-3** son ejemplos actuales.
- **MD5 y SHA-1** tienen debilidades y no se recomiendan para usos criptográficos nuevos.
- Para contraseñas no basta con aplicar un hash rápido: se usan funciones específicas, como **Argon2id**, con sal y parámetros de coste adecuados.
- Un hash público permite comprobar que los datos coinciden, pero **por sí solo no demuestra quién los creó**.

### MAC

- **HMAC** combina una función hash con una clave secreta.
- **CMAC** construye un MAC usando un cifrador de bloque.
- Permite verificar integridad y autenticidad entre quienes conocen la clave.
- No cifra el mensaje y, por sí solo, no evita ataques de repetición: para eso se suelen añadir números de secuencia, marcas de tiempo o *nonces*.

### Checksums y códigos correctores

- Un **checksum** o **CRC** detecta ciertos errores accidentales; no está diseñado para resistir modificaciones maliciosas.
- Los **códigos correctores**, como los de Hamming, añaden redundancia para localizar y corregir algunos errores. La cantidad que pueden corregir depende del código utilizado.

>**Idea clave:** hash = huella; MAC = huella con clave; checksum = detección básica de errores; código corrector = redundancia para reparar ciertos errores.