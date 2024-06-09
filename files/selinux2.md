SELinux fue desarrollado como una solución adicional de seguridad para Linux que utiliza el marco de seguridad en el núcleo de Linux. El propósito era permitir una política de seguridad más granular 
que vaya más allá de lo que ofrecen los permisos predeterminados de Lectura, Escritura y Ejecución, y más allá de asignar permisos a las diferentes capacidades disponibles en Linux. 
SELinux hace esto interceptando todas las llamadas al sistema que llegan al núcleo y negándolas por defecto. Esto significa que en un sistema con SELinux habilitado y sin ninguna otra configuración, 
nada funcionará. Para permitir que tu sistema haga cualquier cosa, como administrador tendrás que escribir reglas y colocarlas en una política.

Un ejemplo explica por qué se necesita una solución como SELinux (o su contraparte AppArmor):

"Una mañana, descubrí que mi servidor había sido hackeado. El servidor estaba ejecutando una instalación de SLES completamente parcheada. Tenía un firewall configurado y no ofrecía servicios innecesarios. 
Un análisis más detallado reveló que el hacker había entrado a través de un script PHP vulnerable que formaba parte de uno de los hosts virtuales de Apache que estaban ejecutándose en este servidor. 
El intruso había logrado acceder a un shell usando la cuenta wwwrun que utilizaba el servidor web Apache. Como este usuario wwwrun, el intruso había creado varios scripts en los directorios /var/tmp 
y /tmp, que formaban parte de una botnet que estaba lanzando un ataque de Denegación de Servicio Distribuido contra varios servidores."

Lo interesante de este hackeo es que ocurrió en un servidor donde realmente no había nada mal. Todos los permisos estaban configurados correctamente, pero el intruso logró entrar en el sistema. 
Lo que queda claramente evidente en este ejemplo es que en algunos casos se necesita seguridad adicional, una seguridad que va más allá de lo que ofrece SELinux. Como una alternativa menos completa 
y menos compleja, se puede usar AppArmor.

AppArmor limita las capacidades específicas de los procesos para leer/escribir y ejecutar archivos (y otras cosas). Su enfoque es principalmente que las cosas que ocurren dentro de un proceso no pueden escapar.

En cambio, SELinux utiliza etiquetas adjuntas a objetos (por ejemplo, archivos, binarios, sockets de red) y las utiliza para determinar los límites de privilegios, construyendo así un nivel de confinamiento 
que puede abarcar más que un proceso o incluso todo el sistema.

SELinux fue desarrollado por la Agencia de Seguridad Nacional de los Estados Unidos (NSA), y desde el principio, Red Hat ha estado fuertemente involucrado en su desarrollo. La primera versión de SELinux se 
ofreció en la era de Red Hat Enterprise Linux 4™, alrededor del año 2006. Al principio solo ofrecía soporte para servicios esenciales, pero con los años se ha desarrollado en un sistema que ofrece muchas 
reglas que se recopilan en políticas para ofrecer protección a una amplia gama de servicios.

SELinux se desarrolló de acuerdo con algunos estándares de certificación como Common Criteria y FIPS 140. Debido a que algunos clientes solicitaron específicamente soluciones que cumplían con estos 
estándares, SELinux se volvió rápidamente relativamente popular.

Como una alternativa a SELinux, Immunix, una empresa que fue comprada por Novell en 2005, había desarrollado AppArmor. AppArmor se construyó sobre los mismos principios de seguridad que SELinux, pero 
adoptó un enfoque completamente diferente, donde era posible restringir los servicios exactamente a lo que necesitaban hacer mediante un procedimiento guiado fácil de usar. Sin embargo, AppArmor nunca 
ha alcanzado el mismo estatus que SELinux, incluso si hay algunos buenos argumentos para asegurar un servidor con AppArmor en lugar de con SELinux.

Debido a que muchas organizaciones están solicitando que SELinux esté en las distribuciones de Linux que están utilizando, SUSE ofrece soporte para el marco de SELinux en SUSE Linux Enterprise Server. 
Esto no significa que la instalación predeterminada de SUSE Linux Enterprise Server cambiará de AppArmor a SELinux en un futuro cercano.

### Estado de Soporte

El marco SELinux es compatible con SUSE Linux Enterprise Server. Esto significa que SLES ofrece todos los binarios y bibliotecas necesarios para poder usar SELinux en tu servidor. Sin embargo, puede que falte algún software con el que estés familiarizado de otras distribuciones de Linux.

El soporte para SELinux está en una etapa bastante temprana en SUSE Linux Enterprise Server, lo que significa que puede ocurrir un comportamiento inesperado. Para limitar este riesgo lo más posible, es mejor usar solo los binarios que se han proporcionado por defecto en SUSE Linux Enterprise Server.

### 32.1.2 Entendiendo los Componentes de SELinux

Antes de comenzar la configuración de SELinux, debes conocer un poco sobre cómo está organizado SELinux. Tres componentes juegan un papel:

- El marco de seguridad en el núcleo de Linux
- Las bibliotecas y binarios de SELinux
- La política de SELinux

