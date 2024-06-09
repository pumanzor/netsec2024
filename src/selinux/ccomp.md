**Componentes Principales de SELinux**

Componentes principales de SELinux que gestionan la aplicación de la política y se componen de lo siguiente:
- Un **Sujeto** que debe estar presente para que se realice una acción sobre un Objeto (como leer un archivo, ya que la información solo fluye cuando un sujeto está involucrado).
- Un **Administrador de Objetos** que conoce las acciones requeridas para el recurso particular (como un archivo) y puede hacer cumplir esas acciones (es decir, permitir escribir en un archivo si lo permite la política).
- Un **Servidor de Seguridad** que toma decisiones sobre los derechos del sujeto para realizar la acción solicitada sobre el objeto, basándose en las reglas de la política de seguridad.
- Una **Política de Seguridad** que describe las reglas utilizando el Lenguaje de Políticas del Kernel de SELinux.
- Un **Cache de Vectores de Acceso (AVC)** que mejora el rendimiento del sistema al almacenar en caché las decisiones del servidor de seguridad.
