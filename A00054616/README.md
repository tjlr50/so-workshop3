Taller 3

Estudiante: Tomas Lemus
Codigo: A00054616
Github: tjlr50


Actividades

1.Empleando el aplicativo strace obtenga 5 llamadas al sistema para uno o varios comandos de linux. Explique por qué los comandos seleccionados emplean las llamadas al sistema encontradas, para ello debe emplear los manuales de Linux en Internet o del sistema operativo (comando man). Debe incluir la explicación de los parámetros que reciben las llamadas al sistema encontradas. Consigne capturas de pantalla donde muestre las llamadas al sistema obtenidas (sugerencia: emplear -etrace para filtrar los resultados)

-strace pwd, indica la ruta en la que estoy ubicado, para saber en que parte de la estructura de directorios se realizarán cambios o accesos.

  munmap(2) ubica o elimina ficheros o dispositivos en memoria.
    1. legth: indica la longitud de dicho archivo
    2. strart: indicica el lugar donde se debe comenzar a ejecutar la acción 

  brk(1) Indica el final del segmento de datos, retorna 0 en caso de éxito
  
    1. end_data_segment: indica en donde es el final del segmento, si es razonable el parametro
    
  close(1) cierra  un descriptor de fichero de forma que ya no se refiera a fichero alguno y pueda ser reutilizado. Retorna 0 para écito, -1 para error.
    1. fd: es la última copia del descriptor de fichero, los recursos
       asociados con dicho descriptor son liberados; si el descriptor fuera la
       última  referencia  a  un  fichero  que  haya  sido  eliminada mediante
       unlink(2) entonces el fichero es borrado.
       
  fstat(2) obtiene informacion sobre el archivo abierto 
    1. fd: descriptor del cual abstrae info.
    2. struct stat: informa al systema el id del archivo, número inodo, numero del hard links del archivo.
  
  write(3) escribe  bytes  en  el  fichero  referenciado.
    1.num: hasta cuanto escribir.
    2 fd: descriptor de fichero 
    3. buf: desde el búfer en que  comienza.
 
 
2.Realice la compilación del código fuente adjunto y su ejecución empleando el aplicativo strace. Identifique las llamadas al sistema encargadas de enviar y recibir datos a través de la red. A partir de los manuales de Linux en Internet o del sistema operativo explique las llamadas al sistema encontradas y sus parámetros.
Las llamadas al sistema identificafas son: Las que envian datos a un socket (sendto), este puede ser utilizado aún si el estado del socket es diferente a connect. Otra función, para leer un mensaje por un socket upd es (recvfrom), al ejecutarla se quedará bloqueada hasta que llegue un mensaje. Para ambos, nos devolverá el número de bytes leidos o -1 si ha habido algún error.
