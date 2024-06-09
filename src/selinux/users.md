**Usuarios de SELinux**

En Linux, los usuarios generalmente se asocian con usuarios humanos (como Alice y Bob) o funciones de operador/sistema (como admin). Si bien esto puede implementarse en SELinux, los nombres de usuario de 
SELinux generalmente son grupos o clases de usuarios. Por ejemplo, todos los usuarios estándar del sistema podrían asignarse un nombre de usuario de SELinux como user_u y el personal administrativo bajo 
staff_u.

Hay un usuario especial de SELinux que nunca debe asociarse a un usuario de Linux, ya que es una identidad especial para procesos y objetos del sistema; este usuario es system_u.

El nombre de usuario de SELinux es el primer componente de un Contexto de Seguridad y, por convención, los nombres de usuario de SELinux terminan en _u. Sin embargo, esto no es impuesto por ningún 
servicio de SELinux (es decir, es solo para identificar el componente de usuario), aunque CIL con espacios de nombres hace que la identificación de un usuario de SELinux sea más fácil; por ejemplo, 
un 'usuario' podría declararse como unconfined.user.

Es posible agregar restricciones y límites a los usuarios de SELinux, como se discute en la sección de Aplicación de Tipo (TE).

Algunas políticas, por ejemplo Android, solo hacen uso de un usuario llamado u.

---
**[[ PREV ]](mac.md)** **[[ TOP ]](#)** **[[ NEXT ]](rbac.md)**
