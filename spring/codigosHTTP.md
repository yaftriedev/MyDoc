# Codigos HTTP

## Codigos más utilizados

| Código | Body | Uso | `HttpStatus` |
| --- | --- | --- | --- |
| 200 | ✅ | Respuesta exitosa estándar con datos. | `OK` |
| 201 | ✅ | Recurso creado (ej. `POST`). | `CREATED` |
| 202 | ✅ | Petición aceptada, pero aún no procesada. | `ACCEPTED` |
| 204 | ❌ | Operación exitosa sin cuerpo (ej. `DELETE`). | `NO_CONTENT` |
| 301 | ❌ | Recurso movido de forma permanente. | `MOVED_PERMANENTLY` |
| 302 | ❌ | Recurso temporalmente en otra URL. | `FOUND` |
| 400 | ✅ | Petición inválida (datos erróneos). | `BAD_REQUEST` |
| 401 | ✅ | No autenticado o token inválido. | `UNAUTHORIZED` |
| 403 | ✅ | Acceso denegado, sin permisos. | `FORBIDDEN` |
| 404 | ❌ | Recurso no encontrado. | `NOT_FOUND` |
| 500 | ✅ | Error interno no controlado. | `INTERNAL_SERVER_ERROR` |

## Codigo `1**` — Informativos

| Código | Body | Uso | `HttpStatus` |
| --- | --- | --- | --- |
| 100 | ❌ | Indica que el cliente puede continuar con la solicitud. | `CONTINUE` |
| 101 | ❌ | El servidor cambia de protocolo (ej. WebSocket). | `SWITCHING_PROTOCOLS` |
| 102 | ❌ | Procesamiento en curso (WebDAV). | `PROCESSING` |
| 103 | ❌ | Sugerencias de recursos antes de la respuesta final. | `EARLY_HINTS` |

## Codigo `2**` — Éxito

| Código | Body | Uso | `HttpStatus` |
| --- | --- | --- | --- |
| 200 | ✅ | Respuesta exitosa estándar con datos. | `OK` |
| 201 | ✅ | Recurso creado (ej. `POST`). | `CREATED` |
| 202 | ✅ | Petición aceptada, pero aún no procesada. | `ACCEPTED` |
| 203 | ✅ | Información modificada por un proxy. | `NON_AUTHORITATIVE_INFORMATION` |
| 204 | ❌ | Operación exitosa sin cuerpo (ej. `DELETE`). | `NO_CONTENT` |
| 205 | ❌ | Indica que el cliente debe reiniciar el formulario. | `RESET_CONTENT` |
| 206 | ✅ | Respuesta parcial (rango de bytes). | `PARTIAL_CONTENT` |
| 207 | ✅ | Varias operaciones (WebDAV). | `MULTI_STATUS` |
| 208 | ✅ | Elemento ya reportado (WebDAV). | `ALREADY_REPORTED` |
| 226 | ✅ | Resultado de una operación delta HTTP. | `IM_USED` |

## Codigo `3**` — Redirecciones

| Código | Body | Uso | `HttpStatus` |
| --- | --- | --- | --- |
| 300 | ❌ | Múltiples opciones de recurso. | `MULTIPLE_CHOICES` |
| 301 | ❌ | Recurso movido de forma permanente. | `MOVED_PERMANENTLY` |
| 302 | ❌ | Recurso temporalmente en otra URL. | `FOUND` |
| 303 | ❌ | Redirección tras `POST` a `GET`. | `SEE_OTHER` |
| 304 | ❌ | Caché válida, sin cambios. | `NOT_MODIFIED` |
| 305 | ❌ | (Obsoleto) Usar proxy específico. | `USE_PROXY` |
| 307 | ❌ | Redirección temporal. | `TEMPORARY_REDIRECT` |
| 308 | ❌ | Redirección permanente sin cambiar método HTTP. | `PERMANENT_REDIRECT` |

## Codigo` 4**` — Errores del cliente

