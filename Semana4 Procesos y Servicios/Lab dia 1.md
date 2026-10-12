Este laboratorio ayuda a entender los comandos de seguimiento de procesos corriendo en el equipo

1.- ps: consultar procesos
2.- top: observar los procesos de manera dinámica en tiempo real
3.- htop: permite de la misma manera que top, pero mas amigable, además de permitir aplicar filtros u otras cosas a los procesos
4.- foreground: procesos en primer plano, ejemplo ejecución en primer plano sleep 300
5.- background: procesos en segundo plano, ejemplo ejecución en segundo plano sleep 400 &

Identificación de campos de procesos

- PID: identificación del proceso
- USER: usuario owner
- PRI: prioridad del proceso
- NI: valor que influye en la prioridad del proceso, a tener en cuenta que el valor puede ir entre -20 a 19, mientras mas cercano a -20 mas prioritario
- VIRT: memoria virtual asignada al proceso
- RES: representa aproximadamente la cantidad de memoria del proceso que actualmente reside en la RAM fisica
- SHR: memoria que puede ser compartida con otros procesos
- S: estado (R: running, S: sleep, D: Espera no interrumpible, T: detenido, Z: zombie)
- CPU%: porcentaje de utilización de CPU
- MEM%: porcentaje de utilización de memoria
- TIME+: tiempo de ejecucion
- command: comando realizado

ejemplo ejecución:
- PID    USER      PRI  NI  VIRT   RES   SHR  S CPU% MEM% TIME+    command
- 23093  vboxuser   20  0  16112  7656  6432  T 0.0  0.2  0:00.00  sleep 300
