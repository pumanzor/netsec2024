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
