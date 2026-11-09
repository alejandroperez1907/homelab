# Capítulo 4 · Configuración posterior

*La primera vez que entro a la web de Proxmox, el cambio a los repositorios gratis y la actualización de todo el sistema*

[← Instalación de Proxmox VE](03-instalacion-proxmox.md) · [Índice](../README.md#documentación) · [Verificación y estado final →](05-verificacion.md)

## 4.1 Primer acceso a la interfaz web

Proxmox se maneja desde el navegador de cualquier equipo de la red entrando en esta dirección

```text
https://192.168.1.60:8006
```

La primera vez el navegador avisa de que el certificado no es de confianza, pero es normal porque Proxmox usa un certificado hecho por él mismo, así que le doy a **Avanzado → Continuar** y entro con estos datos

| Elemento | Detalle |
| --- | --- |
| Usuario | `root` |
| Contraseña | La que puse en el instalador |
| Reino (Realm) | Linux PAM standard authentication |
| Idioma | Español |

> [!NOTE]
> **El aviso de «No hay suscripción válida»**
>
> Cuando inicias sesión sale este aviso y se cierra con **Aceptar**, y no quita ninguna función de Proxmox, solo te dice que no estás pagando el soporte oficial

## 4.2 Repositorios de paquetes

Proxmox viene con los repositorios **Enterprise** puestos, que solo funcionan si pagas una suscripción, y sin ella las actualizaciones fallan, así que para usarlo en casa hay que poner el repositorio gratis, que se llama **No-Subscription**

Esto está en **pve → Actualizaciones → Repositorios**

1. Selecciono el repositorio que apunta a `enterprise.proxmox.com/debian/pve` y le doy a **Deshabilitar**
2. Hago lo mismo con el repositorio **Enterprise de Ceph**
3. Le doy a **Añadir**, elijo **No-Subscription** y confirmo

| Repositorio | Cómo queda |
| --- | --- |
| Proxmox VE Enterprise | Deshabilitado |
| Ceph Enterprise | Deshabilitado |
| Proxmox VE No-Subscription | Habilitado |
| Repositorios de Debian 13 (sin tocar) | Habilitado |

> [!NOTE]
> **El aviso del No-Subscription**
>
> La web te avisa de que este repositorio no se recomienda para empresas que lo usan en serio, pero para un homelab es lo normal

## 4.3 Actualización del sistema

Esto lo hago desde **pve → Shell**

```bash
apt update
apt full-upgrade -y
```

| Elemento | Detalle |
| --- | --- |
| `apt update` | Descarga la lista nueva de paquetes que hay en los repositorios |
| `apt full-upgrade -y` | Instala todas las actualizaciones, también los kernels nuevos y los cambios de dependencias, y el `-y` es para que diga que sí a todo solo |

Y después de actualizar **tuve que reiniciar** el servidor

```bash
reboot
```

---

[← Instalación de Proxmox VE](03-instalacion-proxmox.md) · [Índice](../README.md#documentación) · [Verificación y estado final →](05-verificacion.md)