| Código | Body | Uso | `HttpStatus` |
| --- | --- | --- | --- |
| 400 | ✅ | Petición inválida (datos erróneos). | `BAD_REQUEST` |
| 401 | ✅ | No autenticado o token inválido. | `UNAUTHORIZED` |
| 402 | ✅ | Reservado (pagos futuros). | `PAYMENT_REQUIRED` |
| 403 | ✅ | Acceso denegado, sin permisos. | `FORBIDDEN` |
| 404 | ❌ | Recurso no encontrado. | `NOT_FOUND` |
| 405 | ❌ | Método HTTP no permitido. | `METHOD_NOT_ALLOWED` |
| 406 | ❌ | Tipo de respuesta no aceptado. | `NOT_ACCEPTABLE` |
| 407 | ✅ | Autenticación de proxy requerida. | `PROXY_AUTHENTICATION_REQUIRED` |
| 408 | ❌ | Tiempo de espera excedido. | `REQUEST_TIMEOUT` |
| 409 | ✅ | Conflicto de estado (ej. duplicado). | `CONFLICT` |
| 410 | ❌ | Recurso eliminado permanentemente. | `GONE` |
| 411 | ❌ | Falta cabecera `Content-Length`. | `LENGTH_REQUIRED` |
| 412 | ✅ | Falla de condición previa. | `PRECONDITION_FAILED` |
| 413 | ❌ | Cuerpo de petición demasiado grande. | `PAYLOAD_TOO_LARGE` |
| 414 | ❌ | URI demasiado largo. | `URI_TOO_LONG` |
| 415 | ❌ | Tipo de contenido no admitido. | `UNSUPPORTED_MEDIA_TYPE` |
| 416 | ❌ | Rango de bytes no válido. | `REQUESTED_RANGE_NOT_SATISFIABLE` |
| 417 | ✅ | Cabecera `Expect` no cumplida. | `EXPECTATION_FAILED` |
| 418 | ✅ | Código humorístico (RFC 2324). | `I_AM_A_TEAPOT` |
| 422 | ✅ | Datos válidos sintácticamente pero inválidos lógicamente. | `UNPROCESSABLE_ENTITY` |
| 423 | ❌ | Recurso bloqueado. | `LOCKED` |
| 424 | ✅ | Error por dependencia (WebDAV). | `FAILED_DEPENDENCY` |
| 426 | ❌ | Cliente debe actualizar protocolo. | `UPGRADE_REQUIRED` |
| 428 | ❌ | Se requiere condición previa. | `PRECONDITION_REQUIRED` |
| 429 | ✅ | Límite de peticiones excedido. | `TOO_MANY_REQUESTS` |
| 431 | ❌ | Cabeceras demasiado grandes. | `REQUEST_HEADER_FIELDS_TOO_LARGE` |
| 451 | ❌ | Contenido restringido legalmente. | `UNAVAILABLE_FOR_LEGAL_REASONS` |

## Codigo `5**` — Errores del servidor

| Código | Body | Uso | `HttpStatus` |
| --- | --- | --- | --- |
| 500 | ✅ | Error interno no controlado. | `INTERNAL_SERVER_ERROR` |
| 501 | ✅ | Funcionalidad no implementada. | `NOT_IMPLEMENTED` |
| 502 | ❌ | Error de pasarela / proxy. | `BAD_GATEWAY` |
| 503 | ✅ | Servidor sobrecargado o en mantenimiento. | `SERVICE_UNAVAILABLE` |
| 504 | ❌ | Timeout en servidor intermedio. | `GATEWAY_TIMEOUT` |
| 505 | ❌ | Versión HTTP no soportada. | `HTTP_VERSION_NOT_SUPPORTED` |
| 506 | ❌ | Negociación de contenido incorrecta. | `VARIANT_ALSO_NEGOTIATES` |
| 507 | ❌ | Sin espacio en servidor. | `INSUFFICIENT_STORAGE` |
| 508 | ❌ | Bucle detectado (WebDAV). | `LOOP_DETECTED` |
| 510 | ❌ | Requiere extensiones adicionales. | `NOT_EXTENDED` |
| 511 | ✅ | Se necesita autenticación de red. | `NETWORK_AUTHENTICATION_REQUIRED` |

