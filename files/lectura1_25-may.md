Intro

- Que es Seguridad? es dificil definirlo en una sola frase pero quizas podemos obtener distintos puntos de vista dentro de esta lectura y llegar a un consenso.
* Muchos sistemas están conectados a Internet entonces podemos pensar que vamos a tener algun tipo de adversario. Por lo tanto, es posible que el diseño de muchos sistemas se deba abordar la seguridad, es decir, ¿seguira funcionando el sistema cuando haya un adversario o me esten atacando?


ok pensemos en seguridad , eso implica una objetivo (asegurar activos p.ej) vs algun adversario-> el cual quiere acceder a nuestros archivos para eliminarlos, hacer que nada funcione, robarlos para luego solictar rescate y digamos que seguridad es detenerlo

en general pensar en seguridad es romperlo o dividirlo en 3 partes


* Politica: que es lo que esta permitido o no y vendria siendo la meta que queremos lograr, dar algunos ejemplos, solo esta permitido el puerto 443, solo algunos usuarios pueden acceder a ciertos archivos, no esta permitido el puerto 445, 139 por default cuando se crea una nueva maquina virtual, una politica tambien deberia permitir que los datos sean confidenciales (que ALM den los ej), integros (ej)  y que esten siempre disponibles (ej.)

-- Objetivos comunes de la política: confidencialidad, integridad, disponibilidad

PERO creo que esto no es suficiente si no sabemos que esta pensado el adversario o el bad guy , para ello debe pensar en

* Modelo de amenaza: suposiciones sobre lo que podría hacer el atacante.ej. pueden adivinar contraseñas, puede acceder sin autorizacion a mis archivos (desde adentro o desde Internet) ,que mas?

* Mecanismo: medios que su tu sistema proporciona para ayudar a mantener la política o cumplirla. p.ej. cuentas de usuario, contraseñas, permisos de archivos, cifrado. etc

* Objetivo resultante: no hay forma de que el adversario dentro del modelo de amenaza viole la política.


**Por qué la seguridad es difícil, es un objetivo negativo.**

1. Necesidad de garantizar la política, asumiendo el modelo de amenaza. 
2. Es difícil pensar en todas las formas posibles en las que un atacante podría entrar.
3. Los modelos de amenazas realistas son abiertos 
4. Contraste: es fácil comprobar si se cumple un objetivo positivo, Alicia puede acceder al archivo.
5. El eslabón más débil importa.
6. Proceso iterativo: diseño, actualización del modelo de amenazas según sea necesario, etc.


¿De qué sirve si no podemos lograr una seguridad perfecta?

Amplieemos los límites de cada sistema para ver cuándo falla.

1. Es probable que cada sistema tenga algún punto de ruptura que conduzca a un compromiso.
2. No significa necesariamente que el sistema no sea útil: depende del contexto.
3. Es importante comprender lo que un sistema puede hacer y lo que no puede hacer.

En realidad, se debe gestionar el riesgo de seguridad versus el beneficio.

* Sistemas más seguros significan menos riesgo (o consecuencia) de algunos compromisos.
* Un sistema inseguro puede requerir una auditoría manual para comprobar si hay ataques, etc.
* Un mayor coste del ataque significa que se disuadirá a más adversarios

Una mayor seguridad a menudo hace que las nuevas funciones sean prácticas y seguras. Supongamos que quieres ejecutar alguna aplicación en su sistema. Las grandes empresas a veces prohíben a los usuarios instalar software que no haya sido aprobado en materia de seguridad.

De manera similar, las VPN hacen que sea práctico mitigar el riesgo de permitir que los empleados se conecten a una red corporativa desde cualquier lugar de Internet.

Lo que sale mal 

**1. problemas con la política. Recuperacion de claves de un email**


- Gmail password reset: send a verification link to a backup email address.-
- Google helpfully prints part of the backup email address.
- Apple password reset: need billing address, last 4 digits of credit card.
- Address can be easy, but how to get 4 digits of user's credit card
- Amazon: can add a credit card to an account, no password required.
- Amazon: will not print credit card numbers. But will print last 4 digits!

¿Cómo resolver?
Piense detenidamente en las implicaciones de las declaraciones de políticas.
Algunas herramientas de verificación de políticas pueden ayudar, pero necesitan una manera de especificar qué es lo malo.

**2. Qué sale mal : problemas con el modelo/suposiciones de amenazas**

- Ejemplo: factores humanos no contabilizados, ej.
- El usuario recibe un correo electrónico solicitando renovar su cuenta de correo electrónico, transferir dinero o...
- Ataques de phishing.El soporte técnico recibe una llamada de alguien convincente.

