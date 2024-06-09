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
