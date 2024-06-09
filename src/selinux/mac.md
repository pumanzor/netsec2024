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