Ejemplo: suponiendo que su hardware sea confiable.
* Si la NSA es su adversario, resulta que no es una buena suposición.
* Los adversarios pueden conectarse a una red inalámbrica insegura detrás del firewall


Cada CISO sueña con la computadora invulnerable. Un método común para hacer a prueba de balas un sistema es desconectarlo del mundo exterior. Sin Internet. Sin inalámbricos. Sin módem. Luego rodeas la computadora con guardias y puertas. Esto se llama sistema con aislamiento de aire y se supone que es a prueba de hackeos.

En realidad, no lo es.

https://www.f5.com/labs/articles/cisotociso/attacking-air-gap-segregated-computers

En 2010, se descubrió que el malware Stuxnet había saltado un aislamiento de aire y comprometió casi una quinta parte de las centrífugas nucleares de Irán, causando retrasos significativos. El malware Stuxnet fue posteriormente atribuido a los Estados Unidos e Israel trabajando juntos para debilitar el programa nuclear iraní. De hecho, hackear sistemas con aislamiento de aire es el ámbito del atacante avanzado.

Si bien los sistemas con aislamiento de aire se utilizan en agencias militares seguras e industrias relacionadas, también se pueden encontrar en otros lugares. Cualquier sistema crítico que no pueda ser contaminado o espiado a menudo está aislado de aire. Esto incluye equipos médicos que sostienen la vida, almacenes críticos de propiedad intelectual altamente valiosa y los sistemas de Control y Adquisición de Datos Supervisorios (SCADA) que controlan los sistemas de agua y energía. Las criptomonedas como Bitcoin y Ethereum también utilizan sistemas de almacenamiento aislados de aire llamados billeteras frías para almacenar de forma segura la clave privada que puede desbloquear la moneda.

Penetrando una brecha de aire

Entonces, ¿cómo logra un atacante entrar en una computadora sin conexiones con el mundo exterior? Una forma es hacer lo que los atacantes solían hacer en los viejos tiempos: poner el malware en un disquete. Pasé una buena parte de mi carrera temprana limpiando el virus Stoned de los sistemas del laboratorio informático del campus. Ya no tenemos unidades de disquete, gracias a Dios. Sin embargo, tenemos el equivalente moderno: la unidad de memoria USB. Stuxnet utilizó malware entregado por USB para llevar su carga útil a las centrífugas con aislamiento de aire. Esta técnica parece ser un truco común en el repertorio de la CIA para atacar sistemas con aislamiento de aire. El Proyecto Sauron, otro malware avanzado, se esconde en una unidad USB para llegar a objetivos con aislamiento de aire.

Otra forma de comprometer un sistema con aislamiento de aire es "pre-penetrarlo" antes de que termine en la brecha de aire sabotear su cadena de suministro. No es inusual que un atacante avanzado estudie a su víctima y determine su infraestructura técnica. Luego, el atacante puede ir tras los objetivos más fáciles: los proveedores, para ocultar trampas en el hardware o software. Hay varios casos conocidos de atacantes que esconden malware o puertas traseras secretas en bibliotecas de software que luego se incorporan a aplicaciones de producción. También hemos visto a atacantes avanzados dirigirse a grandes proveedores de servicios para llegar a sus clientes. Incluso los proveedores de antivirus no son inmunes a ser cooptados para ser utilizados en ataques contra los sistemas de sus clientes. Algunas de las sorpresas más desagradables pueden provenir de un atacante que coloca malware en el firmware de la computadora misma y permanece oculto hasta que llegue el momento adecuado.

Si los atacantes no pueden engañar a un técnico o usuario para que lleve una unidad USB infectada, siempre pueden recurrir a sobornar o coaccionar a un insider para que lo haga.

Exfiltración desde la brecha de aire

Suponiendo que la misión no sea destrucción (Stuxnet) o ransomware, entonces el verdadero truco es sacar los datos robados. Si el atacante usó una memoria USB para introducir el malware, puede usar el mismo método para sacarlo. La infame filtradora Chelsea Manning transportó físicamente gigabytes de archivos de video secretos en un CD fuera de una Instalación de Información Compartmentada Sensible (SCIF), la versión militar de un sistema con aislamiento de aire.

