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

![](https://github.com/pumanzor/ssec2024/blob/main/src/selinux/img/allow-rule.png)

**Figura 6: La regla *allow*** - *Muestra que el sujeto (los procesos que se ejecutan en el dominio unconfined_t) ha recibido el permiso de transición sobre el objeto proceso ext_gateway_t.*

Cabe destacar que hay más en una transición de dominio de lo que se describe arriba. Para una explicación más detallada, consulte la sección [**Transición de Dominio**](domain_object_transitions.md#domain-transition).

## Etiquetado de Objetos

En un sistema GNU / Linux con SELinux habilitado y en ejecución, el etiquetado de objetos es gestionado por el sistema y generalmente no es visible para los usuarios (¡hasta que el etiquetado falla!). A medida que se crean y destruyen procesos y objetos, estos:

1. Heredan sus etiquetas del proceso u objeto principal. Las declaraciones predeterminadas de usuario, tipo, rol y rango de la política pueden usarse para cambiar el comportamiento, como se discute en la sección [**Reglas Predeterminadas**](default_rules.md#default-object-rules).
2. Las declaraciones de transición de tipo, rol y rango de la política permiten asignar una etiqueta diferente, como se discute en la sección [**Transiciones de Dominio y Objetos**](domain_object_transitions.md#domain-and-object-transitions).
3. Las aplicaciones compatibles con SELinux pueden asignar una nueva etiqueta (con la aprobación de la política, por supuesto) utilizando las funciones de la API **libselinux**. El permiso *process { setfscreate }* puede usarse para permitir que los sujetos creen archivos con una nueva etiqueta programáticamente utilizando la función ***setfscreatecon**(3)*, anulando las reglas predeterminadas y las declaraciones de transición.
4. Un gestor de objetos (OM) puede imponer una etiqueta predeterminada que puede estar integrada en el OM o obtenerse a través de un archivo de configuración (como los utilizados por el [**Soporte SELinux para X-Windows**](x_windows.md#x-windows-selinux-support)).
5. Utilizar un '[**identificador de seguridad inicial**](sid_statement.md#security-id-sid-statement)' (o SID inicial). Estos se definen en todas las políticas y se utilizan para establecer un contexto inicial durante el proceso de arranque o si un objeto requiere un valor predeterminado (es decir, si el objeto no tiene ya un contexto válido).

La sección [**Computar Contextos de Seguridad**](computing_security_contexts.md#computing-security-contexts) ofrece detalles sobre cómo se computan algunos de los objetos basados en el kernel.

El lenguaje de políticas de SELinux soporta declaraciones de etiquetado de objetos para archivos y servicios de red que están definidos en las secciones [**Declaraciones de Etiquetado del Sistema de Archivos**](file-labeling-statements.md#file-system-labeling-statements) y [**Declaraciones de Etiquetado de Red**](network_statements.md#network-labeling-statements).

Una visión general del proceso requerido para etiquetar sistemas de archivos que utilizan atributos extendidos (como ext3 y ext4) se discute en la sección [**Etiquetado de Sistemas de Archivos con Atributos Extendidos**](objects.md#labeling-extended-attribute-filesystems).

### Etiquetado de Sistemas de Archivos con Atributos Extendidos

El etiquetado de sistemas de archivos que implementan atributos extendidos[^fn_objs_1] es soportado por SELinux usando:

1. La declaración *fs_use_xattr* dentro de la política para identificar qué sistemas de archivos usan atributos extendidos. Esta declaración se usa para informar al servidor de seguridad cómo etiquetar el sistema de archivos.
2. Un archivo de 'contextos de archivos' que define cuáles deberían ser los contextos iniciales para cada archivo y directorio dentro del sistema de archivos. El formato de este archivo y cómo se construye a partir de la política fuente se describe en la sección [**Archivos de Configuración del Almacén de Políticas - Construcción de los Archivos de Soporte de Etiquetado de Archivos**](policy_store_config_files.md#building-the-file-labeling-support-files)[^fn_objs_2].
3. Un método para inicializar el sistema de archivos con estos atributos extendidos. Esto se logra mediante utilidades de SELinux como ***fixfiles**(8)* y ***setfiles**(8)*. También hay comandos como ***chcon**(1)*, ***restorecon**(8)* y ***restorecond**(8)* que se pueden usar para reetiquetar archivos.

Los atributos extendidos que contienen el contexto SELinux de un archivo pueden ser vistos mediante los comandos *ls -Z* o ***getfattr**(1)* de la siguiente manera:


```
ls -Z myfile
-rw-r--r-- rch rch unconfined_u:object_r:user_home:s0 myfile
```

```
getfattr -n security.selinux myfile
# file_name: myfile
security.selinux="unconfined_u:object_r:user_home:s0

# Where -n security.selinux is the name of the extended
# attribute and 'myfile' is a file name. The security context
# (or label) held for the file is displayed.
```

#### Copiar y Mover Archivos

Asumiendo que la política ha otorgado los permisos correctos, los efectos sobre el contexto de seguridad de un archivo cuando se copia o mueve difieren de la siguiente manera:

- copiar un archivo: toma la etiqueta del nuevo directorio.
- mover un archivo: retiene la etiqueta del archivo.

Sin embargo, si el demonio ***restorecond**(8)* está en ejecución y el archivo [**restorecond.conf**](global_config_files.md#etcselinuxrestorecond.conf) está correctamente configurado, entonces otros contextos de seguridad pueden asociarse al archivo a medida que se mueve o copia (siempre que sea un contexto válido y esté especificado en el archivo [**file_contexts**](policy_config_files.md#contextsfilesfile_contexts)). 

Cabe señalar que también existe el comando ***install**(1)* que admite una opción *-Z* para especificar el contexto de destino.

Los ejemplos a continuación muestran los efectos de copiar y mover archivos:

```
# These are the test files in the /root directory and their current security
# context:
#
-rw-r--r-- root root unconfined_u:object_r:unconfined_t copied-file
-rw-r--r-- root root unconfined_u:object_r:unconfined_t moved-file

# These are the commands used to copy / move the files:
# Standard copy file:
cp copied-file /usr/message_queue/in_queue

# Standard move file:
mv moved-file /usr/message_queue/in_queue

# The target directory (/usr/message_queue/in_queue) is labeled "in_queue_t".
# The results of "ls -Z" on the target directory are:
#
-rw-r--r-- root root unconfined_u:object_r:in_queue_t copied-file
-rw-r--r-- root root unconfined_u:object_r:unconfined_t moved-file
```

Sin embargo, si el demonio *restorecond* está en ejecución:

```
# If the restorecond daemon is running with a restorecond.conf file entry of:
#
/usr/message_queue/in_queue/*

# AND the file_context file has an entry of:
#
/usr/message_queue/in_queue(/.*)? -- system_u:object_r:in_file_t

# Then all the entries would be set as follows when the daemon detects
# the files creation:
#
-rw-r--r-- root root unconfined_u:object_r:in_file_t copied-file
-rw-r--r-- root root unconfined_u:object_r:in_file_t moved-file

# This is because the restorecond process will set the contexts defined
in the file_contexts file to the context specified as it is created in
# the new directory.
```

Esto se debe a que el proceso *restorecond* establecerá los contextos definidos en el archivo de contextos de archivos al contexto especificado cuando se crea en el nuevo directorio.

## Etiquetado de Sujetos

En un sistema GNU / Linux en ejecución, los procesos heredan el contexto de seguridad del proceso principal. Si el nuevo proceso que se genera tiene permiso para cambiar su contexto, se permite una 'transición de tipo', que se discute en la sección [**Transición de Dominio**](domain_object_transitions.md#domain-transition). El lenguaje de políticas admite varias declaraciones para asignar componentes a contextos de seguridad, tales como:

- Declaraciones *user*, *role* y *type*.

y para gestionar su alcance:

- *role_allow* y *constrain*

y para gestionar su transición:

- *type_transition*, *role_transition* y *range_transition*

Las aplicaciones compatibles con SELinux pueden asignar una nueva etiqueta (con la aprobación de la política, por supuesto) utilizando las funciones de la API **libselinux**. Los permisos *process { setexec setkeycreate setsockcreate }* pueden utilizarse para permitir que los sujetos etiqueten procesos, anillos de claves del kernel y sockets programáticamente utilizando las funciones ***setexec**(3)*, ***setkeycreatecon**(3)* y ***setsockcreatecon**(3)* respectivamente, anulando las declaraciones de transición.

El **identificador de seguridad inicial** del *kernel* se usa para asociar una etiqueta especificada con objetos del kernel, incluidos hilos del kernel (tanto los que se crean durante la inicialización como también los hilos del kernel creados posteriormente), sockets privados del kernel y objetos sintéticos que representan recursos del kernel (por ejemplo, la clase "sistema").

Es cierto que los procesos creados antes de la carga inicial de la política también estarán en el SID del kernel hasta que, a menos que haya una política cargada y ya sea una transición definida por la política o un setcon o setexeccon+execve explícito, pero eso es solo la herencia predeterminada típica del comportamiento de creación de tareas para procesos.

El contexto asociado con el **identificador de seguridad inicial** *unlabeled* se utiliza como contexto de respaldo tanto para sujetos como para objetos cuando su etiqueta es invalidada por una recarga de política (su SID no cambia pero el SID se remapea de manera transparente al contexto sin etiqueta). También se asigna como el estado inicial para varios objetos, por ejemplo, inodos, superbloques, etc., hasta que alcanzan un punto donde se puede determinar una etiqueta más específica, por ejemplo, a partir de un xattr o de la política.

## Reutilización de Objetos

A medida que GNU / Linux se ejecuta, crea instancias de objetos y gestiona la información que contienen (leer, escribir, modificar, etc.) bajo el control de los procesos, y en algún momento estos objetos pueden ser eliminados o liberados, permitiendo que el recurso (como bloques de memoria y espacio en disco) esté disponible para su reutilización.

GNU / Linux maneja la reutilización de objetos asegurándose de que cuando un recurso se reasigna, se limpia. Esto significa que cuando un proceso libera una instancia de objeto (por ejemplo, libera memoria asignada de vuelta al pool, elimina una entrada de directorio o archivo), puede quedar información que podría resultar útil si se recolecta. Si esto debería ser un problema, entonces el proceso mismo debería limpiar o destruir la información antes de liberar el objeto (lo que puede ser difícil en algunos casos a menos que el código fuente esté disponible).

[^fn_objs_1]: Estos sistemas de archivos almacenan el contexto de seguridad en un atributo asociado con el archivo.

[^fn_objs_2]: Tenga en cuenta que este archivo contiene los contextos de todos los archivos en todos los sistemas de archivos de atributos extendidos para la política. Sin embargo, dentro de una política modular (y/o módulos CIL), cada módulo describe su propia información de contexto de archivo, que luego se usa para construir este archivo.

---
**[[ PREV ]](subjects.md)** **[[ TOP ]](#)** **[[ NEXT ]](comseccon.md)**

