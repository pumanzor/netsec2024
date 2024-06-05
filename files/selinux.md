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


Ahora juan puede cambiar este acceso. jo puede otorgar (y restringir) acceso a este archivo a otros usuarios y grupos o cambiar el propietario del archivo. Estas acciones pueden dejar archivos críticos 
expuestos a cuentas que no necesitan este acceso. juan también puede restringir el acceso para ser más seguro, pero eso es discrecional: no hay forma de que el administrador del sistema lo imponga para
cada archivo en el sistema.

Consideremos otro caso: cuando un proceso de Linux se ejecuta, puede ejecutarse como el usuario root u otra cuenta con privilegios de superusuario. Eso significa que si un adversario de sombrero negro toma 
control de la aplicación, puede usar esa aplicación para acceder a cualquier recurso al que la cuenta de usuario tenga acceso. Para los procesos que se ejecutan como el usuario root, básicamente esto 
significa todo en el servidor Linux.

Piense en un escenario donde quiera restringir a los usuarios la ejecución de scripts shell desde sus directorios personales. Esto puede suceder cuando tiene desarrolladores trabajando en un sistema de 
producción. Le gustaría que vean los archivos de registro, pero no quiere que usen los comandos su o sudo, y no quiere que ejecuten ningún script desde sus directorios personales. ¿Cómo hace eso?

SELinux es una forma de ajustar finamente esos requisitos de control de acceso. Con SELinux, puede definir lo que un usuario o proceso puede hacer. Confina cada proceso a su propio dominio para que el
proceso solo pueda interactuar con ciertos tipos de archivos y otros procesos de dominios permitidos. Esto evita que un hacker secuestre cualquier proceso para obtener acceso a todo el sistema.
