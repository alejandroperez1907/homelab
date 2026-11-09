# Capítulo 5 · Verificación y estado final

*Las comprobaciones que hice después de instalarlo y la ficha del servidor tal y como queda*

[← Configuración posterior](04-configuracion-proxmox.md) · [Índice](../README.md#documentación) · [Pi-hole →](06-pihole.md)

## 5.1 Versión instalada

Primero miro qué versión ha quedado instalada desde la Shell de Proxmox

```bash
pveversion
```

```text
pve-manager/9.2.20/49318c671b82f31e (running kernel: 7.0.14-19-pve)
```

| Elemento | Detalle |
| --- | --- |
| pve-manager | `9.2.20` |
| Kernel en uso | `7.0.14-19-pve` |

## 5.2 Gráfica integrada

Luego compruebo que el sistema ve la gráfica Intel, ya que más adelante la usa Jellyfin para convertir el vídeo

```bash
ls -l /dev/dri
```

```text
total 0
drwxr-xr-x 2 root root         80 Sep 23 12:08 by-path
crw-rw---- 1 root video  226,   1 Sep 23 12:08 card1
crw-rw---- 1 root render 226, 128 Sep 23 12:08 renderD128
```

| Elemento | Detalle |
| --- | --- |
| `renderD128` | Es lo que se usa para acelerar el vídeo y lo que luego le paso al contenedor de Jellyfin, y es del grupo `render` |
| `card1` | Es la gráfica en sí, y que se llame `card1` en vez de `card0` es normal y no pasa nada |

## 5.3 Resumen de comprobaciones

| Qué he comprobado | Resultado |
| --- | --- |
| Entro a la web en `https://192.168.1.60:8006` | Correcto |
| Hay internet y DNS (la actualización bajó e instaló los paquetes) | Correcto |
| Proxmox VE 9.2 instalado y actualizado (`pve-manager 9.2.20`) | Correcto |
| El disco repartido con los valores por defecto en el SSD de 480 GB | Correcto |
| La gráfica Intel se ve bien (`/dev/dri/renderD128`) | Correcto |

## 5.4 Ficha técnica del nodo

**pve** · pve.home.arpa · 192.168.1.60

| Elemento | Detalle |
| --- | --- |
| Equipo | ASUS Chromebox 3 · Celeron 3865U · 16 GB RAM · SSD 480 GB |
| Sistema | Proxmox VE 9.2 (`pve-manager 9.2.20`) sobre Debian 13 |
| Kernel | `7.0.14-19-pve` |
| Dirección IP | `192.168.1.60/24` |
| Puerta de enlace | `192.168.1.1` |
| DNS | `1.1.1.1` |
| Red | Tarjeta `nic0` · puente `vmbr0` |
| Sistema de archivos | ext4 sobre LVM |
| Almacenamiento | `local` · 96 GiB · `local-lvm` · 319,6 GiB (thin) |
| Repositorio | No-Subscription |
| Acceso web | `https://192.168.1.60:8006` |

> **Siguiente paso** · Capítulo 6 · Pi-hole · LXC 101 · 192.168.1.61  
> El primer servicio del homelab, que bloquea los anuncios en toda la red de casa

---

[← Configuración posterior](04-configuracion-proxmox.md) · [Índice](../README.md#documentación) · [Pi-hole →](06-pihole.md)
