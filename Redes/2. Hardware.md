# Introducción

El **hardware de red** comprende los dispositivos físicos y medios de conexión que permiten enlazar computadoras, teléfonos, servidores, impresoras y otros equipos. Estos componentes transportan datos dentro de una red local y, cuando corresponde, entre la red local e Internet.

Una red puede ser pequeña —por ejemplo, la de una casa— o abarcar varias oficinas y edificios. Aunque cambie su tamaño, suele incluir dispositivos que conectan equipos, dirigen el tráfico y proporcionan acceso inalámbrico.

# Objetivos

- Conectar dispositivos entre sí.
- Enviar datos al dispositivo o red de destino.
- Compartir recursos, como una conexión a Internet o una impresora.
- Ampliar la cobertura de una red cableada o inalámbrica.
- Organizar y proteger las comunicaciones.

# Componentes principales

| Componente | Función | Ejemplo de uso |
|---|---|---|
| Tarjeta de red (NIC) | Permite que un dispositivo se conecte a una red por cable o Wi‑Fi. Puede estar integrada en el equipo o instalarse como adaptador. | Conectar una computadora a Ethernet |
| Módem | Establece la conexión entre la red del usuario y ciertos servicios de Internet del proveedor, como cable o DSL. | Conectar el servicio de Internet por cable |
| Terminal de red óptica (ONT) | Termina la conexión de fibra óptica del proveedor y entrega una conexión que puede utilizar el router. | Acceso a Internet por fibra |
| Router | Conecta redes distintas y dirige paquetes de datos según su dirección IP. En redes domésticas, suele compartir Internet y puede incluir otras funciones. | Conectar una red local a Internet |
| Switch | Conecta varios dispositivos cableados dentro de una red local y reenvía los datos por el puerto correspondiente. | Conectar computadoras, impresoras y servidores |
| Punto de acceso (AP) | Permite que dispositivos inalámbricos se conecten a la red, normalmente a través de una conexión cableada. | Proporcionar Wi‑Fi en una oficina |
| Firewall | Filtra el tráfico de red de acuerdo con reglas de seguridad. Puede ser un dispositivo dedicado o estar integrado en otro equipo. | Controlar conexiones que entran o salen de una red |
| Repetidor o extensor | Recibe y vuelve a transmitir una señal inalámbrica para ampliar su alcance. | Llevar Wi‑Fi a una zona con señal débil |
| Panel de conexión (patch panel) | Organiza y facilita la conexión de cables en instalaciones con muchos puntos de red. | Centralizar el cableado de una oficina |
| Cableado de red | Transporta datos entre dispositivos mediante cobre o fibra óptica. | Conectar un switch a una computadora |

La tarjeta de red también se conoce como **adaptador de red**. Los routers, switches y puntos de acceso cumplen tareas distintas, aunque algunos equipos domésticos combinan varias de ellas en un solo aparato. 

# Diferencias entre router, switch y punto de acceso

- **Router:** conecta redes diferentes, como una red local y la de un proveedor de Internet.
- **Switch:** conecta dispositivos cableados dentro de una misma red local.
- **Punto de acceso:** conecta dispositivos inalámbricos a la red local.
- **Módem u ONT:** proporciona la interfaz necesaria para conectar el servicio del proveedor al equipo de red.

Una forma sencilla de recordarlo es: el módem o la ONT entrega la conexión del proveedor; el router conecta redes; el switch añade conexiones cableadas; el punto de acceso proporciona Wi‑Fi.

## Medios de transmisión

Los datos pueden viajar por distintos medios:

- **Cable de par trenzado:** común en redes Ethernet; conecta dispositivos a switches o routers.
- **Fibra óptica:** transmite datos mediante señales de luz y se utiliza en conexiones de alta capacidad o largas distancias.
- **Wi‑Fi:** transmite datos por ondas de radio y permite conectar dispositivos sin cables.
- **Coaxial o línea telefónica:** puede utilizarse en determinados servicios de Internet del proveedor.

La elección del medio depende de la distancia, la velocidad requerida, el entorno y los equipos disponibles.

# Ejemplo del recorrido de los datos

Cuando una computadora conectada por cable solicita una página web:

1. La tarjeta de red envía los datos desde la computadora.
2. El switch, si existe, los dirige hacia el router.
3. El router los envía a la red del proveedor de Internet.
4. La respuesta vuelve por la red y llega al dispositivo solicitado.
5. El navegador muestra la página recibida.

Si la computadora está conectada por Wi‑Fi, el punto de acceso recibe y transmite la comunicación inalámbrica hacia la red.

# Criterios para elegir equipos

Antes de instalar o comprar hardware de red, conviene considerar:

- **Cantidad de dispositivos:** cuántos equipos se conectarán ahora y en el futuro.
- **Tipo de conexión:** Ethernet, Wi‑Fi, fibra u otro medio.
- **Cobertura:** tamaño del espacio, cantidad de pisos y obstáculos físicos.
- **Velocidad y capacidad:** compatibilidad con el servicio de Internet y el uso previsto.
- **Administración:** si se necesitan funciones configurables para controlar la red.
- **Alimentación:** algunos switches pueden alimentar dispositivos compatibles mediante **PoE**, que transmite energía y datos por el cable Ethernet.
- **Seguridad:** disponibilidad de funciones de filtrado, redes para invitados y actualizaciones del fabricante.

# Mantenimiento básico

Para mantener una red en buen estado:

- Coloca el router y los puntos de acceso en lugares ventilados y adecuados para la cobertura.
- Revisa que los cables y conectores estén firmes y sin daños.
- Etiqueta los cables en instalaciones grandes para identificarlos con facilidad.
- Mantén actualizados los equipos administrables y cambia las credenciales predeterminadas.
- Si la conexión falla, comprueba primero la alimentación, los cables y las luces indicadoras del módem, la ONT o el router.