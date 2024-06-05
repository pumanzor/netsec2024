## Introducción

Security Enhanced Linux o SELinux es un mecanismo avanzado de control de acceso incorporado en la mayoría de las distribuciones modernas de Linux. Fue desarrollado inicialmente por la Agencia de Seguridad 
Nacional de los Estados Unidos (NSA) para proteger los sistemas informáticos de intrusiones maliciosas y manipulaciones. Con el tiempo, SELinux se lanzó al dominio público y varias distribuciones 
lo han incorporado en su código.

Muchos administradores de sistemas encuentran SELinux un territorio algo inexplorado. El tema puede parecer abrumador y, en ocasiones, bastante confuso. Sin embargo, un sistema SELinux configurado 
correctamente puede reducir significativamente los riesgos de seguridad, y conocer un poco sobre él puede ayudarte a solucionar mensajes de error relacionados con el acceso. 

## Por qué SELinux

Antes de comenzar, comprendamos algunos conceptos.

SELinux implementa lo que se conoce como MAC (Mandatory Access Control, Control de Acceso Obligatorio). Esto se implementa además de lo que ya está presente en cada distribución de Linux, 
el DAC (Discretionary Access Control, Control de Acceso Discrecional).

Para entender el DAC, primero consideremos cómo funciona la seguridad de archivos tradicional en Linux.

En un modelo de seguridad tradicional, tenemos tres entidades: Usuario, Grupo y Otros (u, g, o), que pueden tener una combinación de permisos de Lectura, Escritura y Ejecución (r, w, x) en un 
archivo o directorio. Si un usuario juan crea un archivo en su directorio personal, ese usuario tendrá acceso de lectura/escritura a él, y también lo tendrá el grupo juan. La entidad "otros" posiblemente 
no tendrá acceso a él. En el siguiente bloque de código, podemos considerar el contenido hipotético del directorio personal de juan.

Ejecutar un comando como este:

ls -l /home/juan

total 4
drwxrw-r-- 2 juan juan 4096 may 29 13:55 lab2


Ahora juan puede cambiar este acceso. juan puede otorgar (y restringir) acceso a este archivo a otros usuarios y grupos o cambiar el propietario del archivo. Estas acciones pueden dejar archivos críticos 
expuestos a cuentas que no necesitan este acceso. juan también puede restringir el acceso para ser más seguro, pero eso es discrecional: no hay forma de que el administrador del sistema lo imponga para
cada archivo en el sistema.

Consideremos otro caso: cuando un proceso de Linux se ejecuta, puede ejecutarse como el usuario root u otra cuenta con privilegios de superusuario. Eso significa que si un adversario de sombrero negro toma 
control de la aplicación, puede usar esa aplicación para acceder a cualquier recurso al que la cuenta de usuario tenga acceso. Para los procesos que se ejecutan como el usuario root, básicamente esto 
significa todo en el servidor Linux.

Piense en un escenario donde quiera restringir a los usuarios la ejecución de scripts shell desde sus directorios personales. Esto puede suceder cuando tiene desarrolladores trabajando en un sistema de 
producción. Le gustaría que vean los archivos de registro, pero no quiere que usen los comandos su o sudo, y no quiere que ejecuten ningún script desde sus directorios personales. ¿Cómo hace eso?

SELinux es una forma de ajustar finamente esos requisitos de control de acceso. Con SELinux, puede definir lo que un usuario o proceso puede hacer. Confina cada proceso a su propio dominio para que el
proceso solo pueda interactuar con ciertos tipos de archivos y otros procesos de dominios permitidos. Esto evita que un adversario secuestre cualquier proceso para obtener acceso a todo el sistema.

## Modos de SELinux

En cualquier momento, SELinux puede estar en uno de los tres modos posibles:

    Enforcing (Ejecutando)
    Permissive (Permisivo)
    Disabled (Deshabilitado)

En el modo enforcing, SELinux aplicará su política en el sistema Linux y se asegurará de que cualquier intento de acceso no autorizado por parte de usuarios y procesos sea denegado. Las denegaciones de acceso también se escriben en los archivos de registro correspondientes. Hablaremos sobre las políticas de SELinux y los registros de auditoría más adelante.

El modo permissive es como un estado semi-habilitado. SELinux no aplica su política en modo permisivo, por lo que no se deniega ningún acceso. Sin embargo, cualquier violación de la política sigue registrándose en los registros de auditoría. Es una excelente manera de probar SELinux antes de aplicarlo.

El modo disabled es autoexplicativo: el sistema no funcionará con la seguridad mejorada.
Verificación de Modos y Estado de SELinux

Podemos ejecutar el comando getenforce para verificar el modo actual de SELinux.

    getenforce

SELinux debería estar actualmente deshabilitado, por lo que la salida se verá así:

    Disabled

También podemos ejecutar el comando sestatus:

    SELinux status:        disabled

SELinux configuration file

El archivo de configuración principal para SELinux es /etc/selinux/config. Podemos ejecutar el siguiente comando para ver su contenido:

    cat /etc/selinux/config

