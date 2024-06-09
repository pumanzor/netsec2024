**Componentes Principales de SELinux**

Componentes principales de SELinux que gestionan la aplicación de la política y se componen de lo siguiente:
- Un **Sujeto** que debe estar presente para que se realice una acción sobre un Objeto (como leer un archivo, ya que la información solo fluye cuando un sujeto está involucrado).
- Un **Administrador de Objetos** que conoce las acciones requeridas para el recurso particular (como un archivo) y puede hacer cumplir esas acciones (es decir, permitir escribir en un archivo si lo permite la política).
- Un **Servidor de Seguridad** que toma decisiones sobre los derechos del sujeto para realizar la acción solicitada sobre el objeto, basándose en las reglas de la política de seguridad.
- Una **Política de Seguridad** que describe las reglas utilizando el Lenguaje de Políticas del Kernel de SELinux.
- Un **Cache de Vectores de Acceso (AVC)** que mejora el rendimiento del sistema al almacenar en caché las decisiones del servidor de seguridad.


**En la implementación actual de SELinux, el servidor de seguridad está integrado en el kernel con la política cargada desde el espacio de usuario a través de una serie de funciones contenidas en la biblioteca libselinux (ver Bibliotecas de Espacio de Usuario de SELinux para más detalles). Los administradores de objetos (OM) y el caché de vectores de acceso (AVC) pueden residir en:**

- **Espacio del kernel**: Estos administradores de objetos son para los servicios del kernel como archivos, directorios, sockets, IPC, etc., y se proporcionan mediante hooks en el subsistema SELinux a través del marco del Módulo de Seguridad de Linux (LSM) (mostrado como Hooks de LSM en la Figura 2) que se discute en la sección del Módulo de Seguridad de Linux y SELinux. El servicio de AVC del kernel de SELinux se utiliza para almacenar en caché la respuesta de los servidores de seguridad a los administradores de objetos basados en el kernel, acelerando así las decisiones de acceso si se realiza la misma solicitud en el futuro.

- **Espacio de usuario**: Estos administradores de objetos se proporcionan con la aplicación o servicio que requiere soporte para MAC y se conocen como aplicaciones o servicios 'conscientes de SELinux'. Ejemplos de estos son: X-Windows, mensajería D-bus (utilizada por el escritorio Gnome), base de datos PostgreSQL, Name Service Cache Daemon (nscd) y el comando passwd de GNU/Linux. Generalmente, estos OM utilizan los servicios AVC integrados en la biblioteca SELinux (libselinux), sin embargo, podrían, si fuera necesario, suministrar su propio AVC o no usar un AVC en absoluto (ver Implementación de Aplicaciones Conscientes de SELinux para más detalles).

La política de seguridad de SELinux (lado derecho de la Figura 2) y sus archivos de configuración de soporte están contenidos en el directorio /etc/selinux. Este directorio contiene el archivo de configuración principal de SELinux, config, que tiene el nombre de la política a cargar (a través de la entrada SELINUXTYPE) y el modo de aplicación inicial de la política en el momento de la carga (a través de la entrada SELINUX). Los directorios /etc/selinux/<SELINUXTYPE> contienen políticas que pueden activarse junto con sus archivos de configuración (por ejemplo, 'SELINUXTYPE=targeted' tendrá su política y archivos de configuración asociados ubicados en /etc/selinux/targeted). Todos los archivos de configuración conocidos se muestran en la sección Archivos de Configuración de SELinux.

SELinux soporta una 'política modular', lo que significa que una política no tiene que ser una única política de origen grande, sino que puede construirse a partir de módulos. Una política modular consiste en una política base que contiene la información obligatoria (como clases de objetos, permisos, etc.), y cero o más módulos de política donde generalmente cada uno soporta una aplicación o servicio en particular. Estos módulos se compilan, enlazan y almacenan en un 'almacén de políticas' donde pueden construirse en un formato binario que luego se carga en el servidor de seguridad (en el diagrama, la política binaria se encuentra en /etc/selinux/targeted/policy/policy.30). Los tipos de políticas y su construcción se tratan en la sección Tipos de Políticas de SELinux.

Para poder construir la política en primer lugar, se requiere el origen de la política (parte superior izquierda de la Figura 2). Esto puede suministrarse de tres maneras básicas:

- Como código fuente escrito utilizando el Lenguaje de Políticas del Kernel, sin embargo, no se recomienda para desarrollos de políticas grandes.
- Usando la Política de Referencia que tiene macros de alto nivel para definir reglas de política. Esta es la forma estándar en que ahora se construyen las políticas para distribuciones de SELinux como Red Hat y Debian y se discute en la sección La Política de Referencia. Cabe señalar que SE para Android también utiliza macros de alto nivel para definir reglas de política.
- Usando CIL (Lenguaje Intermedio Común). Se puede encontrar una visión general en la sección Lenguaje de Políticas de CIL. El https://github.com/DefenSec/dssp es un buen ejemplo.

Para poder compilar y enlazar la fuente de la política y luego cargarla en el servidor de seguridad, se requieren una serie de herramientas (parte superior de la Figura 2).

Para permitir que los administradores del sistema gestionen la política, el entorno de SELinux y etiqueten los sistemas de archivos, se utilizan herramientas y comandos modificados de GNU/Linux. Estos se mencionan a lo largo del Cuaderno según sea necesario y se resumen en Comandos de SELinux. Cabe destacar que existen muchas otras aplicaciones para gestionar la política, sin embargo, este Cuaderno solo se concentra en los servicios principales.

Para asegurar que los eventos de seguridad se registren, GNU/Linux tiene un servicio de auditoría que captura las violaciones de políticas. La sección de Eventos de Auditoría describe el formato de estos eventos de seguridad.

**[[ PREV ]](selinux_overview.md)** **[[ TOP ]](#)** **[[ NEXT ]](mac.md)**
SELinux soporta servicios de red que se describen en la sección Soporte de Redes de SELinux.

La sección del Módulo de Seguridad de Linux y SELinux entra en mayor detalle sobre los módulos LSM/SELinux con un recorrido de un proceso fork(2) y exec(2).