Un atacante no siempre puede contar con un insider o alguien más para llevar inconscientemente un USB con los datos fuera de una instalación. Pero hay muchas formas de enviar información a distancia. Cualquiera que haya estudiado formalmente ciencias de la computación probablemente haya oído hablar de la teoría de la información. La teoría de la información postula que cualquier cosa que puedas hacer variar se puede utilizar para transmitir información. Esto se llama "La diferencia que marca la diferencia". Si ambos lados de una conversación pueden interpretar el mensaje, muchas cosas pueden usarse como un medio de transmisión, desde puntos y rayas por radio hasta golpes contra una pared.

Sabemos que el malware controla la computadora con aislamiento de aire, por lo que puede codificar señales de la manera que el atacante elija. Luego, el atacante puede colocar un dispositivo receptor para hacer contacto a través de un canal que pueda propagarse a través de la brecha de aire. Aquí está el verdadero giro: ese dispositivo receptor puede ser nada más que un teléfono inteligente común que ejecute el software decodificador del atacante. Esto deja muchas posibilidades para la exfiltración.

El más simple es el que usamos los humanos: el sonido. Los altavoces de la computadora pueden producir fácilmente sonido a niveles inaudibles para el oído humano (18-24hz) que pueden ser decodificados por un teléfono celular hasta a 25 pies de distancia. ¿Sin altavoces en la computadora con aislamiento de aire? Los micrófonos también pueden funcionar como altavoces. ¿Sin altavoces ni micrófonos? El brazo actuador del disco duro puede ser golpeado para enviar señales de audio. ¿Discos de estado sólido sin partes móviles? Entonces los ventiladores de la computadora también producen ruido y pueden ser alterados por el malware para transmitir información.

Obviamente, una computadora con aislamiento de aire no tendrá una red Wi-Fi funcional, pero hay otras formas de generar una señal de radio. De hecho, las primeras computadoras personales eran conocidas por generar emisiones de radio superfluas debido a sus componentes eléctricos mal blindados. Los procesadores o incluso un cable USB largo pueden convertirse en un transmisor de radio que puede enviar señales en frecuencias

Los procesadores o incluso un cable USB largo pueden convertirse en un transmisor de radio que puede enviar señales en frecuencias de radio FM o de teléfono celular que incluso pueden penetrar el blindaje de radio Faraday.

El enchufe eléctrico al que está conectada la computadora también puede usarse como un canal encubierto. La técnica de enviar señales a través de líneas eléctricas fue en realidad un método común de automatización del hogar durante décadas. Incluso los paquetes de red normales pueden pasar por líneas eléctricas. En algún lugar de mi sótano, tengo un par de módems Ethernet sobre línea eléctrica (EOP/Powerline) que se utilizaron en la era anterior al Wi-Fi para redes domésticas.

Muchas de estas técnicas de exfiltración han sido demostradas en laboratorio por Mordechai Guri, un investigador académico especializado en exfiltración de sistemas con aislamiento de aire. Si estás interesado en cómo se puede filtrar información de sistemas con aislamiento de aire, mantén un ojo en su página de investigación sobre Aislamiento de Aire en la Universidad Ben-Gurion del Negev, en Israel.

Defendiendo la Brecha de Aire

¿Cómo lidiar con este problema? Ser consciente de las amenazas específicas y cómo funcionan es el primer paso. Los defensores deben ser conscientes de que los teléfonos inteligentes ordinarios pueden convertirse en herramientas de espionaje. Prohibir los móviles en cualquier lugar cercano a los sistemas con aislamiento de aire parece ser una política prudente. Considera también la multitud de "dispositivos inteligentes" que podrían ser comprometidos y convertidos en receptores de canales encubiertos.

Protegerse contra los vectores de ataque conocidos también es una buena idea. Si es necesario usar unidades de memoria USB, deben ser escrutadas muy minuciosamente primero. También es una buena idea auditar la cadena de suministro. Siempre existirá la posibilidad de insiders maliciosos, por lo que es importante registrar y revisar sus acciones, buscando comportamientos sospechosos.

Finalmente, los defensores siempre deben recordar el principio de asumir la brecha. Los atacantes avanzados que apuntan a sistemas con aislamiento de aire pueden tener capacidades superiores, por lo que es prudente esperar que en algún momento logren ingresar. Suponiendo que lo lograron, ¿cómo puedes diseñar tus sistemas y tus procesos de respuesta? Es mejor esperar lo peor que lidiar con una sorpresa desagradable.

Ten en cuenta que muchas de estas técnicas defensivas son útiles ya sea que uses sistemas con aislamiento de aire o no. Son todas buenas ideas para cualquier organización que busque defenderse contra ciberataques.

## como lo resolvemos?

* Un modelo de amenazas más explícito para comprender las debilidades.

## 3. que fue mal con el mecanismo:
