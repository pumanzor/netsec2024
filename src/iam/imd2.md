**Diseño de Estrategia de Identificación y Autenticación (5.2)**

**Objetivos**

- Explicar las opciones de diseño y aspectos de la estrategia de identificación y autenticación.

**Resumen**

El uso de la gestión de identidades durante las conexiones iniciales y la autenticación a través de múltiples sistemas refleja la evolución dramática, si no revolucionaria, en la que los mercados, 
los individuos y los gobiernos han tenido que enfrentarse a la identidad digital de diferentes maneras. Podemos ver tres grandes eras en esta evolución:

**La primera era**, al inicio de la era de Internet, utilizaba conceptos de identidad en línea o digital que coincidían estrechamente con las prácticas comerciales, gubernamentales y personales existentes
en ese momento. Una persona específica tendría múltiples archivos de identidad, uno con cada empresa o agencia con la que tuviera tratos, y todos podrían contener información diferente sobre esa persona o 
reflejar diferentes puntos en el tiempo cuando se creó el archivo de identidad.

**La segunda era de cambio** comenzó cuando las redes sociales en línea se volvieron generalizadas, y otras empresas en línea permitirían a los clientes iniciar sesión en sus sistemas utilizando una de sus 
identidades de redes sociales en línea (OSM). En poco tiempo, los servicios de identificación de Facebook, LinkedIn, Google, Apple y Microsoft se convirtieron en líderes del mercado y estaban proporcionando
relaciones de confianza transitiva de esta manera.

**La tercera era de cambio** despegó en algún momento entre 2015 y 2020. Había un auge existente de sentido comercial y de mercado, pero los individuos querían soberanía de datos. Querían poseer los datos 
sobre sus hábitos en línea, acciones, decisiones y transacciones, en lugar de que fueran propiedad de los enormes agregadores de datos de los operadores de redes sociales en línea. Nuevas tecnologías como 
blockchain ofrecieron el potencial de que las identidades digitales soberanas se pusieran en uso, y se propusieron y atrajeron gran interés una variedad de esquemas de identidad y credenciales. 
La COVID-19 trajo un crecimiento explosivo al trabajo desde casa, las compras en línea, la telemedicina y, desafortunadamente, nuevas ocurrencias increíblemente inventivas de fraude cibernético.

Varios países, desde Estonia hasta Canadá, han hecho avances significativos hacia la implementación de identificaciones digitales para sus ciudadanos. La UE ha lanzado varias iniciativas para mejorar y 
agilizar los servicios de identificación digital y el comercio electrónico. Ninguna de estas fuerzas de cambio, por supuesto, ha impulsado a los mercados hacia un nuevo conjunto de estándares y prácticas 
ampliamente adoptados. Los sistemas en línea actuales dependen de tecnologías y conceptos desarrollados y madurados durante 10 a 15 años para gestionar identidades y su autenticación a través de una 
ecología multiorganizacional. El cambio puede estar en camino; hasta que llegue, examinemos en más detalle cómo funcionan estas tecnologías actuales. Clave para esas tecnologías, como el inicio de sesión 
único (SSO) y la gestión federada de identidades (FIM), es el uso del almacén de identidades y su papel en la creación y uso de credenciales.

**El Almacén de Identidades**

A lo largo de los años, un número creciente de sistemas ha hecho que mantener almacenes de identidades separados sea costoso y propenso a errores. Por lo tanto, las organizaciones comenzaron a buscar mecanismos para simplificar el mantenimiento de credenciales, reducir la carga sobre los usuarios para gestionar múltiples credenciales y estandarizar los servicios de identidad en sus diversos entornos.

Los primeros sistemas de federación se basaban en servicios de scripting para pasar credenciales entre un almacén de identidades central y diferentes sistemas. El scripting era relativamente simple de implementar, pero era débil en su capacidad para escalar y vulnerable a la interceptación de credenciales y posterior suplantación. Varios enfoques técnicos diferentes han evolucionado para abordar las demandas competitivas de identidad, autenticación y autorización. Este proceso refleja la evolución de los protocolos y estándares de comunicación, las crecientes capacidades de los sistemas y la creciente dependencia de los sistemas de información para mantener la identidad organizacional.

Algunos ejemplos bien conocidos de estos repositorios son Kerberos, Remote Authentication Dial-in User Service (RADIUS), Lightweight Directory Access Protocol (LDAP), Open Authorization (OAuth)/OAuth 2.0, Security Assertion Markup Language (SAML), OpenID, OpenID Connect, FIDO (FIDO U2F, FIDO UAF, FIDO2) y Web Authentication (WebAuthn).

**Sistemas de Gestión de Credenciales**

