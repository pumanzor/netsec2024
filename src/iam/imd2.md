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

**Autenticación sin Contraseña**

Muchas brechas de seguridad son causadas por contraseñas débiles, reutilizadas y robadas. La autenticación sin contraseña implica verificar la identidad de un usuario con algo distinto a una contraseña. Aunque algunos argumentan a favor de los beneficios de la autenticación sin contraseña, el denominador común son los problemas que han plagado a las contraseñas; por ejemplo, son fácilmente comprometidas, costosas y difíciles de gestionar, y proporcionan una mala experiencia de usuario. La autenticación sin contraseña puede adoptar muchas formas dependiendo del caso de uso, incluyendo notificaciones push o autenticación biométrica como huellas dactilares.

**Gestión de Sesiones**

Las sesiones se crean, gestionan, soportan y luego se terminan mediante una variedad de protocolos que forman parte de la capa de sesión, o Capa 5, del modelo de red de 7 capas OSI. Algunos de estos protocolos interactúan con las funciones de gestión de identidad y control de acceso en los puntos finales, servidores u otros dispositivos reales o virtualizados y con los IDs de usuario en cuyo nombre se ha creado y se está soportando la sesión.

Desde la perspectiva de IAM, la gestión de sesiones autenticadas es el conjunto de actividades que se centran en garantizar que el sistema mantenga un camino ininterrumpido de protección para los recursos durante toda la sesión. Esto involucra a los sistemas IAM en uso por todos los nodos involucrados en la sesión, y, en la mayoría de los casos, esto se basará en certificados x.509. El segundo de los diez principales riesgos de seguridad de aplicaciones web de OWASP es la autenticación y gestión de sesiones rota. RFC 2965 proporciona un ejemplo de cómo mantener la gestión de sesiones con cookies. Cuando un usuario accede a un sitio web, las acciones e identidad del usuario se rastrean a través de varias solicitudes de ese sitio web. El estado de estas interacciones se mantiene en una cookie de sesión. La evidencia de este estado se mantiene vinculando todas las nuevas conexiones a lo largo de una sesión con la cookie. El manejo de cookies logra la no repudio, aprovechando efectivamente una pista de auditoría de la actividad de la sesión.

Aunque comúnmente consideramos la gestión de sesiones como un requisito para gestionar y controlar el acceso a recursos en línea como una cuenta bancaria, no se limita a esta área. La gestión de sesiones es el proceso de rastrear y asegurar múltiples solicitudes a cualquier servicio provenientes del mismo sujeto. Primero, el sujeto debe ser identificado como un usuario legítimo. Segundo, se rastrea información adicional como cuándo (fecha y hora), desde dónde se accede lógicamente (dirección IP o MAC) y dónde está físicamente el sujeto (qué puerta, torniquete). Por último, se rastrea cuándo termina la sesión y qué acciones se tomaron durante la sesión.

La presentación de la autenticación proporciona la información como un identificador de sesión (ID de sesión). Los IDs de sesión son valores largos y aleatorios para hacerlos inviables de adivinar, y solo se usan una vez, de ahí el término "nonce" o por qué los números solo pueden usarse una vez.

Con la mayoría de las transferencias bancarias, por ejemplo, se crea un número de 30 dígitos cuando se inicia una transferencia. Este valor puede usarse más tarde para verificar quién, cuándo y dónde comenzó la transferencia. De manera similar, cuando un usuario inicia sesión en un reino de seguridad Kerberos, el ID del evento es 4768. Luego se solicita y genera un ticket de autenticación de Kerberos, y los códigos de evento asociados proporcionarán la función de auditoría necesaria siguiendo la solicitud.

Una organización debe rastrear todos los IDs de sesión y estar preparada para terminar forzosamente las sesiones de usuarios o sistemas conectados cuando se alcanza un período de inactividad, como en la banca por internet, o cuando ocurren anomalías dentro de una sesión. Estos pueden ser un cambio repentino de fuente, como un cambio en la dirección IP de origen, múltiples inicios de sesión detectados, que ocurre cuando los usuarios comparten los detalles de su cuenta, o un token de acceso de usuario se usa dos veces para iniciar sesión en un edificio sin un cierre de sesión previo.

Aunque la creación de un ID de sesión es automática y aleatoria, el uso de cookies presenta otro conjunto de problemas potenciales para la gestión de sesiones, ya que el ID de sesión a menudo se almacena dentro de la cookie. Si se puede capturar la cookie de sesión de un usuario o su transmisión es retrasada por un atacante, podría ser posible simplemente reproducir la cookie en un sistema, permitiendo así al atacante iniciar sesión con lo que son, esencialmente, credenciales robadas. Esto se conoce como una repetición de sesión o simplemente un ataque de repetición.

**Implementación de Gestión de Identidad y Acceso (IAM)**

La parte más difícil y más importante de un proyecto de IAM es implementar la política creada. Hay varias formas de implementar. El primer paso para una implementación exitosa es comprender las necesidades, desafíos y deseos de su organización. Cada organización es diferente; algunas tienen una alta tasa de rotación de empleados, mientras que otras son más estables por naturaleza. Algunas basan la mayoría o todos sus sistemas en la nube, mientras que otras organizaciones más tradicionales tienen la mayoría o todos sus sistemas internamente. El proyecto IAM requiere una revisión meticulosa de los activos, necesidades empresariales y capacidades de una organización, ya que un sistema IAM debe identificar, autenticar y autorizar a individuos, procesos, sistemas y dispositivos que utilizan los diferentes recursos de la organización.

