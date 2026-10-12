En este laboratorio se detallara los procesos y las interacciones que se mantuvieron para poder trabajar con los procesos generados

Entorno
- Sistema operativo: Ubuntu Linux en VirtualBox.
- Herramientas: terminal, sleep, htop y kill.
- Proceso de prueba: sleep 600.

1. Iniciar un proceso en segundo plano
    Sleep 600 &
    Resultado: Terminal entrega el PID 30224
2. Identificar el proceso con htop
    htop
    utilizar el buscador de htop , buscar el proceso filtrando por PID o buscarlo directamente por comando 
    Se identifica el proceso donde se puede observar que se encuentra en estado S
3. Pausar el proceso
    kill -SIGSTOP 30224
    Resultado: Terminal mostrara por pantalla el mensaje stopped 30224
4.   Reanudar el proceso
    kill -SIGCONT 30224
    Resultado: Se retoma proceso que se encuentraba detenido
5.  Finalizar el proceso
    kill -SIGKILL 30224
    Resultado: Se detiene completamente el proceso
6.   Verificar que el proceso no se encuentre ejecutando
    ps -p 30224
    Resultado: Terminal entrega la cabezera del listado que muestra, pero sin ningun proceso con ese PID corriendo, lista vacia



Conclusión

En este laboratorio aprendí a gestionar un proceso de Linux utilizando señales. Inicié el proceso sleep en segundo plano, 
identifiqué su PID mediante htop, lo pausé con SIGSTOP, reanudé su ejecución con SIGCONT y finalmente lo terminé con SIGKILL.

Comprendí que kill es el comando utilizado para enviar señales a un proceso y que cada señal tiene un propósito diferente. También verifiqué que el proceso hubiera finalizado correctamente.
