# Aplicación de Tipo

- [Restricciones](#constraints)
- [Límites](#bounds)

SELinux utiliza un estilo específico de aplicación de tipo (TE) para hacer cumplir el control de acceso obligatorio. Para SELinux, esto significa que todos los [**sujetos**](subjects.md#subjects) y 
[**objetos**](objects.md#objects) tienen un identificador de *tipo* asociado a ellos que luego puede usarse para imponer las reglas establecidas por la política.

El identificador de *tipo* de SELinux es una cadena de longitud variable simple que se define en la política y luego se asocia a un [**contexto de seguridad**](security_context.md#security-context). 
También se utiliza en la mayoría de las [**declaraciones y reglas del lenguaje de SELinux**](policy_languages.md#the-selinux-policy-languages) utilizadas para construir una política que, cuando se carga 
en el servidor de seguridad, hace cumplir la política a través de los administradores de objetos.

Debido a que el identificador de *tipo* (o simplemente 'tipo') está asociado a todos los sujetos y objetos, a veces puede ser difícil distinguir con qué está realmente asociado el tipo (no se ayuda por 
el hecho de que, por convención, los identificadores de tipo terminan en *\_t*). Al final, se trata de comprender cómo se asignan en la propia política y cómo los utilizan los servicios de SELinux 
(aunque las políticas de CIL con espacios de nombres sí ayudan en que un proceso de dominio 'tipo' podría declararse como *msg_filter.ext_gateway.process* con tipos de objetos siendo cualquier otro 
(como *msg_filter.ext_gateway.exec*).

Básicamente, si el identificador de tipo se usa para hacer referencia a un sujeto, se refiere a un proceso de Linux o una colección de procesos (un dominio o tipo de dominio). Si el identificador de 
tipo se usa para hacer referencia a un objeto, entonces especifica su tipo de objeto (es decir, tipo de archivo).

Aunque SELinux se refiere a un sujeto como un proceso activo que está asociado a un tipo de dominio, el alcance de un dominio de aplicación de tipo en SELinux puede variar ampliamente. Por ejemplo, en 
la sencilla [**política del Kernel**](./notebook-examples/selinux-policy/kernel/kern-nb-policy.txt) en los *notebook-examples*, todos los procesos en el sistema se ejecutan en el dominio *unconfined_t*, 
por lo tanto, cada proceso es 'de tipo *unconfined_t*' (lo que significa que puede hacer lo que quiera dentro de los límites de la política estándar de DAC de Linux, ya que todo acceso está permitido 
por SELinux).

Es solo cuando se agregan declaraciones de política adicionales a la política simple que las áreas comienzan a ser confinadas. Por ejemplo, una puerta de enlace externa se ejecuta en su propio dominio 
aislado (*ext_gateway_t*) que no puede ser 'interferido' por ninguno de los procesos *unconfined_t* (excepto para ejecutar o transitar el proceso de la puerta de enlace a su propio dominio). Este escenario 
es similar a la política 'targeted' entregada como estándar en Red Hat Fedora, donde la mayoría de los procesos en el espacio de usuario se ejecutan bajo el dominio *unconfined_t*.

El tipo de SELinux es el tercer componente de un 'contexto de seguridad' y, por convención, los tipos de SELinux terminan en *\_t*, sin embargo, esto no es impuesto por ningún servicio de SELinux 
(es decir, solo se utiliza para identificar el componente de tipo), aunque como se explicó anteriormente, CIL con espacios de nombres hace que la identificación de tipos sea más fácil.

### Restricciones

Es posible agregar restricciones a usuarios, roles, tipos y rangos de MLS, por ejemplo, dentro de un entorno TE, la forma en que los sujetos pueden acceder a un objeto es a través de un 
[***allow***](avc_rules.md#allow) de TE, por ejemplo:

```
allow unconfined_t ext_gateway_t : process transition;
```

Esto establece que un proceso que se ejecuta en el dominio *unconfined_t* tiene permiso para transitar un proceso al dominio *ext_gateway_t*. Sin embargo, podría ser que el escritor de la política quiera 
restringir esto aún más y establecer que esto solo puede ocurrir si el rol del dominio fuente es el mismo que el rol del dominio objetivo. Para lograr esto, se puede imponer una restricción usando una 
declaración de [***constrain***](constraint_statements.md#constrain):

```
constrain process transition ( r1 == r2 );
```

Esto establece que una transición de proceso solo puede ocurrir si el rol de origen es el mismo que el rol de destino, por lo tanto, una restricción es una condición que debe cumplirse para que se otorguen 
uno o más permisos (es decir, una restricción impone restricciones adicionales a las reglas de TE). Cabe señalar que la restricción se basa en una clase de objeto (*proceso* en este caso) y uno o más de 
sus permisos.

Las restricciones del lenguaje de políticas del kernel se definen en la sección de [**Declaraciones de Restricción**](constraint_statements.md#constraint-statements).

### Límites

Es posible agregar límites a usuarios, roles y tipos, sin embargo, actualmente solo los tipos son impuestos por el kernel usando la regla *typebounds* como se describe en la sección 
de [**Soporte Apache-Plus - Descripción General de Límites**](apache_support.md#bounds-overview).

Los límites de usuarios y roles pueden declararse usando CIL, sin embargo, son validados en tiempo de compilación por el compilador de CIL y NO son impuestos por los servicios del kernel de SELinux. 
La sección de [**Reglas de Límites**](bounds_rules.md#bounds-rules) define la regla *typebounds* y también ofrece un resumen de las reglas *userbounds* y *rolebounds*.

---
**[[ PREV ]](rbac.md)** **[[ TOP ]](#)** **[[ NEXT ]](seccon.md)**