Una credencial es la vinculación entre un autenticador y un identificador (usuario/servicio/sistema). El Sistema de Gestión de Credenciales (CMS) es una forma establecida de emitir y gestionar credenciales basadas en software. El software CMS puede ser parte de sistemas de infraestructura de clave pública (PKI) y puede utilizarse para emitir identidades de autenticación de dos factores (2FA). Las credenciales pueden ser recopiladas y gestionadas por un proveedor de servicios de credenciales (CSP). Ejemplos de credenciales incluyen, pero no se limitan a, tarjetas inteligentes, claves criptográficas privadas/públicas y certificados digitales.

En 2009, el gobierno federal de los EE. UU. se dio cuenta de que se necesitaba un marco para la gestión de identidades en las agencias federales para asegurar el cumplimiento en todo el sector federal. Publicaron la arquitectura FICAM, que proporcionaba reglas comunes de Gestión de Acceso a Credenciales de Identidad (ICAM) para construir una arquitectura sólida de credenciales en las agencias federales. La Hoja de Ruta y Guía de Implementación de FICAM Versión 2.0 tiene el siguiente proceso de inscripción en cinco pasos:

1. **Patrocinio.** Una entidad autorizada patrocina a los reclamantes para una credencial con un CSP.
2. **Inscripción.** El reclamante patrocinado se inscribe para las credenciales. Este paso incluiría la verificación de identidad, que podría incluir la captura de datos biográficos y biométricos.
3. **Producción de Credenciales.** Las credenciales se producen como tarjetas inteligentes, claves criptográficas privadas/públicas o certificados digitales.
4. **Emisión.** Se emite la credencial al reclamante.
5. **Gestión del Ciclo de Vida de la Credencial.** Las credenciales se mantienen a través de actividades que incluyen revocación, reemisión, reinscripción, expiración, suspensión o reinstalación.

Esta arquitectura y guía pueden usarse como referencia para cómo un CMS puede implementarse en varias organizaciones.

Aunque FICAM proporciona pautas útiles, se actualizó por última vez en diciembre de 2011. A finales de 2020, el director de información del gobierno de los EE. UU. y la Administración de Servicios Generales comenzaron un esfuerzo de migración, actualización y reestructuración de estas conocidas como la Hoja de Ruta y Guías de los Programas de Gestión de Identidad Federal. Los profesionales de seguridad que manejan procesos de gestión de identidad y credenciales federales pueden encontrar útil esta arquitectura FICAM en evolución. Otros sistemas más actuales, como las Directrices de Identidad Digital del NIST (Publicación Especial 800-63) y el Anexo 9 (Control de Acceso) de ISO 27001, también pueden ser útiles.

En 2018, NIST emitió la SP 800-63, que proporciona una visión más actualizada de la gestión de credenciales. Su modelo de identidad digital, mostrado en la Figura 5.2, ilustra el uso de la PKI para proporcionar servicios de autenticación de identidad basados en certificados.

Piensa en este modelo como la implementación en tiempo real del ciclo de vida de la identidad. El flujo en este modelo comienza con un usuario, en el papel de solicitante, entrando en un proceso de inscripción y verificación de identidad con un CSP, como Google, Facebook, LinkedIn, Outlook Live o incluso un CSP interno patrocinado por una organización. La siguiente acción del usuario es como reclamante, en la que intenta acceder a un servicio como un potencial suscriptor, lo que lo lleva a interactuar con el verificador para autenticar sus credenciales con el CSP. Esto eleva al usuario-como-reclamante al rol de suscriptor. Todo esto resulta en que la parte confiada (RP), quien llevará a cabo el trabajo real de la sesión con el usuario-como-suscriptor, tenga la certeza que necesita para llevar a cabo la sesión como una sesión autenticada.

La confianza se ha transmitido del CSP a través del verificador hasta la RP.


Autenticacion

Autenticacion Puede definirse como la verificación de una reclamación de identidad por parte de un usuario, proceso o dispositivo, a menudo como un requisito previo para otorgarle acceso a recursos dentro de un sistema. Esto puede hacerse una vez o varias veces durante una sesión particular, jornada laboral u otro período de actividad que consista en múltiples pasos y tareas. Por ejemplo:

- Un empleado conduce su coche privado hacia las instalaciones de la organización, pero primero debe mostrar su tarjeta de identificación a un guardia de seguridad en la puerta de entrada.
- El empleado luego entra al edificio por una entrada de empleados y usa su tarjeta de identificación para pasar por un punto de control físico como un torniquete o recepcionista.
- Luego, el empleado usa su tarjeta de identificación para desbloquear su estación de trabajo e inicia sesión en el sistema.
- El empleado se conecta a su correo electrónico, a la plataforma de aplicaciones que usará la mayor parte del día y a otros recursos.

A medida que transcurre el día, el empleado intenta acceder a numerosos archivos, bases de datos u otros recursos. Cada uno de estos intentos, desde el desafío del guardia de seguridad mientras conducen (y se detienen, se presume, en la puerta), hasta los intentos de acceder a un archivo en particular, son oportunidades para autenticar a ese usuario. Más específicamente, cada intento puede usarse para validar lo siguiente:

