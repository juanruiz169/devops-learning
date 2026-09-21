Se Adjuntan las preguntas sin correccion


📝 Evaluación Semana 1 — Fundamentos de DevOps
Parte 1 — Conceptos fundamentales

1. ¿Qué significa DevOps y qué relación existe entre "Dev" y "Ops"?

Actualmente devops mas que un equipo de trabajo se tomaría como una cultura que se desea implementar con los equipos, con una metodología de trabajo ágil con la finalidad que se pueda realizar un trabajo mas centrado en el desarrollo y entregas mas cortas al clientes  como se trabajaba con el cliente anteriormente

Dev se refiere al equipo de desarrollo y OPs al equipo de Operaciones, con que finalidad se relacionarían, es aquí donde nace el equipo Devops, que la finalidad de la creación de estos mismos como cultura, es que el mismo equipo que se relaciona con el cliente, pueda tener y generar las soluciones de primera mano y con los entregables directo con los mismos

2. ¿Qué problema principal intenta resolver DevOps dentro del ciclo de desarrollo de software?

Devops intenta resolver la problemática en la forma que se realizan los trabajos entre los equipos de desarrollo y operaciones, ya que como se indica, uno solamente se encarga del código sin tener contacto con el cliente y el equipo de operaciones se encarga de las conversaciones del mismo
Que busca devops, busca que estos equipos se integren y se trabaje tanto de forma directa, con la finalidad de una claridad y entrega mas confiable, con plazos mas acotados y sin lapsos de espera tan altos.

3. Menciona al menos 4 características o prácticas que forman parte de DevOps.
R: -----

4. ¿DevOps es una herramienta, un software o un lenguaje de programación? Explica tu respuesta
Devops no es ninguna de las indicadas anteriormente, es una cultura que se esta intentado implementar en los equipos, con la finalidad que no existan 2 equipos o mas en separación con la programación y el trato con el cliente, se desea tener una forma directa y concreta de la metodología de trabajo que se desea implementar

5. ¿Qué relación existe entre Agile y DevOps?
Agile refiere a una metodología que se efectua con la finalidad de realizar un ciclo de entrega mas ciclico con respecto al trabajo, cabe mencionar dentro de la metodología agile, existen muchos equipos involucrados en la toma de deciciones y donde esto pueda generar demoras, con la finalidad en Devops, se busca que los 2 equipos principales DEV y OPS, se encuentren unidos y se pueda trabajar de forma mas directa con los requerimientos del cliente y también en la forma de implementación y mejora en el ciclo de vida del codigo

Parte 2 — Pipeline y CI/CD

6. ¿Qué es un pipeline y cuál es su objetivo principal?
El pipeline es una implementación que se realiza para realizar el despligue del código que se esta pasando de un ambiente a otro, efectuando revisiones del mismo, con el objetivo principal de verificar vulnerabilidades en el mismo, pruebas de calidad, entre otras

7. Explica con tus palabras la diferencia entre un commit y un pipeline
LA diferencia aplica que al realizar un commit, el código se empaqueta y se deja preparado para realizar el despligue , y el pipeline es el encargado de realizar las verificaciones correspondientes y el despligue del mismo

8. Ordena correctamente las siguientes etapas:

Staging -
Test
Commit -
PROD -
Build
Verificaciones de Calidad
Pipeline - 

Y explica brevemente por qué las ordenaste de esa manera.

Commit -> Pipeline -> Build -> Verificaciones de calidad -> Test-> Staging -> Prod

Se realiza el commit donde se empaqueta o se guarda el código en el repo, se da build para comenzar con el proceso de las verificaciones correspondientes en el pipeline e identificar si existe algún problema, se carga en ambiente Staging donde se realizaran las ultimas verificaciones, este paso es necesario ya que puede ser que algo que no verifique el pipeline, no significa que esta siempre bien, puede que las verificaciones del pipeline esten malas y se deben revisar, y luego de verificar que todo se encuentra correcto, se realiza el despligue en el ultimo ambiente donde aquí verificara el usuario final o cliente.

9. ¿Qué ocurre normalmente si el Build falla dentro de un pipeline?
Se detiene todo el proceso y no continua, no realiza las verificaciones y no se despliga en ambiente staging

10. ¿Cuál es la diferencia entre Test y Verificaciones de Calidad?
En el test se realizan todo tipo de pruebas entre estas las pruebas unitarias, y entre muchas otras, y las pruebas de calidad según lo que se pueda definir puede ser que cumpla con el objetivo de la lógica esperada en el código 

11. ¿Qué objetivo tiene el ambiente de Staging antes de llegar a Producción?
La finalidad de ambiente Staging es mas bien conocido como ambiente pre productivo, donde se pueden realizar las pruebas correspondientes de lo que se desea desplegar antes que llegue al usuario o cliente final en ambiente productivo

12. Explica con tus palabras la diferencia entre Continuous Delivery y Continuous Deployment.
Continuos Delivery o como en español se conoce como Entrega continua significa que con este tipo de CD, se espera siempre las aprobaciones correspondientes y validaciones necesarias antes de realizar los despligues en ambientes productivos, y Continuous Deployment o Despliegue continuo, es no pasar por el paso que se realiza en Entrega Continua y realizar los despliegues de forma directa en ambiente prod, Cabe mencionar que esto se realiza, siempre y cuando uno tenga la confianza necesaria en que lo que se esta implementando no se encuentra con fallas y no va a generar ningún problema

Parte 3 — Herramientas y categorías

13. Clasifica las siguientes tecnologías en su categoría correspondiente:

Git -
Docker -
Python -
AWS -
Jenkins
Prometheus -
Ubuntu -
AWS Lambda
DNS
GitHub Actions -

Categorías disponibles:

Lenguaje de programación: Python
Sistema operativo: Ubuntu
Control de versiones: Git
Contenedores: Docker
Networking: DNS
Cloud: AWS
Serverless: AWS Lambda
CI/CD: GitHub Actions, Jenkins
Monitoreo: Prometheus

14. ¿Cuál es la diferencia entre una herramienta de CI/CD como Jenkins o GitHub Actions y un proveedor Cloud como AWS o GCP?
R:

15. De todos los conceptos estudiados durante esta semana, elige uno que al principio no entendías y explica con tus propias palabras qué entiendes ahora de él.
R: Herramientas y Categorías seria la sección que aun no me encuentro capacitado, independiente que se me allá emplicado a grandes rasgos sus categorias
