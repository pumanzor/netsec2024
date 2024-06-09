# Contexto de Seguridad

SELinux requiere que un contexto de seguridad esté asociado con cada proceso (o sujeto) y objeto que son utilizados por el servidor de seguridad para decidir si se permite el acceso o no, según lo definido 
por la política.

El contexto de seguridad también se conoce como una 'etiqueta de seguridad' o simplemente etiqueta, lo que puede causar confusión ya que hay muchos tipos de etiquetas dependiendo del contexto.

Dentro de SELinux, un contexto de seguridad se representa como cadenas de longitud variable que definen el usuario de SELinux (esto no es el id. de usuario de Linux. El id. de usuario de Linux se asigna 
al id. de usuario de SELinux mediante archivos de configuración), su rol, un identificador de tipo y un rango o nivel de seguridad MCS/MLS opcional de la siguiente manera:


```
user:role:type[:range]
```
**Donde:**

*usuario*

- El identificador de usuario de SELinux. Este puede estar asociado con uno o más roles que el usuario de SELinux tiene permitido usar.

*rol*

- El rol de SELinux. Este puede estar asociado con uno o más tipos a los que el usuario de SELinux tiene permitido acceder.

*tipo*

- Cuando un tipo está asociado con un proceso, define a qué procesos (o dominios) puede acceder el usuario de SELinux (el sujeto). Cuando un tipo está asociado con un objeto, define qué permisos de acceso tiene el usuario de SELinux a ese objeto.

*rango*

- Este campo también puede conocerse como un *nivel* y solo está presente si la política admite MCS o MLS. La entrada puede consistir en:
  - Un único nivel de seguridad que contiene un nivel de sensibilidad y cero o más categorías (por ejemplo, *s0*, *s1:c0*, *s7:c10.c15*).
  - Un rango que consiste en dos niveles de seguridad (uno bajo y uno alto) separados por un guion (por ejemplo, *s0 - s15:c0.c1023*).
  
- Estos componentes se discuten en la sección de [**Niveles de Seguridad**](mls_mcs.md#security-levels).


Sin embargo, ten en cuenta que:

1. Las decisiones de acceso relacionadas con un sujeto hacen uso de todos los componentes del **contexto de seguridad**.
2. Las decisiones de acceso relacionadas con un objeto hacen uso de los componentes de la siguiente manera:
    1. El usuario se establece en un usuario especial llamado *system_u* o se establece en el id. de usuario de SELinux del proceso creador. Es posible agregar restricciones a los usuarios dentro de la política basadas en su clase de objeto (un ejemplo de esto es la opción UBAC (Control de Acceso Basado en Usuarios) de la Política de Referencia).
    2. El rol generalmente se establece en un rol interno especial de SELinux llamado *object_r*, aunque la versión de la política 26 con el kernel 2.6.39 y superiores admiten transiciones de rol en cualquier clase de objeto. Es posible agregar restricciones al rol dentro de la política basadas en su clase de objeto.

La sección [**Cálculo de Contextos de Seguridad**](computing_security_contexts.md#computing-security-contexts) describe cómo SELinux calcula los componentes del contexto de seguridad basándose en un *contexto de origen*, *contexto de destino* y la *clase* del objeto.

Los ejemplos a continuación muestran contextos de seguridad para procesos, directorios y archivos (nota que la política no admitía MCS o MLS, por lo tanto, no hay campo *nivel*):

**Ejemplo de Contexto de Seguridad de un Proceso:**

```
# These are process security contexts taken from a ps -Z command
# (edited for clarity) that show four processes:

LABEL                                       PID  TTY   CMD
unconfined_u:unconfined_r:unconfined_t      2539 pts/0 bash
unconfined_u:message_filter_r:ext_gateway_t 3134 pts/0 secure_server
unconfined_u:message_filter_r:int_gateway_t 3138 pts/0 secure_server
unconfined_u:unconfined_r:unconfined_t      3146 pts/0 ps

# Note the bash and ps processes are running under the
# unconfined_t domain, however the secure_server has two instances
# running under two different domains (ext_gateway_t and
# int_gateway_t). Also note that they are using the
# message_filter_r role whereas bash and ps use unconfined_r.
#
# These results were obtained by running the system in permissive mode.
```

**Example Object Security Context:**

```
# These are the message queue directory object security contexts
# taken from an ls -Zd command (edited for clarity):
system_u:object_r:in_queue_t /usr/message_queue/in_queue
system_u:object_r:out_queue_t /usr/message_queue/out_queue

# Note that they are instantiated with system_u and object_r
```

```
# These are the message queue file object security contexts
# taken from an ls -Z command (edited for clarity):
/usr/message_queue/in_queue:
unconfined_u:object_r:in_file_t Message-1
unconfined_u:object_r:in_file_t Message-2
/usr/message_queue/out_queue:
unconfined_u:object_r:out_file_t Message-10
unconfined_u:object_r:out_file_t Message-11

# Note that they are instantiated with unconfined_u as that was
# the SELinux user id of the process that created the files
# (see the process example above). The role remained as object_r.
```