- El ID de usuario que se utiliza para obtener acceso está registrado y coincide sin error.
- El ID de usuario y la persona que lo usa o lo presenta están correctamente asociados entre sí.
- El ID o las credenciales asociadas no están suspendidas.

El paso de autenticación no implica tomar ninguna acción para aprobar o desaprobar la acción solicitada por el usuario. Más bien, el paso de autorización aplica privilegios definidos para solicitar permiso para actuar.

Es importante mantener clara la distinción entre la verificación de identidad y la autenticación. La verificación de identidad es la decisión inicial de que la reclamación de identidad del usuario puede ser validada por evidencia o atestación aceptable de terceros. La autenticación es la decisión en tiempo real de que una identidad emitida por el sistema que reclama tener derechos de acceso a ese sistema puede ser verificada como (a) una identidad válida emitida por el sistema, que (b) está siendo utilizada o presentada por el sujeto al que se le ha emitido.

Autorizacion

autorizacion proporciona a los usuarios la capacidad de solicitar que se realicen diversas modificaciones a su identidad y a los permisos asociados. Los usos rutinarios de esto pueden incluir:

- Cambiar una contraseña, frase de paso, número de identificación personal (PIN) u otro parámetro de desafío similar.
- Cambiar o actualizar una dirección física (residencial o laboral), números de teléfono u otros elementos relacionados.
- Solicitar acceso a recursos en un servidor, sistema, extranet o repositorio de documentos.
- Solicitar o intentar usar una aplicación o plataforma de aplicaciones que requiera que cada usuario cree y use una identidad separada para ello.

La forma más sencilla de ver esto es que todos implican solicitudes de acceso. El usuario intenta acceder a servicios, que son objetos, para modificar valores registrados en otros objetos, como el almacén de identidades.

Como con cualquier intento de acceso a cualquier objeto, estos deben gestionarse mediante permisos.


Self-Service identity management proporciona a los usuarios la capacidad de solicitar que se realicen diversas modificaciones a su identidad y a los permisos asociados. Los usos rutinarios de esto pueden incluir:

- Cambiar una contraseña, frase de paso, número de identificación personal (PIN) u otro parámetro de desafío similar.
- Cambiar o actualizar una dirección física (residencial o laboral), números de teléfono u otros elementos relacionados.
- Solicitar acceso a recursos en un servidor, sistema, extranet o repositorio de documentos.
- Solicitar o intentar usar una aplicación o plataforma de aplicaciones que requiera que cada usuario cree y use una identidad separada para ello.

La forma más sencilla de ver esto es que todos implican solicitudes de acceso. El usuario intenta acceder a servicios, que son objetos, para modificar valores registrados en otros objetos, como el almacén de identidades.

Como con cualquier intento de acceso a cualquier objeto, estos deben gestionarse mediante permisos.

Accounting

Accounting es la función de gestión de identidades que lleva un registro de cada acción que involucra cada identidad definida en el sistema. Es la función que proporciona a los usuarios la fecha y hora de su último inicio de sesión exitoso o fallido, por ejemplo. La contabilidad proporciona la información detallada necesaria para apoyar la evaluación de seguridad, revisión y auditoría de un sistema. Al hacerlo, la función de contabilidad implementa la no repudio: establece la evidencia que evita que los usuarios intenten negar que realizaron o intentaron realizar acciones particulares.

Como una función vital del almacén de identidades (u otras estructuras de datos en el corazón del sistema IAM), captura información sobre cada intento de acceder al sistema o a sus recursos, y si esos intentos fueron exitosos y se concedió acceso, o los motivos por los cuales se negó.

Estos datos desempeñan un papel importante en numerosas investigaciones, que van desde la resolución de problemas de cuentas y accesos hasta el uso indebido de recursos. Pueden y deben considerarse una fuente de evidencia admisible en procedimientos legales y a menudo son el foco de solicitudes de descubrimiento digital. También es uno de los conjuntos de datos importantes utilizados como parte de la monitorización rutinaria de la seguridad de los sistemas. Por ejemplo, un usuario básico puede no tener permiso para instalar software, ya que no tiene una función laboral que lo requiera. Los intentos pueden indicar un comportamiento inapropiado por su parte o la presencia de instaladores de malware que intentan ejecutar software no autorizado. Aunque una herramienta de permitido/bloqueado de software puede prevenir que la instalación ocurra, la función de contabilidad en IAM debe registrar esto.

Los eventos desencadenantes son la ocurrencia de acciones que pueden requerir la toma de decisiones humanas para resolver. Ejemplos pueden incluir intentos de usuarios de ir más allá de los límites establecidos por los privilegios de acceso de su identidad (ya sea una falla de autenticación o autorización). Estos desencadenantes podrían causar que se activen alarmas en tiempo real o ser parte de informes de estado rutinarios por parte del sistema.

