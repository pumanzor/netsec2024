Las organizaciones clasifican y categorizan la información en función de su valor para sus actividades en curso, y si alguna de sus características de seguridad se ve comprometida, determinan cómo ese 
valor puede verse afectado. A medida que las necesidades de seguridad de la información se alinean con las prioridades organizacionales, esto informa decisiones críticas sobre los controles de seguridad, 
que pueden ser de naturaleza administrativa, técnica u operativa. Sin embargo, todos estos controles dependen de decisiones sobre la necesidad de saber: quién, dentro y fuera de la organización, debe poseer
el conocimiento sobre lo que contiene un conjunto de datos en particular y, por extensión, quién requiere la capacidad de crear, modificar, mover, copiar o cambiar de otra manera la ubicación, estado o
características de ese conjunto de datos.

Esto lleva a la siguiente tarea importante que enfrentan los profesionales de seguridad de la organización: crear y gestionar los procesos de gestión de identidades y accesos (IAM) que la organización 
necesita. Dichos sistemas IAM deben acomodar tanto a usuarios humanos como no humanos, como software, hardware, dispositivos de Internet de las Cosas (IoT) y una creciente variedad de robots.

Existe cierta confusión en el mercado sobre qué terminología usar para este tema: gestión de identidades (IdM) o IAM. Algunas fuentes, como Gartner Research, han intentado definir IdM como enfocado en 
el proceso de emisión y gestión de identidades para controlar su acceso a los recursos del sistema, y reservar IAM para el problema más grande de cuestiones de identidad y acceso en sistemas en la nube y 
sistemas federados. IAM se usará a lo largo de este dominio y curso. Los sistemas IAM consisten en procesos que crean y gestionan identidades, asocian privilegios con identidades y luego usan esa 
información para asegurar que ninguna identidad desconocida o no reconocida (humana o no humana) pueda acceder a los recursos del sistema o realizar cualquier operación sobre ellos. Los sistemas IAM 
también deben realizar un seguimiento de todo lo relacionado con el ciclo de vida de una identidad y de sus intentos de acceder a los recursos. Esta "triple A" de autenticación, autorización y contabilidad 
(AAA), y las funciones centrales de gestión de identidades en el corazón de esto, han sido reconocidas durante mucho tiempo como la piedra angular de la seguridad, y se conoce por el acrónimo IAAA. 
Sin esto, ninguno de los controles de seguridad sabría qué actividades permitir y cuáles prevenir.

Control de Acceso Físico y Lógico a Activos (5.1)
Objetivos

    Explicar las necesidades y los procesos para el acceso físico y lógico a los activos.

Resumen

Proveer un control positivo de los intentos de acceso (visualizar, modificar o mover) a los activos de una organización requiere un conjunto consistente y cohesivo de controles administrativos, físicos y lógicos (o técnicos). Por supuesto, todos los sistemas de control de acceso (AC) están impulsados por información: el inventario de activos de información, las políticas de clasificación y categorización, y los resultados de las decisiones tomadas a lo largo del ciclo de vida del sistema de identidad y AC y los sistemas de información que ayuda a proteger.

La selección y uso de esos controles mencionados deben estar guiados por consideraciones de diseño basadas en los modelos de seguridad y modelos de AC empleados. Los controles administrativos, que dirigen las acciones de las personas, están basados en un contexto organizacional más amplio.

Como sus nombres sugieren, los controles físicos restringen o guían los movimientos y acciones de los usuarios; los controles lógicos permiten, restringen, guían o de otra manera influyen en el flujo de información a través del sistema. Algunos de esos flujos de información pueden haber sido desencadenados por acciones físicas de un usuario, como una pulsación de tecla, un clic de ratón o moverse dentro del rango de captura de un detector de movimiento u otro sensor. Otros flujos de información resultaron de las acciones de elementos de software, que presumiblemente fueron activados por un usuario.

Con el rápido crecimiento en el uso de robots semiautónomos y autopropulsados, es importante tener en cuenta que los usuarios en este contexto deben incluir tanto a humanos como no humanos. Veamos más de cerca el control de acceso físico y lógico en acción, como parte de un programa de seguridad de activos de información.

**Control de Acceso: Lo Básico**

Una variedad de definiciones de control de acceso se utilizan en toda la comunidad de seguridad de la información a nivel mundial. Un punto de partida útil se encuentra en la norma ISO/IEC 27000:2016(E), que define el control de acceso como un “medio para asegurar que el acceso a los activos esté autorizado y restringido según los requisitos comerciales y de seguridad”. Para obtener información adicional, consulte ISO/IEC 27000:2016(E) y otros documentos de la serie ISO/IEC 27000. El NIST define el control de acceso de diversas maneras; algunas (como NIST SP 800-79-2) se enfocan más claramente en otorgar o denegar solicitudes para obtener o usar información u otros activos, mientras que otros controles (como NIST SP 800-192) se enfocan más en los medios para hacerlo. La declaración de propósito de la ISO proporciona un punto de partida para que las organizaciones lo usen mientras desarrollan, implementan, gestionan y evalúan el rendimiento de tales sistemas como parte de sus programas de seguridad de la información.

Como nombre, el control de acceso deja algunas palabras clave implícitas en lugar de explícitas. Más explícitamente, el control de acceso podría llamarse control del acceso de sujetos a objetos en un sistema. Esto se ilustra en la Figura 5.1, que proporciona una visión general y una introducción a los temas básicos del control de acceso. Pongámonos en el papel de los defensores de los sistemas y activos de la organización mientras nos adentramos en la terminología.

- **Objetos** son los activos de información o los recursos del sistema que son los bloques de construcción de los sistemas que debemos proteger. Pueden ser archivos, registros o campos dentro de una base de datos. Los recursos de hardware como áreas de memoria, tiempo de CPU, espacio en disco o dispositivos de interfaz de red también son objetos, en términos de AC. Las áreas físicas de un edificio, documentos impresos e incluso los canales Wi-Fi proporcionados por los puntos de acceso inalámbrico de la organización pueden considerarse como objetos que necesitan protección. Los objetos también pueden ser otros sujetos.
- **Sujetos** son cualquier persona, proceso, dispositivo u otra entidad que quiera acceder a cualquiera de los objetos en el sistema.
- **Acceso** se puede pensar en términos de base de datos, como operaciones de crear, leer, actualizar o eliminar (CRUD), o los diversos pasos en el modelo de ciclo de vida de seguridad de datos descrito en el Dominio 2, que agrega compartir, archivar y almacenar como acciones explícitas.

Observe en esta figura que uno de los sujetos (presumiblemente un humano) está utilizando una computadora (que puede o no ser su propio activo) como intermediario para acceder a una base de datos en un servidor perteneciente a la organización. Esto destaca la complejidad de conocer al sujeto solicitante final.