El núcleo predeterminado de SUSE Linux Enterprise Server soporta SELinux y las herramientas necesarias para gestionarlo. La parte más importante del trabajo del administrador con respecto a SELinux es la gestión de la política.

En la política de SELinux, se aplican etiquetas de seguridad a diferentes objetos en un servidor Linux. Estos objetos suelen ser usuarios, puertos, procesos y archivos. Usando estas etiquetas de seguridad, se crean reglas que definen lo que está permitido y lo que no en un servidor. Recuerda, por defecto SELinux niega todo, y al crear las reglas adecuadas, puedes permitir el acceso que es estrictamente necesario. Por lo tanto, deben existir reglas para todos los programas que desees usar en un sistema. Alternativamente, puedes configurar partes de un sistema para que funcionen en modo no confinado, lo que significa que puertos, programas, usuarios, archivos y directorios específicos no están protegidos por SELinux. Este modo es útil si solo deseas usar SELinux para proteger algunos servicios esenciales, mientras que no te preocupan específicamente otros servicios. Para obtener un sistema realmente seguro, deberías evitar esto.

Para asegurar la protección adecuada de tu sistema, necesitas una política de SELinux. Esta debe ser una política hecha a medida en la que todos los archivos estén provistos de una etiqueta, y todos los servicios y usuarios tengan una etiqueta de seguridad también para expresar qué archivos y directorios pueden ser accedidos por qué usuario y procesados en el servidor. Desarrollar una política de este tipo requiere una gran cantidad de trabajo.

La complejidad de SELinux es también uno de los principales argumentos en contra de su uso. Debido a que un sistema Linux típico es muy complejo, es fácil pasar algo por alto y dejar una abertura que los intrusos pueden aprovechar para ingresar a tu sistema. E incluso si está configurado completamente como debería, sigue siendo muy difícil para un administrador supervisar todos los aspectos con SELinux. Con respecto a la complejidad, AppArmor adopta un enfoque completamente diferente y funciona con procedimientos automatizados que permiten al administrador configurar la protección de AppArmor y entender exactamente lo que está sucediendo.

Ten en cuenta que una política de SELinux disponible libremente podría funcionar en tu servidor, pero es poco probable que ofrezca la misma protección que una política personalizada. SUSE tampoco soporta políticas de terceros.

### Política

Como se mencionó, la política es el componente clave en SELinux. Define reglas que especifican qué objetos pueden acceder a qué archivos, directorios, puertos y procesos en un sistema. Para hacer esto, se define un contexto de seguridad para todos estos. En un sistema SELinux donde se ha aplicado la política para etiquetar el sistema de archivos, puedes usar el comando `ls -Z` en cualquier directorio para encontrar el contexto de seguridad de los archivos en ese directorio. El Ejemplo 32.1: "Configuraciones de Contexto de Seguridad Usando ls -Z" muestra las configuraciones de contexto de seguridad para los directorios en el directorio raíz (/) de un sistema SUSE Linux Enterprise Server con un sistema de archivos etiquetado por SELinux.

#### Ejemplo 32.1: Configuraciones de Contexto de Seguridad Usando ls -Z

    ls -Z
    system_u:object_r:bin_t bin
    system_u:object_r:boot_t boot
    system_u:object_r:device_t dev
    system_u:object_r:etc_t etc
    system_u:object_r:home_root_t home
    system_u:object_r:lib_t lib
    system_u:object_r:lib_t lib64
    system_u:object_r:lost_found_t lost+found
    system_u:object_r:mnt_t media
    system_u:object_r:mnt_t mnt
    system_u:object_r:usr_t opt
    system_u:object_r:proc_t proc
    system_u:object_r:default_t root
    system_u:object_r:bin_t sbin
    system_u:object_r:security_t selinux
    system_u:object_r:var_t srv
    system_u:object_r:sysfs_t sys
    system_u:object_r:tmp_t tmp
    system_u:object_r:usr_t usr
    system_u:object_r:var_t var

La línea más importante en el contexto de seguridad es el tipo de contexto. Esta es la parte del contexto de seguridad que termina en _t. Indica a SELinux qué tipo de acceso se permite al objeto. En la política, se especifican reglas para definir qué tipo de usuario o qué tipo de rol tiene acceso a qué tipo de contexto. Por ejemplo, esto puede suceder utilizando una regla como la siguiente:

    allow user_t bin_t:file {read execute gettattr};

Esta regla de ejemplo establece que el usuario que tiene el tipo de contexto user_t (este usuario se llama el objeto fuente) tiene permiso para acceder a objetos de la clase "archivo" con el tipo de contexto bin_t (el objetivo), utilizando los permisos de lectura, ejecución y getattr.

La política estándar que vas a utilizar contiene una gran cantidad de reglas. Para hacerla más manejable, las políticas a menudo se dividen en módulos. Esto permite al administrador activar o desactivar la protección para diferentes partes del sistema.

Al compilar la política para tu sistema, tendrás la opción de trabajar con una política modular o una política monolítica, donde se utiliza una política enorme para proteger todo en tu sistema. Se recomienda encarecidamente usar una política modular y no una política monolítica. Las políticas modulares son mucho más fáciles de gestionar.



