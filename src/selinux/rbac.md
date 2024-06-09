# Control de Acceso Basado en Roles

Para controlar aún más el acceso a los dominios TE, SELinux utiliza el control de acceso basado en roles (RBAC). Esta característica permite que los usuarios de SELinux se asocien con uno o más roles, 
donde cada rol se asocia luego con uno o más tipos de dominio, como se muestra en la **Figura 4: Control de Acceso Basado en Roles**.

El nombre del rol en SELinux es el segundo componente de un 'contexto de seguridad' y, por convención, los roles de SELinux terminan en *\_r*. Sin embargo, esto no es impuesto por ningún servicio de 
SELinux (es decir, solo se utiliza para identificar el componente del rol), aunque CIL con espacios de nombres hace que la identificación de un rol sea más fácil; por ejemplo, un 'rol' podría declararse como *unconfined.role*.

Es posible agregar restricciones y límites a los roles, como se discute en la sección de [**Aplicación de Tipo**](type_enforcement.md#type-enforcement).

Algunas políticas, por ejemplo Android, solo hacen uso de un rol llamado *r*.


![](https://github.com/pumanzor/ssec2024/blob/main/src/selinux/img/rbac.png)

**Figura 4: Control de Acceso Basado en Roles** - *Muestra cómo SELinux controla el acceso mediante la asociación de usuario, rol y tipo de dominio.*

---
**[[ PREV ]](users.md)** **[[ TOP ]](#)** **[[ NEXT ]](typeen.md)**
