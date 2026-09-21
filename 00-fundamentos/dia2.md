Día 2 — Ciclo DevOps / Pipeline CI/CD
CI: continues integration o integración continua
-esto explica el merch continuo de código dentro de la rama indicada, las veces que sea necesario en el dia, siempre ejecutar verificciones automatizadas y lo que sea necesario para descubrir puntos de vulnerabilidad en el código a implementar, independiente del tamaño

CD #1 continuous delivery o entrega continua
- significa de el código siempre estará en espera de paso a producción, estando testeado y empaquetado hasta que alguien diga "vamos", esto siempre estará a la espera del ser humano

CD #2 continuos deploy o despliegue continuo
- En este caso pasa directo a producción eliminando el proceso de espera, eliminando al humano, siempre si se tiene una base solida de los test y empaquetado realizado, en vez de esperar por ejemplo 2 semanas para desplegar y lanzar muchos cambios con una alta probabilidad de error


Cuando un equipo comienza se tiene
CI --> CD #1
Luego del tiempo y que ya el equipo tiene seguridad en lo realizado se pasa a 
CI --> CD #2 


pipeline: automatización que pasa el código de "lo que escribi" a lo que ven los usuarios
Los pasos siguientes son:
- commit: se puede entender como el disparador de salida del código a git o repositorio donde se guarda
- build: aquí es donde se compila, empaqueta e instala, o en cortas apalabras prepara el código, si falla en esta parte por algún error, no se continua los siguientes paso, es donde siempre se pueden encontrar los errores
-Test:  Se pueden aplicar 2 tipos de test
	unitarios: cubren funcionalidades individuales
	Integración: este verifica la comunicación entre componentes
Cabe mencionar que si falla en la primera etapa, el pipeline se detiene por completo
-Verificaciones de Calidad: En este paso, el equipo decide que se desea probar, puede ser todo tipo de pruebas o solo algunas especificas, esto se efectua cada vez que se realiza un despliegue, no cuando se acuerdan
- Despliegue a staging: En términos sencillos, es el despliegue en pre-producción, donde se realizan todas las pruebas funcionales antes de pasar a prod
- Despliegue a prod: Paso final, donde un humano lo aprueba (entrega continua) o sucede automáticamente (despliegue continuo)

Algunas herramientas a tener en cuenta:
- GithubActions, GitLab CI/CD, Jenkins, CircleCI

Anti-Patrones de pipelines 
- Sin test en el pipeline: el objetivo es atrapar los problemas antes de pasar a prod, si el pipeline no efectua test, no es un pipeline CI/CD, es IMPRUDENCIA AUTOMATIZADA
- test que tardan 45 minutos: si es pipeline es lento, la gente lo rodea pensando "seguro esta bien" y no estaba bien. optimiza tests lentos. Paraleliza. Ejecuta los rapidos primero para fallar temprano
- Despliegues el viernes por la tarde: no realizarlo si no tienes una estrategia de rollback solida
- Secrets en el repo: Usar la gestión de secrets de tu herramienta CI, todas la tienen
- Ignorar test inestables: NO ignorar los test que tienen una tasa de aprobación alta, arregla los test inestables inmediatamente o eliminalos, no vuelvas a ejecutar el pipeline hasta que pase en verde, eso le enseña a tu equipo a desconfiar de todo el sistema
- sin entorno de staging: no tener un ambiente previo, te deja una brecha alta a tener la respuesta del cliente de "el sistema esta caído", cuando este tipo de cosas se pueden prevenir


**Tarea:** Dibuja el ciclo y explica cada etapa con tus palabras.

-  commit --> Build --> Test --> Verificaciones de Calidad --> Despliegue a Stagging --> Despliegue a prod

- pipeline: flujo automatizado de pasos. Commit -> Compilar -> Ejecutar pruebas -> Analizar calidad -> Desplegar
- commit: Es el registro de un cambio realizado en el código dentro del sistema de control de versiones. Este cambio puede generar el inicio de un pipeline.
- build: Punto de inicio donde se compila y/o se empaqueta , si falla en este punto todo el próximo proceso no continua
- Test: Aquí se realizan todas las pruebas que se hallan ajustado en el momento en el pipeline
- Verificaciones de Calidad: En este punto se realizan las verificaciones definidas en el pipeline para comprobar que el código cumple con los criterios de  calidad establecidos, se realiza siempre
- Despliegue a stagging: Paso antes de prod y donde el usuario tester prueba lo necesario , con la finalidad de que lo que no se detecto anteriomente
- Despliegue a PROD: paso final, se puede aplicar entrega continua (humano aprueba) o Despliegue continuo (se pasa de forma directa)
