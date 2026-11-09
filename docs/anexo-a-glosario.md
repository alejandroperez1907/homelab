# Anexo A · Glosario

*Las palabras técnicas que salen en el documento, explicadas de forma sencilla*

[← Jellyfin](10-jellyfin.md) · [Índice](../README.md#documentación)

| Palabra | Qué significa |
| --- | --- |
| Proxmox VE | Un sistema basado en Debian para crear y manejar máquinas virtuales y contenedores desde una página web |
| Máquina virtual (VM) | Un ordenador entero simulado, con su propio sistema operativo y su propio kernel |
| Contenedor LXC | Un Linux aislado que usa el mismo kernel que el servidor, gasta mucho menos que una VM pero tiene su propia IP y sus propios programas |
| Plantilla (CT) | La imagen base de un sistema operativo que se usa para crear un contenedor |
| Contenedor sin privilegios | Un contenedor donde el `root` de dentro no manda sobre el servidor, y por eso es más seguro |
| Anidamiento | Una opción del contenedor (en inglés *nesting*) que deja que dentro funcionen algunas cosas modernas de Linux y, si hace falta, otros contenedores |
| pct | La herramienta de Proxmox para manejar los contenedores desde la terminal |
| Kernel | El núcleo del sistema operativo, la parte que controla el hardware |
| ISO | Una imagen de un disco de instalación metida en un solo archivo |
| UEFI | El firmware moderno que arranca el equipo, el que ha sustituido a la BIOS de toda la vida |
| Hash SHA-256 | Es como la huella de un archivo, y si cambia aunque sea un poco del archivo la huella sale totalmente distinta |
| ext4 | El sistema de archivos normal de Linux |
| ZFS | Un sistema de archivos más avanzado, pensado sobre todo para cuando tienes varios discos, y gasta más RAM |
| LVM | Un sistema que divide un disco en partes (volúmenes) a las que se les puede cambiar el tamaño |
| LVM-thin | Un tipo de LVM donde cada volumen solo ocupa lo que usa de verdad |
| Swap | Una parte del disco que se usa como memoria de reserva cuando la RAM se llena |
| FQDN | El nombre completo de un equipo con el dominio incluido, por ejemplo `pve.home.arpa` |
| CIDR (/24) | Una forma corta de poner la máscara de red, por ejemplo `/24` es lo mismo que `255.255.255.0` |
| Puerta de enlace | El equipo por donde sale el tráfico hacia internet, que en casa es el router |
| DNS | El servicio que traduce los nombres (`google.com`) a direcciones IP |
| DNS upstream | El DNS al que Pi-hole le pasa las consultas que no bloquea, que al principio era Cloudflare y ahora es Unbound, en el mismo contenedor |
| Lista de bloqueo | Una lista de dominios de anuncios y rastreadores que Pi-hole bloquea |
| HaGeZi | Un proyecto que hace listas de bloqueo DNS en varios niveles (de Light a Ultimate) y otras listas más concretas como TIF o DoH |
| Gravity | Lo que usa Pi-hole para bajar todas las listas de bloqueo y juntarlas en su base de datos |
| Unbound | Un DNS que busca las direcciones él solo, sin depender de un DNS de fuera como Cloudflare |
| Resolvedor recursivo | Un DNS que encuentra un nombre haciendo todo el camino, primero los servidores raíz, luego el dominio de primer nivel y al final el servidor del dominio |
| Servidores raíz | Los servidores que están arriba del todo en el sistema DNS, y saben a quién hay que preguntar por cada dominio de primer nivel (`.com`, `.net`, `.es`…) |
| DNSSEC | Unas firmas en las respuestas DNS que sirven para comprobar que nadie las ha cambiado por el camino |
| DNS cifrado (DoH) | DNS que va cifrado por HTTPS, y algunos navegadores y apps lo usan por su cuenta y así se saltan Pi-hole |
| DHCP | El servicio del router que reparte las IPs solo, y una *reserva* hace que un equipo reciba siempre la misma IP |
| Dirección MAC | El identificador único de una tarjeta de red, que el router usa para saber a qué equipo le da cada IP reservada |
| Puente de red (vmbr0) | Un switch virtual que conecta los contenedores y las VMs con la red de casa |
| Repositorio | El servidor de donde el sistema baja los programas y las actualizaciones |
| Docker | Un programa que ejecuta aplicaciones empaquetadas en *contenedores Docker*, con todo lo que necesitan para funcionar |
| Imagen Docker | Un paquete ya listo con una aplicación y todo lo que necesita, por ejemplo `vaultwarden/server` |
| Docker Compose | Una herramienta para poner uno o varios contenedores Docker en un archivo (`compose.yaml`) y arrancarlos con un solo comando |
| Tailscale | Una VPN que funciona con WireGuard y conecta tus dispositivos entre ellos sin abrir puertos en el router |
| Tailnet | La red privada que forman todos los dispositivos que están en la misma cuenta de Tailscale |
| MagicDNS | Una función de Tailscale que le pone nombre a cada máquina de la tailnet (por ejemplo `vaultwarden.tailxxxxxx.ts.net`) |
| Clave de host (SSH) | La clave que identifica a un servidor SSH, y su *huella* (fingerprint) sirve para comprobar que te estás conectando al servidor que toca |
| Contraseña maestra | La contraseña con la que se cifra la caja fuerte de Vaultwarden, y si se olvida no se puede recuperar |
| Subnet router | Una máquina de la tailnet que deja entrar a una red entera (por ejemplo la de casa) a los demás dispositivos de Tailscale |
| Reenvío IP | Cuando un Linux puede pasar paquetes de una red a otra como si fuera un router (en inglés *IP forwarding*) |
| Ruta más concreta | Cuando hay varios caminos para llegar al mismo sitio gana el que tiene el número más alto después de la barra, por ejemplo una `/24` gana a una `/23` |
| Node.js | Lo que se usa para ejecutar programas hechos en JavaScript fuera del navegador, y es con lo que funciona Uptime Kuma |
| npm | El gestor de paquetes de Node.js, que baja e instala las librerías que necesita un programa |
| systemd (servicio) | Lo que arranca y vigila los programas en Linux, y un *servicio* es un programa que systemd arranca solo y lo vuelve a encender si falla |
| Monitor | En Uptime Kuma, cada comprobación que se repite cada cierto tiempo de un servicio (ping, web, DNS…) |
| SMTP | El protocolo para mandar correos, y Uptime Kuma lo usa para mandar los avisos con Gmail |
| Contraseña de aplicación | Una contraseña que crea Google para que un programa use la cuenta sin saber la contraseña de verdad, y se puede borrar cuando quieras |
| arping | Una herramienta que pregunta en la red quién tiene una IP, y sirve para ver si una IP está libre |
| Transcodificación | Convertir un vídeo a otro formato o calidad mientras se está viendo, para que lo pueda reproducir un dispositivo que no soporta el original |
| Reproducción directa | Cuando el dispositivo reproduce el archivo tal cual sin convertir nada, que es lo que menos carga al servidor |
| HDR / tone mapping | El HDR es un formato de vídeo con más brillo y más color, y el *tone mapping* lo pasa a imagen normal (SDR) para las pantallas que no lo soportan |
| VA-API | Lo que usa Linux para que la gráfica convierta vídeo, y QuickSync funciona encima de esto |
| Punto de montaje | Un espacio de almacenamiento extra que se le añade a un contenedor en una carpeta concreta, como `/srv/media` |
| SFTP | Pasar archivos por SSH de forma cifrada, que es lo que usa WinSCP para subir las películas |
| Quick Sync | Una función de las gráficas Intel para convertir vídeo con la gráfica y no cargar el procesador |

---

[← Jellyfin](10-jellyfin.md) · [Índice](../README.md#documentación)
