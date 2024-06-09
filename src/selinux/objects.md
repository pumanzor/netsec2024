# Objetos

- [Clases de Objetos y Permisos](#object-classes-and-permissions)
- [Permitir a un Proceso Acceder a Recursos](#allowing-a-process-access-to-resources)
- [Etiquetado de Objetos](#labeling-objects)
  - [Etiquetado de Sistemas de Archivos con Atributos Extendidos](#labeling-extended-attribute-filesystems)
    - [Copiar y Mover Archivos](#copying-and-moving-files)
- [Etiquetado de Sujetos](#labeling-subjects)
- [Reutilización de Objetos](#object-reuse)

Dentro de SELinux, un objeto es un recurso como archivos, sockets, tuberías o interfaces de red que son accedidos mediante procesos (también conocidos como sujetos). Estos objetos se clasifican según el 
recurso que proporcionan con permisos de acceso relevantes para su propósito (por ejemplo, leer, recibir y escribir), y se les asigna un [**Contexto de Seguridad**](security_context.md#security-context) como
se describe en las siguientes secciones.

## Clases de Objetos y Permisos

Cada objeto consta de un identificador de clase que define su propósito (por ejemplo, archivo, socket) junto con un conjunto de permisos (también conocidos como Vectores de Acceso (AV)) que describen qué 
servicios puede manejar el objeto (leer, escribir, enviar, etc.). Cuando un objeto se instancia, se le asigna un nombre (por ejemplo, un archivo podría llamarse config o un socket my_connection) y un 
contexto de seguridad (por ejemplo, *system_u:object_r:selinux_config_t*) como se muestra en la **Figura 5: Clase de Objeto = 'archivo' y permisos**.

![](https://github.com/pumanzor/ssec2024/blob/main/src/selinux/img/object-class.png)

**Figura 5: Clase de Objeto = 'archivo' y permisos** - *las reglas de la política definirían aquellos permisos permitidos para cada proceso que necesita acceso al archivo /etc/selinux/config.*

El objetivo de la política es permitir al usuario del objeto (el sujeto) el acceso a los permisos mínimos necesarios para completar la tarea (es decir, no permitir permiso de escritura si solo se necesita 
leer información).

Estas clases de objetos y sus permisos asociados están integrados en el núcleo de GNU / Linux y en los gestores de objetos del espacio de usuario por los desarrolladores y, por lo tanto, generalmente no son 
actualizados por los escritores de políticas.

Las clases de objetos consisten en clases de objetos del núcleo (para manejar archivos, sockets, etc.) además de clases de objetos del espacio de usuario para gestores de objetos del espacio de usuario 
(para servicios como X-Windows o dbus). El número de clases de objetos y sus permisos puede variar según las características configuradas en la versión de GNU / Linux. Todas las clases de objetos y 
permisos conocidos se describen en [**Apéndice A - Clases de Objetos y Permisos**](object_classes_permissions.md#appendix-a---object-classes-and-permissions).

## Permitir a un Proceso Acceder a Recursos

Este es un ejemplo simple que intenta explicar dos puntos:

1. Cómo se le otorgan permisos a un proceso para usar los recursos de un objeto.
2. Usando la clase de objeto *process*, mostrar que un proceso puede describirse como un proceso o un objeto.

Una política SELinux contiene muchas reglas y declaraciones, la mayoría de las cuales son reglas *allow* que (simplemente) permiten que los procesos obtengan permisos de acceso a los recursos de los objetos.

La siguiente regla *allow* y la **Figura 6: La regla *allow*** ilustran que 'un proceso también puede ser un objeto', ya que permite que los procesos que se ejecutan en el dominio *unconfined_t* tengan permiso para *transition* la aplicación de puerta de enlace externa al dominio *ext_gateway_t* una vez que se haya ejecutado:

```
allow Rule | source_domain |  target_type  :  class  | permission
-----------▼---------------▼-------------------------▼------------
allow        unconfined_t    ext_gateway_t :  process  transition;
```

Dónde:

*allow*

- La regla *allow* en el lenguaje SELinux.

*unconfined_t*

- El identificador del dominio fuente (o sujeto): en este caso, el shell que desea *ejecutar* la aplicación de puerta de enlace.

*ext_gateway_t*

- El identificador del objeto de destino: la instancia del objeto del proceso de la aplicación de puerta de enlace.

*process*

- La clase de objeto de destino: la clase de objeto *process*.

*transition*

- El permiso otorgado al dominio fuente sobre el objeto de destino: en este caso, el dominio *unconfined_t* tiene permiso de transición sobre el objeto *ext_gateway_t process*.


