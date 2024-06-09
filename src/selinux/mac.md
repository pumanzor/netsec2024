**Control de Acceso Obligatorio**

El Control de Acceso Obligatorio (MAC) es un tipo de control de acceso en el cual se utiliza el sistema operativo para restringir a un usuario o proceso (el sujeto) de acceder o realizar una operación 
sobre un objeto (como un archivo, disco, memoria, etc.).

Cada uno de los sujetos y objetos tiene un conjunto de atributos de seguridad que pueden ser interrogados por el sistema operativo para verificar si la operación solicitada puede ser realizada o no. 
Para SELinux, los:

- [**sujetos**](subjects.md#subjects) son procesos.
- [**objetos**](objects.md#objects) son recursos del sistema como archivos, sockets, etc.
- Los atributos de seguridad son el [**contexto de seguridad**](security_context.md#security-context).
- El Servidor de Seguridad dentro del kernel de Linux autoriza el acceso (o no) utilizando la política de seguridad (o política) que describe las reglas que deben aplicarse.

Es importante destacar que el sujeto (y por lo tanto el usuario) no puede decidir ignorar las reglas de la política que está siendo aplicada por la política MAC con SELinux habilitado. Esto contrasta con 
el Control de Acceso Discrecional (DAC) estándar de Linux, que también regula la capacidad de los sujetos para acceder a los objetos, sin embargo, permite a los usuarios tomar decisiones de política. 
Los pasos en la cadena de toma de decisiones para DAC y MAC se muestran en la **Figura 3**.


![](https://github.com/pumanzor/ssec2024/blob/main/src/selinux/img/pcall.png)

**Figura 3: Procesamiento de una Llamada al Sistema** - *Primero se realizan las comprobaciones de DAC, si pasan, entonces se consulta al Servidor de Seguridad para una decisión.*

SELinux admite dos formas de MAC:

**Aplicación de Tipo** - Donde los procesos se ejecutan en dominios y las acciones sobre los objetos están controladas por la política. Esta es la implementación utilizada para el MAC de propósito general dentro de SELinux junto con el Control de Acceso Basado en Roles. Las secciones de [**Aplicación de Tipo (TE)**](type_enforcement.md#type-enforcement) y [**Control de Acceso Basado en Roles**](rbac.md#role-based-access-control) cubren estos temas con más detalle.

**Seguridad Multinivel** - Esta es una implementación basada en el modelo Bell-La Padula (BLP), y es utilizada por organizaciones donde se requieren diferentes niveles de acceso para que la información restringida se separe de la información clasificada para mantener la confidencialidad. Esto permite que las reglas de aplicación, como 'no escribir hacia abajo' y 'no leer hacia arriba', se implementen en una política extendiendo el contexto de seguridad para incluir niveles de seguridad. La sección de [**MLS**](mls_mcs.md#multi-level-and-multi-category-security) cubre esto con más detalle junto con una variante llamada Seguridad de Multicategoría (MCS).

Los servicios de MLS/MCS ahora se utilizan más generalmente para mantener la separación de aplicaciones, por ejemplo, SELinux habilitado:

- Máquinas virtuales usan categorías MCS para permitir que cada VM se ejecute dentro de su propio dominio para aislar las VMs entre sí (ver la sección de [**Soporte de Máquinas Virtuales en SELinux**](vm_support.md#selinux-virtual-machine-support)).
- Dispositivos Android usan categorías MCS generadas dinámicamente para que una aplicación que se ejecuta en nombre de un usuario no pueda leer o escribir archivos creados por la misma aplicación que se ejecuta en nombre de otro usuario (ver la sección de [**Mejoras de Seguridad para Android - Computación de un Contexto**](seandroid.md#computing-process-context-examples)).
