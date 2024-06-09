# Contexto de Seguridad

SELinux requiere que un contexto de seguridad esté asociado con cada proceso (o sujeto) y objeto que son utilizados por el servidor de seguridad para decidir si se permite el acceso o no, según lo definido 
por la política.

El contexto de seguridad también se conoce como una 'etiqueta de seguridad' o simplemente etiqueta, lo que puede causar confusión ya que hay muchos tipos de etiquetas dependiendo del contexto.

Dentro de SELinux, un contexto de seguridad se representa como cadenas de longitud variable que definen el usuario de SELinux (esto no es el id. de usuario de Linux. El id. de usuario de Linux se asigna 
al id. de usuario de SELinux mediante archivos de configuración), su rol, un identificador de tipo y un rango o nivel de seguridad MCS/MLS opcional de la siguiente manera:


```
user:role:type[:range]
```