The output will look something like this:


    # This file controls the state of SELinux on the system.
    # SELINUX= can take one of these three values:
    #     enforcing - SELinux security policy is enforced.
    #     permissive - SELinux prints warnings instead of enforcing.
    #     disabled - No SELinux policy is loaded.
    SELINUX=disabled
    # SELINUXTYPE= can take one of these two values:
    #     targeted - Targeted processes are protected,
    #     minimum - Modification of targeted policy. Only selected processes are protected. 
    #     mls - Multi Level Security protection.
    SELINUXTYPE=targeted


Hay dos directivas en este archivo. La directiva SELINUX dicta el modo de SELinux y puede tener tres valores posibles, como discutimos anteriormente.

La directiva SELINUXTYPE determina la política que se usará. El valor predeterminado es targeted. Con una política targeted, SELinux  permite personalizar y ajustar finamente los permisos de control de acceso. El otro valor posible es MLS (multilevel security), un modo avanzado de protección. Además, con MLS, requiere instalar un paquete adicional.

## Habilitar y Deshabilitar SELinux

Habilitar SELinux es bastante simple; pero a diferencia de deshabilitarlo, debe hacerse en un proceso de dos pasos. Asumimos que SELinux está actualmente deshabilitado y que se ha instalado todos los paquetes de SELinux.

Como primer paso, necesitamos editar el archivo /etc/selinux/config para cambiar la directiva SELINUX a modo permisivo.

    ...
    SELINUX=permissive
    ...

Configuración del estado a permisivo

Configurar el estado a permisivo primero es necesario porque cada archivo en el sistema necesita tener su contexto etiquetado antes de que SELinux pueda ser aplicado. A menos que todos los archivos estén etiquetados correctamente, los procesos que se ejecutan en dominios confinados pueden fallar porque no pueden acceder a archivos con los contextos correctos. Esto puede causar que el proceso de arranque falle o inicie con errores. Presentaremos los contextos y dominios más adelante

Ahora, realizar un reinicio del sistema:

    reboot

## Política de SELinux

En el corazón del motor de seguridad de SELinux está su política. Una política es lo que su nombre implica: un conjunto de reglas que definen los derechos de seguridad y acceso para todo en el sistema. Y cuando decimos todo, nos referimos a usuarios, roles, procesos y archivos. La política define cómo se relacionan entre sí cada una de estas entidades.

### Terminología Básica

Para entender la política, tenemos que aprender algo de terminología básica. Una política de SELinux define el acceso de los usuarios a los roles, el acceso de los roles a los dominios y el acceso de los dominios a los tipos.

### Usuarios

SELinux tiene un conjunto de usuarios predefinidos. Cada cuenta de usuario regular de Linux está mapeada a uno o más usuarios de SELinux.

En Linux, un usuario ejecuta un proceso. Esto puede ser tan simple como que el usuario juan abra un documento en el editor vi (será la cuenta de juan ejecutando el proceso de vi) o una cuenta de servicio ejecutando el daemon httpd. En el mundo de SELinux, un proceso (un daemon o un programa en ejecución) se llama sujeto.

### Roles

Un rol es como una puerta de entrada que se encuentra entre un usuario y un proceso. Un rol define qué usuarios pueden acceder a ese proceso. Los roles no son como los grupos, sino más bien como filtros: un usuario puede entrar o asumir un rol en cualquier momento, siempre que el rol lo permita. La definición de un rol en la política de SELinux define qué usuarios tienen acceso a ese rol. También define a qué dominios de proceso tiene acceso el propio rol. Los roles entran en juego porque parte de SELinux implementa lo que se conoce como Control de Acceso Basado en Roles (RBAC).

### Sujetos y Objetos

Un sujeto es un proceso y puede afectar potencialmente a un objeto.

Un objeto en SELinux es cualquier cosa sobre la que se pueda actuar. Esto puede ser un archivo, un directorio, un puerto, un socket TCP, el cursor o quizás un servidor X. Las acciones que un sujeto puede realizar sobre un objeto son los permisos del sujeto.

### Dominios para los Sujetos

Un dominio es el contexto dentro del cual puede ejecutarse un sujeto de SELinux (proceso). Ese contexto es como un envoltorio alrededor del sujeto. Le dice al proceso lo que puede y no puede hacer. Por ejemplo, el dominio definirá qué archivos, directorios, enlaces, dispositivos o puertos son accesibles para el sujeto.

### Tipos para los Objetos

Un tipo es el contexto para el contexto de un archivo que estipula el propósito del archivo. Por ejemplo, el contexto de un archivo puede indicar que es una página web, o que el archivo pertenece al directorio /etc, o que el propietario del archivo es un usuario específico de SELinux. El contexto de un archivo se llama su tipo en la jerga de SELinux.

### ¿Qué es la política de SELinux?

La política de SELinux define el acceso de los usuarios a los roles, el acceso de los roles a los dominios y el acceso de los dominios a los tipos. Primero, el usuario debe estar autorizado para ingresar a un rol, y luego el rol debe estar autorizado para acceder al dominio. El dominio, a su vez, está restringido para acceder solo a ciertos tipos de archivos.

La política en sí es un conjunto de reglas que dicen que ciertos usuarios solo pueden asumir ciertos roles, y esos roles estarán autorizados para acceder solo a ciertos dominios. Los dominios, a su vez, solo pueden acceder a ciertos tipos de archivos. La siguiente imagen muestra el concepto:
