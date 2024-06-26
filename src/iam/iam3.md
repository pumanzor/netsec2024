**Autenticación de un solo factor versus autenticación de múltiples factores (SFA y MFA)**

La autenticación dentro de un sistema implica presentar evidencia de que una entidad identificada debe ser permitida para acceder a través de un punto de control. La evidencia estándar para ser permitido 
iniciar sesión en un sistema incluye tres factores principales:

- Algo que sabes, como una contraseña, un PIN o respuestas a preguntas de desafío;
- Algo que tienes, como un token o una tarjeta inteligente; y
- Algo que eres o haces, como biometría o una huella digital.


**SFA** implica que un usuario o entidad proporcione un tipo de evidencia para respaldar una afirmación o solicitud de acceso a un sistema. El factor podría estar relacionado con algo que la entidad sabe, 
tiene, es o dónde se encuentra. Un factor o tipo de evidencia puede tener múltiples metodologías. Por ejemplo, si una entidad proporciona una contraseña y un PIN, eso sería dos metodologías del mismo 
factor (algo que sabes); por lo tanto, estos dos elementos seguirían considerándose un solo factor.

**MFA** implica que una entidad proporcione más de un factor de prueba para autenticar su identidad. Un ejemplo sería proporcionar tanto una contraseña como un escaneo de iris. Cada factor de autenticación 
puede representar un obstáculo adicional a superar por un usuario no autorizado. A medida que aumentan los factores de autenticación, también aumentan las capas de defensa o DiD (defensa en profundidad). 
Los sistemas de múltiples factores pueden aumentar la complejidad de la gestión de sistemas o disminuir o afectar de otra manera la productividad del usuario que intenta acceder al sistema.

Las metodologías de autenticación en auge incluyen la ubicación y el nodo. La autenticación por ubicación utiliza datos de geolocalización que permiten o desautorizan la autenticación desde o hacia
ubicaciones globales específicas. Proveedores de servicios como Netflix y Amazon usan la autenticación por ubicación para protegerse contra la fuga o el robo de contenido de propiedad intelectual. 
La autenticación por nodo permite que el reconocimiento del tipo de dispositivo se utilice como un medio de autenticación, y ejemplos podrían incluir un smartphone específico, una laptop o un escritorio.

Desde una perspectiva de riesgo, SFA, particularmente de la variedad de "lo que sabes", ha demostrado ser inadecuada. Los usuarios parecen incapaces de lidiar con políticas de contraseñas o frases de
contraseña complejas y eligen continuamente contraseñas fáciles de recordar que también son fáciles de hackear. La autenticación de dos factores (2FA) es más segura, pero nuevamente, depende de la postura 
de riesgo y del contexto en el que opera cada organización para determinar si 2FA o una MFA más robusta es justificada.

2FA es ampliamente utilizada tanto por organizaciones como por el público que desea proteger datos sensibles, como sus cuentas de redes sociales y de correo electrónico personal. El mecanismo de 2FA 
más utilizado es una contraseña de un solo uso enviada por mensaje de texto o generada por una aplicación de software.

**Tecnologías y Dispositivos de Control de Acceso**

Existe una variedad de dispositivos (sistemas o componentes, si son lógicos) asociados con el control de acceso lógico y físico que incluyen, pero no se limitan a, tokens de acceso (hardware y software),
llaves y tarjetas. El objetivo de usar dispositivos de control de acceso es agregar una capa adicional de protección para el acceso a los datos. Los dispositivos pueden usarse con otros métodos de 
identificación, proporcionando autenticación de múltiples factores (MFA).

**Tokens de Control de Acceso**
Los tokens de control de acceso toman dos formas distintas y tienen dos usos distintos en el control del acceso a los recursos de los sistemas:

**Tokens de seguridad física** abordan la parte de "algo que tienes" de un desafío MFA. Muchos de estos, en uso hoy en día, utilizan diversas tecnologías de hash criptográfico y números seudorandom que generan un nuevo valor cada vez que el token es activado por el usuario. Estos tokens se activan al presionar un botón, deslizando o insertando el token en un lector adecuado, o mediante otras tecnologías de comunicación de campo cercano que los escanean. Esto actúa como parte de un sistema criptográfico de un solo uso y requiere que el proveedor inicialice tanto el dispositivo token (que puede venir en forma de llavero, tarjeta inteligente u otro formato) como los datos en la cuenta del usuario en sus sistemas. Las aplicaciones de control de acceso también pueden instalarse en los smartphones de los usuarios u otros dispositivos finales, convirtiéndolos en un token físico algo más grande pero a menudo más capaz.

**Tokens de acceso lógico**, que son paquetes de datos generados por un sistema de control de acceso para un ID de usuario autenticado, contienen información sobre esa identidad, los privilegios otorgados y otra información. Estos tokens se pasan a varios programas de aplicaciones o sistemas de servidores, o como parte de los handshakes que establecen sesiones en las redes de la organización. Casi invariablemente, estos contienen una fecha y hora de expiración, que puede ser tan breve como unos pocos minutos si las necesidades de seguridad lo dictan.

**Biometría: ¿Quién Eres?**

Los dispositivos biométricos miden características fisiológicas de un usuario humano, como sus retinas, patrones capilares, la geometría de sus manos o caras, sus huellas dactilares o incluso una grabación de voz. Estas características biométricas proporcionan diferentes medidas de unicidad: de miles de millones de personas, hay muy pocas con las mismas huellas dactilares y un pequeño puñado de personas cuyos escaneos de retina serían casi idénticos. Cada tecnología de medición biométrica puede tener una susceptibilidad diferente a errores y sesgos en sus mediciones; por lo tanto, pocos sistemas de seguridad dependen de una sola técnica biométrica como factor único de autenticación. Sin embargo, utilizados dentro de un sistema de MFA, pueden reducir en gran medida la vulnerabilidad de ese sistema a una intrusión.

La autenticación de acceso a través de biometría comienza tomando mediciones de referencia de las características requeridas y almacenándolas como parte del perfil asociado con la identidad de ese usuario en el sistema. En la mayoría de los sistemas de identificación digital, estas lecturas luego se codifican criptográficamente para que puedan colocarse en una tarjeta inteligente u otro token de seguridad física.

**Inicio de Sesión Único (SSO)**

SSO describe una experiencia de inicio de sesión unificada, desde el punto de vista del usuario final, al acceder a uno o más sistemas. SSO a menudo se refiere como inicio de sesión reducido o gestión de ID federada. La idea es que un usuario solo tenga que iniciar sesión en un único proveedor de autorización y luego se le conceda acceso a todos los recursos para los que tiene privilegios, incluidos activos de información, carpetas y sistemas.

Los sistemas clásicos de SSO proporcionan un repositorio central de credenciales de usuario, como IDs de usuario y contraseñas, asociados con un conjunto de aplicaciones. Los usuarios lanzan varias aplicaciones a través del software cliente de SSO, que abre el programa de aplicación correspondiente y envía las pulsaciones de teclas apropiadas a ese programa, simulando así que el usuario está escribiendo su propio ID y contraseña. Sin embargo, hay algunas limitaciones, riesgos y desafíos al diseñar una arquitectura de SSO:

- **Sistemas heredados.** Algunos sistemas heredados no soportan el uso de mecanismos de SSO y, en algunos casos, es difícil encontrar expertos que sepan trabajar en esos sistemas.
- **Punto único de fallo.** Algunos expertos en seguridad tienden a considerar el SSO como "poner todos los huevos en una canasta". Si un atacante malintencionado obtiene acceso a un conjunto único de credenciales en una organización que implementó SSO, el atacante ahora tiene acceso a todos los recursos asignados a ese usuario. Sin embargo, el riesgo puede mitigarse utilizando mecanismos adicionales de control de acceso como 2FA y limitación de acceso por tiempo/geolocalización. Además, el punto único de fallo puede referirse a que la base de datos de SSO sea un activo deseable para cualquier atacante.
- **Sincronización de contraseñas.** Para que el mecanismo de SSO funcione correctamente, todo el sistema debe estar sincronizado para que cualquier cambio de contraseña se ejecute en todos los sistemas integrados.

La Figura 5.4 muestra los conceptos básicos de un sistema SSO en operación. La solicitud inicial de inicio de sesión del usuario es autenticada por el servidor SSO (mostrado como pasos 1 y 2). Cada intento del usuario para acceder a otro servidor, como uno que aloja un servicio web o una plataforma de aplicaciones, requiere un intercambio de autenticación en el backend entre el servidor SSO y el servidor de aplicaciones (pasos 3-6). Esta autenticación generalmente implica que el servidor SSO envíe información sobre la identidad autenticada del usuario, junto con una contraseña de aplicaciones actual de su base de datos interna, al servidor de aplicaciones. También se pueden usar tokens de acceso en lugar de contraseñas de aplicaciones; esto se basa en gran medida en lo que las aplicaciones y sus servidores necesitan para fines de autenticación y autorización. Se pueden utilizar una variedad de tecnologías como SAML para implementar SSO.
