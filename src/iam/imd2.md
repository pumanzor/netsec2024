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

The Identity Store

Over the years, increasing numbers of systems have made maintaining separate identity stores expensive and error prone. Thus, organizations began seeking mechanisms to simplify the maintenance of credentials to reduce the burden on users to manage multiple credentials and to standardize the identity services in their various environments.

Early federation systems relied on scripting services to pass credentials between a central identity store and different systems. Scripting was relatively simple to implement but were weak in their ability to scale and vulnerable to credential interception and subsequent spoofing. Several different technical approaches have evolved to address the competing demands of identity, authentication, and authorization. This process reflects the evolution of communication protocols and standards, increasing systems capabilities, and increasing reliance oninformation systems to maintain organizational identity.

A few well-known examples of such repositories are Kerberos, Remote Authentication Dial-in User Service (RADIUS), Lightweight Directory Access Protocol (LDAP), Open Authorization (OAuth)/OAuth2.0, Security Assertion Markup Language (SAML), OpenID, OpenID Connect, FIDO (FIDO U2F, FIDO UAF, FIDO2), and Web Authentication (WebAuthn).

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

