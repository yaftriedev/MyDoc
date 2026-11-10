# Fisico

- **Estrella:** cada dispositivo se conecta a un equipo central, normalmente un switch. Si falla un cable, suele quedar aislado solo el dispositivo conectado a ese cable. Si falla el switch central, pueden perder conexión todos los dispositivos de esa estrella. Es muy habitual en redes Ethernet domésticas y de oficina.

- **Bus:** todos los dispositivos comparten un mismo cable principal. Era sencilla y barata para redes pequeñas, pero una interrupción en el cable podía afectar a toda la red. Además, cuando muchos equipos transmitían, podían producirse colisiones y bajar el rendimiento. Por eso hoy está prácticamente en desuso en redes locales.

- **Anillo:** cada dispositivo se conecta al siguiente y al último, formando un circuito cerrado. En algunos diseños, los datos circulan en una dirección y cada equipo los retransmite. Un fallo podía interrumpir el anillo, aunque existen variantes con un segundo anillo o mecanismos de protección. La idea de que “no hay colisiones” depende del método de acceso que use la red; no es una propiedad automática de cualquier anillo.

- **Malla:** los dispositivos o nodos tienen varias conexiones entre sí. En una **malla completa**, cada nodo se conecta directamente con todos los demás; en una **malla parcial**, solo algunos tienen varias rutas. Esa redundancia permite que los datos encuentren otro camino si falla un enlace, pero aumenta el costo y la complejidad. Se usa, por ejemplo, en ciertas redes inalámbricas y sistemas de transporte de datos. Internet no es una única malla uniforme: es una red de redes con múltiples rutas.

- **Árbol:** organiza la red por niveles, como las ramas de un árbol. Suele combinar varias estrellas conectadas a un nodo superior. Facilita ampliar y ordenar redes grandes, pero una falla en un equipo o enlace de nivel superior puede afectar a las ramas que dependen de él.

- **Híbrida:** combina dos o más topologías. Por ejemplo, una empresa puede conectar los equipos de cada oficina en estrella y enlazar las oficinas mediante una estructura de árbol o malla. Es común porque permite adaptar la red a distintas necesidades, aunque su diseño puede ser más complejo.

# Digital

- **PAN (Personal Area Network, red de área personal):** conecta dispositivos muy próximos a una persona, normalmente a unos pocos metros. Por ejemplo, un teléfono conectado a auriculares o a un reloj mediante Bluetooth. NFC también sirve para intercambios a muy corta distancia, como pagos sin contacto.

- **LAN (Local Area Network, red de área local):** conecta equipos dentro de un espacio reducido, como una casa, una oficina o un edificio. Puede usar Wi‑Fi o cables Ethernet. Permite compartir internet, impresoras y archivos.

- **CAN (Campus Area Network, red de área de campus):** une varias LAN de edificios cercanos que pertenecen a una misma organización, como una universidad, un hospital o una empresa. Por ejemplo, permite que las redes de distintos edificios compartan servicios y conexión.

- **MAN (Metropolitan Area Network, red de área metropolitana):** conecta redes a través de una ciudad o zona metropolitana. Puede enlazar edificios o sedes de una organización, o ser operada por un proveedor de telecomunicaciones. No necesariamente cubre toda la ciudad.

- **WAN (Wide Area Network, red de área amplia):** conecta redes que están muy separadas geográficamente, entre ciudades, países o continentes. Internet es el ejemplo más conocido, pero una empresa también puede tener una WAN privada que conecte sus sucursales.

- **SAN (Storage Area Network, red de área de almacenamiento):** se diferencia de las anteriores porque se define sobre todo por **lo que conecta y para qué sirve**, no por su tamaño geográfico. Enlaza servidores con dispositivos de almacenamiento de alto rendimiento, normalmente en centros de datos. Para los servidores, ese almacenamiento puede aparecer como si fuera un disco local.

# Subredes

> La **subnetting** consiste en dividir una red grande en varias redes más pequeñas, llamadas **subredes**. Esto permite organizar mejor los dispositivos y aprovechar las direcciones IP de forma más ordenada.

> **Regla rápida:** el prefijo indica cuántos bits pertenecen a la red; cuanto mayor es el prefijo, más pequeñas son las subredes. Por ejemplo, `/26` es más pequeño que `/24`. Para diseñar una red real, primero decide cuántas subredes necesitas y cuántos equipos debe admitir cada una; luego eliges el prefijo adecuado.

## Ejemplo: dividir `192.168.1.0/24`

El `/24` indica que los primeros 24 bits identifican la red; quedan 8 bits para los dispositivos. En total hay 256 direcciones, pero normalmente 254 pueden asignarse a equipos: se reservan la primera para identificar la subred y la última para difusión (*broadcast*).

Supongamos que quieres crear **4 subredes iguales**:

1. **Calcula cuántos bits necesitas tomar prestados:** para obtener al menos 4 subredes, necesitas 2 bits, porque \(2^2 = 4\).

2. **Ajusta el prefijo:** el prefijo pasa de `/24` a `/26`. La máscara correspondiente es `255.255.255.192`.

3. **Calcula el tamaño de cada bloque:** (256 - 192 = 64). Por tanto, las subredes avanzan de 64 en 64 en el último octeto.

| Subred | Dirección de red | Direcciones para equipos | Broadcast |
|---|---|---|---|
| 1 | `192.168.1.0/26` | `192.168.1.1–192.168.1.62` | `192.168.1.63` |
| 2 | `192.168.1.64/26` | `192.168.1.65–192.168.1.126` | `192.168.1.127` |
| 3 | `192.168.1.128/26` | `192.168.1.129–192.168.1.190` | `192.168.1.191` |
| 4 | `192.168.1.192/26` | `192.168.1.193–192.168.1.254` | `192.168.1.255` |

Cada subred tiene 64 direcciones en total, de las cuales 62 se pueden asignar a equipos en este ejemplo.