La implementación de IAM es la implementación de los requisitos del ciclo de vida de la identidad y debe manejarse en consecuencia. Implementar un IAM no reduce la responsabilidad de la organización de asegurar que sus procesos se manejen según lo deseado y de mantener los controles relevantes para detectar y reducir las posibilidades de incumplimiento.

**Modelo de Identidad ISO**

ISO está desarrollando un marco para la gestión de identidades (ISO/IEC FDIS 24760-1). Su estándar elaborará trabajos previos, incluyendo la serie ISO 2700x que identifica el control de acceso (AC) como uno de sus requisitos fundamentales. La norma ISO 24760 incluirá referencias a la terminología, arquitectura y requisitos. Hay otros estándares ISO que abordan la gestión de identidades (IdM/IAM), incluyendo la serie ISO 29100 que aborda la privacidad, la ISO 29003 sobre Verificación y Prueba de Identidad, y otros.

**Gestión de Identidades Federadas (FIM)**

Una federación de identidades se aplica donde uno o más sistemas permiten a los usuarios iniciar sesión basándose en la autenticación contra uno de los sistemas que participan en la federación. Cuando diferentes organizaciones tienen la necesidad de compartir información común, se buscan soluciones FIM. Pensemos en empresas que usan plataformas de redes sociales como LinkedIn y Twitter pero tienen diferentes modelos de negocio y objetivos y misiones corporativas.

A pesar de sus diferentes estrategias y objetivos comerciales, comparten una base de clientes común. Los clientes comunes entre LinkedIn y Twitter pueden, en ocasiones, querer que la información que reside en la plataforma de un proveedor de servicios (SP) aparezca automáticamente y de manera sincronizada en la plataforma de otro SP.

FIM actualmente utiliza dos estándares ampliamente aceptados, SAML y OAuth, para proporcionar declaraciones legibles por humanos y procesables por máquinas sobre identidad, autenticación y autorización.

Cada uno utiliza tecnologías y enfoques diferentes para abordar las mismas necesidades fundamentales. Ambos están ampliamente utilizados en el mercado, y los marcos de implementación como OpenID Connect se basan en una u otra de estas arquitecturas. También hay una arquitectura de referencia promulgada por la organización Open Authentication, llamada OATH, que busca alejarse aún más de los servicios propietarios de identidad y autenticación. En un foro digital reciente de KNOW Identity, varios de los panelistas expresaron que los grandes actores del sistema, como Microsoft y Apple, ya no desean monetizar la identidad como servicio, y en su lugar ven las oportunidades comerciales que crea una identidad digital omnipresente y confiable.

La gestión de identidades se trata de confianza. Un servidor de autenticación debe confiar en las credenciales proporcionadas por una entidad. Con todos los sistemas de gestión de identidades, debe adoptarse el concepto de "Confiar, pero verificar". La identificación es la afirmación de una identidad única, y la autenticación es la verificación de esa afirmación. Dentro de una red o dominio, estos dos procesos pueden ser llevados a cabo por Kerberos, que proporciona el proceso de tres pasos de autenticación, autorización y contabilidad.

Sin embargo, esta necesidad de verificar se vuelve más difícil cuando un conjunto de credenciales de una organización puede usarse para acceder a servicios en una organización diferente: usar tus credenciales de Facebook para iniciar sesión en LinkedIn, por ejemplo. FIM permite este proceso de crear una relación de confianza entre diferentes dominios de seguridad. Estos dominios de confianza luego proporcionan acceso (verificación) utilizando identidades digitales comunes que consisten en tres componentes: el cliente o principal, el SP o RP, y el proveedor de identidad (IdP).

El IdP es un servicio de intermediación. Su papel es proporcionar la afirmación de que el principal es quien o lo que dice ser. El SP mantiene un servidor de autorización y es responsable de la decisión final de aceptar o rechazar. El IdP también se conoce como IdP residente (local o titular), lo que significa que su papel se limita a la afirmación de identidades dentro de su propio dominio de seguridad (confianza). Dentro del modelo FIM, cada organización o dominio de seguridad (confianza) se convertirá en un IdP federado, lo que significa que proporcionará la afirmación de la validez de las credenciales pertenecientes a un dominio de seguridad (confianza) diferente.

La Figura 5.3 muestra un ejemplo de los pasos involucrados en FIM:

1. El usuario, Sue, tiene una cuenta en Any Bank Inc. y quiere acceder a su cuenta en línea. Cada vez que hace esto, hace clic en el botón "Login" en su sitio web, lo que genera una solicitud de acceso a su banco.
2. Any Bank Inc. envía una solicitud de verificación al IdP.
3. El IdP presenta a Sue con un ID de inicio de sesión.
4. Sue proporciona algunas credenciales de identificación para verificar su identidad, que se envían para verificación a la base de datos de identidad del IdP.
5. Esta base de datos envía la verificación al IdP.
6. El IdP notifica al banco que la persona que está iniciando sesión es, de hecho, Sue.
7. El banco permite que Sue inicie sesión.


