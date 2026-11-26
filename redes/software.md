# Introducción

El **software de infraestructura de red** administra, protege y distribuye las comunicaciones entre usuarios, aplicaciones y servidores. A diferencia del hardware de red, que corresponde a dispositivos físicos, estos componentes son programas o servicios que pueden ejecutarse en servidores, máquinas virtuales, contenedores o plataformas en la nube.

Algunas funciones se ofrecen en un dispositivo físico o como servicio administrado, pero siguen siendo conceptos de software: firewall, proxy inverso, balanceador de carga, DNS y VPN, entre otros.

# Componentes principales

| Componente | Función | Ejemplo de uso |
|---|---|---|
| Firewall | Permite o bloquea conexiones según reglas, como direcciones, puertos o protocolos. | Restringir el acceso a servicios de una red |
| Proxy inverso | Recibe solicitudes de los clientes y las reenvía a uno o más servidores. Puede centralizar funciones como terminación TLS y caché. | Publicar una aplicación sin exponer directamente sus servidores |
| Balanceador de carga | Distribuye solicitudes entre varios servidores para repartir el trabajo y mejorar la disponibilidad. | Repartir visitas entre varias instancias de una aplicación |
| DNS | Traduce nombres de dominio a direcciones IP y puede orientar a los usuarios hacia distintos servicios. | Resolver el nombre de un sitio web |
| VPN | Crea un canal de comunicación protegido entre dispositivos o redes a través de otra red. | Permitir el acceso remoto de personal autorizado |
| Servidor DHCP | Asigna automáticamente parámetros de red, como una dirección IP, a los dispositivos. | Configurar computadoras de una oficina al conectarse |
| IDS/IPS | Analiza el tráfico para identificar actividad sospechosa; un IPS también puede tomar medidas para bloquearla. | Detectar o detener tráfico que coincida con reglas de seguridad |
| WAF | Filtra y supervisa solicitudes dirigidas a aplicaciones web. | Añadir una capa de protección frente a solicitudes web no deseadas |
| Caché | Guarda temporalmente contenido para entregarlo más rápido o reducir solicitudes al servidor de origen. | Servir archivos estáticos desde una ubicación cercana |
| Monitorización y registro | Recopila métricas, eventos y registros para observar el estado de la red y diagnosticar problemas. | Revisar errores, disponibilidad y uso de recursos |

# Firewall

Un firewall aplica reglas al tráfico que entra o sale de un sistema o una red. Según su configuración, puede permitir o bloquear comunicaciones por dirección IP, puerto, protocolo, aplicación u otros atributos.

Puede funcionar en distintos niveles:

- **Firewall de red:** controla comunicaciones entre redes.
- **Firewall de host:** se ejecuta en un servidor o computadora y protege ese equipo.
- **Firewall de aplicaciones web (WAF):** se enfoca en solicitudes dirigidas a aplicaciones web.

Las reglas deben corresponder a los servicios que realmente se necesitan. Una política demasiado permisiva reduce la protección; una demasiado restrictiva puede impedir el funcionamiento de aplicaciones legítimas.

# Proxy inverso

Un proxy inverso se ubica delante de uno o varios servidores. El cliente se comunica con el proxy y este reenvía la solicitud al servidor apropiado. Desde el punto de vista del usuario, normalmente parece estar accediendo directamente al servicio.

Entre sus usos habituales están:

- Recibir conexiones de los clientes y encaminarlas a servicios internos.
- Terminar conexiones TLS y gestionar certificados.
- Aplicar controles de acceso y límites de solicitudes.
- Almacenar en caché contenido que se repite.
- Ocultar la estructura interna de los servidores.

Un proxy inverso puede incluir funciones de balanceo de carga, pero no todo proxy inverso se usa necesariamente para repartir tráfico.

# Balanceador de carga

Un balanceador de carga distribuye solicitudes entre varios servidores o instancias de una aplicación. Puede utilizar distintos criterios, como turnos, conexiones activas o capacidad disponible, según el producto y su configuración.

Sus objetivos principales son:

- Repartir el trabajo para evitar que un servidor concentre todas las solicitudes.
- Mantener el servicio disponible si una instancia deja de responder.
- Facilitar el crecimiento de una aplicación mediante la incorporación de más instancias.
- Comprobar periódicamente si los servidores están disponibles.

El balanceador no garantiza por sí solo que una aplicación sea tolerante a fallos: también deben considerarse la base de datos, el almacenamiento, la configuración de las instancias y otros componentes dependientes.

# Diferencia entre proxy inverso y balanceador

Un **proxy inverso** actúa como intermediario entre clientes y servidores. Un **balanceador de carga** distribuye las solicitudes entre varios destinos. Un mismo programa puede desempeñar ambas funciones, pero son responsabilidades distintas: el proxy administra el punto de entrada y el balanceador decide cómo repartir el tráfico.

# Flujo de una solicitud web

1. El usuario introduce el nombre del sitio en su navegador.
2. DNS devuelve la información necesaria para localizar el servicio.
3. La solicitud llega al punto de entrada de la red.
4. El firewall aplica sus reglas.
5. El proxy inverso recibe la conexión y puede aplicar controles adicionales.
6. El balanceador selecciona una instancia disponible.
7. La aplicación procesa la solicitud y devuelve una respuesta.
8. La respuesta vuelve al usuario a través de la ruta correspondiente.

# Consideraciones de diseño y administración

Al diseñar estos servicios, conviene definir:

- **Disponibilidad:** qué ocurre si una instancia o servicio deja de responder.
- **Seguridad:** qué conexiones se permiten y dónde se gestionan certificados y credenciales.
- **Capacidad:** cuántos usuarios o solicitudes se espera atender.
- **Registro y monitorización:** qué métricas y eventos se conservarán para detectar fallos.
- **Actualizaciones:** cómo se aplicarán parches y cambios de configuración.
- **Redundancia:** si los componentes críticos cuentan con alternativas para reducir interrupciones.