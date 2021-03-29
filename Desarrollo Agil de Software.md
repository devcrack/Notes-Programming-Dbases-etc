# Desarrollo Agil de Software

Muchas empresas estan dispuestas a negociar la calidad del software y el compromiso con los requerimientos, para lograr con na mayor celeridad la implementacion del software.

En las startups y empresas con modelos de negocios con requerimientos cambiantes es posible que sea solo hasta que el sistema este terminado y los usuarios adquieran experiencia usandolo sea hasta entonces que los requerimientos se aclaren.


**Los procesos de software que buscan especificar por completo los requerimientos y, luego diseñar, construir y probar el sistema, no estan orientados al desarrollo agil de software**.


A medidad que los requerimientos cambian, o se descubren problemas en los requerimientos, el diseño o la implementacion del sistema tienen que reelaborarser y probarse de nuevo.

Los procesos de desarrollo de software rapido se deiseñan para producir rapidamente software util. En ese sentido el software se desarrolla como una serie de incrementos y cada incremento incluye una nueva funcionalidad del sistema. 

**Caracteristicas fundamentales del desarrollo agil de software**

1. Los procesos de especificacion, diseño e implementacion estan entrelazados casi que se desarrollan de manera simultanea. En este tipo de desarrollo no exist e una especificacion detallada y la documentacion del diseño se minimiza o tiene que ser generada por una herramienta de software como el entorno de programacion o algun 3rtd party software. 
El documento de requerimientos del usuario define solo las caracteristicas mas importantes del sistema.

2. El sistema se desarrolla en diferentes versiones. Los usuarios y los desarrolladores del sistema intervienen en la especificacion y evaluacion de cada deploy. Se podran proponer nuevos cambios y requerimientos nuevos para una version posterior del sistema.

Los metodos agiles de desarrollo de software son incrementales y se tiene que liberar nuevas caracteristicas y funcionalidades cada 2 o 3 semanas que se ponene a disposicion de los clientes. Se busca involucrar al cliente en el desarrollo, se minimiza la documentacion y se busca invertir menos tiempo en el diseño del sistema que en su desarrollo .

Sin embargo el desarrollo agil tiene ciertas consecuencias indeseables ya que este tipo de desarrollo se centra mas en las personas que en los procesos el conocimiento implicito del sistema recae en las personas ue que comprenden los aspectos del sistema sin que deban de consultar algun tipo de docuemtnacion. Si se separa el equipo ser pierde el conocimiento de este sistema y es dificil que los nuevos miembros del equipo acumulen la misma percepcion del sistema y sus componentes.

La solucion es desde luego optar por un enfoque hibrido donde el metodo agil incorpore tecnicas del desarrollo dirigido por un plan.

**Programacion Extrema**

En la programacion extrema,los requeriemientos se expresan como escenarios(Llamados **historias de usuario**) que se implementan directamente como una serie de tareas. Los programadores trabajan en pares usualmente y desarrollan pruebas para cada tarea antes de  escribir el codigo. Todas las pruebas deben de ejecutarse con exito una vez que el codigo nuevo se integre al sistema. 

Principos de la programacion extrema:

1. El desarrollo incremental se apoya en las pequeñas y frecuentes liberaciones del sistema. Los requerimientos se fundamentan en simples historias del cliente o bien en historias de usuario para decidirse que funcionalidad debe incluirse en el sistema.

2. El cliente siempre forma parte del desarrollo del sistema. Es el responsable de definir los criterios de aceptacion del sistema.

3. El desarrollo se basa en las personas  en la propiedad colectiva del codigo del sistema. 

4. El cambio se acepta  mediante liberaciones continuas del del sistema para los clientes, el desarrollo siempre tiene que incluir pruebas escritas y la refactorizacion continua para la evitar la degeneracion del codigo.

5. Mantener la simplicidad se logra mediante la refactorizacion constantte, que mejora la calidad del codigo y con el uso de diseños simples que no anticipan innecesariamente futuros cambios al sistema. Si se tiene que cambiar en el futuro se creara una nueva historia de usuario y se evaluara.


Las tarjetas de historia o las historias de usuario juegan un papel fundamental en la Prgramacion Extrema ya que esta encapsula todas las necesidades del cliente, entonces el equipo de desarrollo implementa dicha necesidad o escenario en una liberacion futura del software.

![Historia Usuario](./resources/ejemp_historia_usuario.png "Historia de Usuario")