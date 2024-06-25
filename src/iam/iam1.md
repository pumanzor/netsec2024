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

- El usuario ejecuta una aplicación en su dispositivo, a la cual su sistema operativo (SO) anfitrión le asigna un conjunto de identificaciones de proceso (IDs).

- Uno de esos IDs de proceso, para un hilo particular, realiza llamadas al sistema para solicitar una conexión a la base de datos remota en el servidor; esto involucra a otros IDs de proceso que realizan estos servicios en nombre del proceso solicitante.

- El servidor recibe esa solicitud de conexión remota y las solicitudes de acceso a datos subsiguientes.

Para mantener la seguridad de los datos en el servidor, ese sistema de gestión de bases de datos necesita recibir un conjunto de credenciales que esencialmente digan: “El usuario con ID X, que ha sido reconocido y aprobado para acceder en su propio sistema, está solicitando acceso a estos registros y campos de datos, para que pueda realizar estas acciones CRUD. ¿Puedes aprobar?”





**Opciones de Administración de IAM**

La información y la administración de la información son clave para la gestión de los sistemas de control de acceso (AC) de una organización. La información puede asociarse con sistemas de AC tanto lógicos como físicos. Ya sea un sistema de acceso lógico o físico, el control de ese sistema se mantiene en algún lugar como datos discretos o información, o ambos. La gestión de la información relacionada con el acceso físico y lógico se lleva a cabo de tres maneras principales: centralizada, descentralizada e híbrida.

**Centralizada.** La administración centralizada significa que una función es responsable de configurar los ACs para que los usuarios puedan acceder a los datos y realizar actividades relevantes. A medida que cambian las necesidades de procesamiento de información de los usuarios, su acceso solo puede modificarse a través de la administración central, generalmente después de que las solicitudes hayan sido aprobadas mediante un procedimiento establecido y por la autoridad correspondiente. Una ventaja de la administración centralizada es que se mantiene un control estricto sobre la información porque la capacidad de realizar cambios reside en unas pocas personas. La cuenta de cada usuario puede ser monitoreada centralmente, y cerrar el acceso de todos los usuarios puede lograrse fácilmente si ese individuo deja la organización. Los procedimientos y criterios consistentes y uniformes generalmente no son difíciles de hacer cumplir, ya que relativamente pocas personas supervisan el proceso.

Las implementaciones de AC centralizado requieren que todas las acciones de autenticación y autorización sean manejadas por el sistema de AC central. Desde una perspectiva, esto es una ventaja, ya que las actualizaciones de identidades y privilegios están disponibles inmediatamente para su uso en todos los nodos dentro de las redes de la organización. Esto también puede imponer demandas de rendimiento sustanciales en ese sistema de AC.

**Descentralizada.** En contraste con la administración centralizada, la administración descentralizada o distribuida significa que el acceso a la información es controlado por los propietarios o creadores de los archivos, sean quienes sean o estén donde estén esos individuos. Una ventaja de la administración descentralizada es que el control está en manos de las personas más responsables de la información, más familiarizadas con ella y mejor capaces de juzgar quién debería poder hacer qué en relación con ella. Una desventaja, sin embargo, es que puede no haber consistencia entre los creadores/propietarios sobre los procedimientos y criterios para otorgar acceso y capacidades a los usuarios. Otra desventaja es que cuando las solicitudes no se procesan centralmente, puede ser más difícil formar una vista general del acceso de todos los usuarios en el sistema en un momento dado. Diferentes propietarios de datos pueden implementar inadvertidamente combinaciones de acceso que introducen conflictos de intereses o no están en el mejor interés de la organización. También puede ser difícil asegurar que el acceso se termine correctamente cuando un empleado se transfiere dentro o deja una organización.

Los sistemas de AC descentralizados o distribuidos pueden proporcionar mayores niveles de tolerancia a fallos, especialmente para arquitecturas empresariales grandes y dispersas geográficamente. También pueden proporcionar mejores tiempos de respuesta en comparación con los sistemas centralizados, ya que tienden a estar sirviendo a un número mucho menor de sistemas clientes (es decir, cualquier sistema que solicite una acción de autenticación o autorización). También puede tomar bastante tiempo, tal vez hasta 24 a 48 horas, para actualizar las bases de datos de AC en todos los servidores del sistema. Esta latencia puede permitir una ventana de oportunidad para que un atacante intente usar privilegios que la administración ha decidido revocar, pero que no todos los nodos en el sistema de AC han llevado a cabo.

**Híbrida.** En un enfoque híbrido, se ejerce control centralizado para cierta información y se permite control descentralizado para otra información. Una disposición típica es que la administración central sea responsable del acceso más amplio y básico, y los creadores/propietarios de archivos controlen los tipos de acceso o las habilidades de los usuarios para los archivos bajo su control. Por ejemplo, cuando se contrata a un nuevo empleado en un departamento, un administrador central podría proporcionar al empleado permisos de acceso basados en el elemento funcional al que están asignados, la clasificación del trabajo y la tarea específica para la que fueron contratados. El empleado podría tener acceso solo de lectura a una biblioteca de documentos de SharePoint de toda la organización y a archivos de informes de estado del proyecto, pero el mismo empleado podría tener privilegios de lectura y escritura en el informe semanal de actividades de su departamento. Además, si el empleado deja un proyecto, el gerente del proyecto puede cerrar fácilmente el acceso de ese empleado a ese archivo.

