# Capítulo 2 · Preparación de la instalación

*La copia de lo que tenía en el servidor antes de borrarlo, la descarga de Proxmox VE, cómo comprobé el archivo y cómo hice el pendrive de arranque*

[← Visión general del homelab](01-vision-general.md) · [Índice](../README.md#documentación) · [Instalación de Proxmox VE →](03-instalacion-proxmox.md)

## 2.1 Copia de la instalación anterior

Antes de esto el servidor ya tenía un Proxmox con una máquina virtual Debian 13 donde funcionaban Pi-hole, Tailscale y Vaultwarden, y como al reinstalar se borra todo el disco, antes de empezar hice esto

| Qué | Qué hice | Estado |
| --- | --- | --- |
| **Contraseñas de Vaultwarden** | Las exporté desde **Herramientas → Exportar caja fuerte** en formato **.json (Cifrado)** y tipo **«Protegido por contraseña»**, y luego las volví a importar al instalar Vaultwarden (capítulo 7) | Hecho |
| **Configuración de Pi-hole** | No la exporté porque preferí empezar Pi-hole de cero | Descartado |
| **DNS del router** | Lo dejé como estaba antes, porque si el router seguía dando el Pi-hole antiguo como DNS, al borrar el servidor toda la casa se habría quedado sin poder abrir webs | Hecho |

> [!NOTE]
> **Por qué «Protegido por contraseña»**
>
> La otra opción es «Restringido a la cuenta», pero esa solo se puede importar en la misma cuenta de Vaultwarden y la cuenta desaparece al reinstalar, en cambio con «Protegido por contraseña» puedo importar el archivo en una cuenta nueva usando la contraseña que puse al exportar

## 2.2 Descarga de la ISO

La ISO la descargué de la web oficial de Proxmox (`proxmox.com/downloads`) y cogí la versión más nueva que había

| Elemento | Detalle |
| --- | --- |
| Producto | Proxmox VE 9.2 ISO Installer |
| Versión | `9.2-1` |
| Archivo | `proxmox-ve_9.2-1.iso` |
| Tamaño | 1,71 GB |
| Publicación | 21 de mayo de 2026 |
| Sistema base | Debian 13 «Trixie» |

## 2.3 Verificación de la descarga

Antes de grabar la ISO miro su **hash SHA-256**, que es como la huella del archivo, y si la descarga se ha cortado o el archivo ha cambiado aunque sea un poco, el hash sale totalmente distinto, así que lo saco en el PC con PowerShell desde la carpeta donde está el archivo

```powershell
Get-FileHash .\proxmox-ve_9.2-1.iso -Algorithm SHA256
```

Y el resultado tiene que ser exactamente igual que el hash que pone Proxmox en su web para la versión 9.2-1

```text
4e88fe416df9b527624a175f24c9aa07c714d3332afb1ee3dbf3879573ef2c6c
```

## 2.4 Grabación en el pendrive

La ISO se graba en un pendrive de **4 GB** o más, pero ojo porque al grabarla **se borra todo lo que tenga el pendrive**, y para hacerlo hay dos programas

| Programa | Cómo se usa |
| --- | --- |
| **balenaEtcher** (el que recomiendo) | Eliges la ISO, eliges el pendrive y le das a **Flash** |
| **Rufus** | Hay que elegir **«Modo imagen DD»**, porque con el otro modo puede que no arranque |

---

[← Visión general del homelab](01-vision-general.md) · [Índice](../README.md#documentación) · [Instalación de Proxmox VE →](03-instalacion-proxmox.md)
