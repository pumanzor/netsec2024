# Sujetos

Un sujeto es una entidad activa que generalmente toma la forma de una persona, proceso o dispositivo que causa el flujo de información entre objetos o cambia el estado del sistema.

Dentro de SELinux, un sujeto es un proceso activo y tiene un [**contexto de seguridad**](security_context.md#security-context) asociado con él. Sin embargo, un proceso también puede ser referido como 
un objeto dependiendo del contexto en el que se tome, por ejemplo:

1. Un proceso en ejecución (es decir, una entidad activa) es un sujeto porque causa el flujo de información entre objetos o puede cambiar el estado del sistema.
2. El proceso también puede ser referido como un objeto porque cada proceso tiene una clase de objeto asociada[^fn_sub_1] llamada ***proceso***. Este 'objeto' proceso define qué permisos la política
3. permite otorgar o denegar en el proceso activo.

Un ejemplo de los escenarios anteriores se da en la sección [**Permitir a un Proceso Acceder a Recursos**](objects.md#allowing-a-process-access-to-resources).

En SELinux, los sujetos pueden ser:

**Confiables**: Generalmente son comandos, aplicaciones, etc., que han sido escritos o modificados para soportar funcionalidades específicas de SELinux para hacer cumplir la política de seguridad 
(por ejemplo, el kernel, init, pam, xinetd y login). Sin embargo, también puede cubrir cualquier aplicación que la organización esté dispuesta a confiar como parte del sistema general. Aunque 
(dependiendo de tu nivel de paranoia), la mejor política es no confiar en nada hasta que se haya verificado que cumple con la política de seguridad. Generalmente, estas aplicaciones confiables 
ejecutarían en su propio dominio (por ejemplo, el demonio de auditoría podría ejecutarse bajo auditd\_t) o agruparse juntas (por ejemplo, los comandos ***semanage**(8)* y ***semodule**(8)* podrían 
agruparse bajo *semanage_t*).

**No confiables**: Todo lo demás.

[^fn_sub_1]: La clase de objeto y sus permisos asociados se explican en [**Apéndice A - Clases de Objetos y Permisos - Clase de Objeto Proceso**](object_classes_permissions.md#process-object-class)

---
**[[ PREV ]](seccon.md)** **[[ TOP ]](#)** **[[ NEXT ]](objects.md)**
