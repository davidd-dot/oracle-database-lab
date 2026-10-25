# Laboratorio 3 — Preguntas de comprobación

## 1. Docker

1. ¿Qué diferencia hay entre una imagen y un contenedor? Usa como ejemplo lo que hiciste en los ejercicios G2 y G4.

Una imagen es como una plantilla que contiene todo lo necesario para ejecutar un programa, mientras que el contenedor es cuando ponemos esa imagen a funcionar. Por ejemplo, en los ejercicios G2 y G4 utilizamos imágenes de Docker para crear contenedores y comprobar cómo funcionaban.

2. En el Ejercicio G5 el archivo nota.txt desapareció y en el G6 no. Explica por qué.

En G5 el archivo desapareció porque lo habíamos guardado dentro del propio contenedor y, al eliminarlo, también perdimos su contenido. Sin embargo, en G6 utilizamos almacenamiento persistente, por lo que el archivo seguía estando disponible aunque elimináramos el contenedor.

3. ¿Qué diferencia hay entre docker ps y docker ps -a, y qué significa STATUS = Exited (0)?

La diferencia es que "docker ps" muestra solamente los contenedores que están funcionando en ese momento, mientras que "docker ps -a" muestra todos, incluso los que están apagados. Por otro lado, "Exited (0)" significa que el contenedor ha terminado correctamente y sin errores.

4. En -p 8181:8181, ¿qué número corresponde a tu equipo y cuál al contenedor? ¿Qué pasaría con -p 80:8080 en el ejercicio de nginx?

El primer número corresponde al puerto de nuestro ordenador y el segundo al puerto del contenedor. Si utilizamos "-p 80:8080" con nginx, podríamos acceder desde el puerto 80 de nuestro ordenador y Docker enviaría la conexión al puerto 8080 del contenedor.

5. ¿Por qué un contenedor de Oracle se queda en marcha y el de hello-world termina solo?

Porque Oracle necesita estar funcionando continuamente para que podamos conectarnos y utilizar la base de datos. Sin embargo, "hello-world" simplemente ejecuta un mensaje para comprobar que Docker funciona y cuando termina, se cierra automáticamente.

6. ¿Qué es el digest de una imagen y por qué lo registramos si ya sabemos que usamos :latest?

El digest es como una identificación única de una imagen, que nos permite saber exactamente cuál estamos utilizando. Lo registramos porque latest no significa que siempre sea la misma imagen, ya que puede actualizarse y cambiar con el tiempo.

7. ¿Qué comando borraría realmente los datos de Oracle? ¿Por qué docker rm oralab-26ai no lo hace?

El comando sería "docker volume rm oralab-26ai-data", siempre que el volumen no esté siendo utilizado por ningún contenedor. Esto se debe a que los datos de Oracle están guardados en un volumen independiente. Por eso, aunque eliminemos el contenedor con docker rm, los datos siguen guardados.

## 2. Git, organización y evidencia

8. ¿Por qué este laboratorio se hace dentro del repositorio oracle-database-lab, con Issue, branch y Pull Request, en vez de en una carpeta aparte?

Porque así tenemos todo el trabajo organizado y registrado en un mismo sitio. El Issue nos permite identificar la tarea, la branch trabajar sin modificar directamente la rama principal y el Pull Request sirve para que otra persona pueda revisar lo que hemos hecho antes de añadirlo al proyecto.

9. ¿Qué diferencia hay entre source 00-config.sh y bash 00-config.sh? ¿Por qué usamos source?

La diferencia es que "source" ejecuta el archivo en la misma terminal en la que estamos trbajando, por lo que las variables que contiene se quedan disponibles. En cambio, con "bash" se ejecuta en otro proceso y, cuando termina, esas variables no se quedan en nuestra terminal. Por eso utilizamos "source", ya que necesitamos esas variables para el resto de comandos.

10. Explica cada parte del nombre 20260915T091230Z_02-docker.script.log.

Los primeros ocho números (20260915) indican la fecha, es decir, el 15 de septiembre de 2026. Después, "T091230Z" indica la hora en UTC, las 09:12:30. El "02" hace referencia al número de la evidencia, "docker" nos indica a qué corresponde y ".script.log" significa que es un archivo donde se ha guardado el registro de la terminal.

11. ¿Para qué sirve .gitattributes y qué error evita?

Sirve para configurar cómo debe tratar Git determinados archivos. En nuestro caso lo utilizamos para que los archivos tengan los mismos finales de línea, independientemente de si trabajamos desde Windows o Linux. Así evitamos errores como "$'\r': command not found" al ejecutar scripts.

12. ¿Por qué en este Pull Request elegimos Create a merge commit en lugar de Squash and merge?

Porque durante esta práctica hemos ido haciendo un commit por cada apartado. Si utilizamos "Squash and merge", todos esos commits se juntarían en uno solo. En cambio, con "Create a merge commit" mantenemos el historial y podemos ver cada parte de la instalación por separado.

## 3. Seguridad

13. Describe las cuatro capas de la estrategia de contraseñas (Parte D) y qué pasaría si te saltas la primera.

La primera capa consiste en añadir el archivo config/.env a .gitignore para evitar que Git lo suba. La segunda es crear un archivo .env.example que sirva como ejemplo, pero sin poner contraseñas reales. La tercera consiste en crear nuestro archivo .env privado y comprobar que Git lo está ignorando. Por último, la cuarta capa es cargar las contraseñas mediante variables de entorno en lugar de escribirlas directamente en los comandos.

Si nos saltamos la primera capa, podríamos subir nuestras contraseñas al repositorio sin darnos cuenta.

14. ¿Por qué no escribimos la contraseña directamente en el comando docker run, aunque el script no se suba a Git?

Porque aunque no subamos el script a Git, la contraseña podría quedar guardada en el historial de comandos de la terminal. Por eso utilizamos variables de entorno, para no tener que escribir la contraseña directamente y evitar que quede expuesta.

15. Si descubres tu contraseña en un commit ya publicado, ¿basta con borrarla en un commit nuevo? ¿Qué debes hacer?

No, porque aunque la eliminemos en un commit nuevo, seguiría apareciendo en los anteriores. Lo que tendríamos que hacer sería cambiar esa contraseña cuanto antes, avisar al responsable y limpiar el historial del repositorio para evitar que siga apareciendo.

## 4. Oracle y herramientas

16. ¿Por qué no usamos SPOOL ni @archivo.sql con sqlplus dentro del contenedor, y qué hicimos en su lugar?

Porque los archivos que tenemos en Ubuntu no están directamente disponibles dentro del contenedor de Oracle. Por eso, si intentamos utilizar @archivo.sql, puede que no lo encuentre. Para solucionarlo, enviamos el contenido de los archivos SQL al contenedor desde Ubuntu y utilizamos tee para guardar los resultados. En el caso de SQLcl, sí utilizamos SPOOL porque lo ejecutamos directamente desde nuestro entorno.

17. ¿Qué hace WHENEVER SQLERROR EXIT SQL.SQLCODE al inicio de V000 y V001, y qué pasaría sin esa línea?

Esta instrucción hace que SQL*Plus se detenga cuando encuentra un error SQL. Es importante porque, si una parte de la migración falla, no queremos que siga ejecutando el resto como si nada hubiera pasado. Sin esa línea podríamos terminar con una base de datos configurada solo a medias y sin darnos cuenta.

18. ¿Qué es una migración y por qué V000 y V001 no se deben editar una vez aplicadas?
Una migración es un archivo SQL que utilizamos para hacer cambios en la base de datos de forma ordenada. En nuestro caso, V000 y V001 nos han servido para crear los entornos de negocio y sus tablas. No debemos modificarlas una vez aplicadas porque podríamos provocar diferencias entre las bases de datos. Si queremos cambiar algo, lo correcto sería crear una nueva migración.

19. ¿Por qué en SQL Developer se usa el servicio FREEPDB1 y no FREE ni un SID?

Porque FREEPDB1 es la base de datos conectable donde hemos creado los usuarios y las tablas de la práctica. En cambio, FREE corresponde al contenedor principal de Oracle. Por eso, para trabajar con nuestros esquemas necesitamos conectarnos a FREEPDB1 utilizando el nombre del servicio.

20. ¿Qué aporta SQLcl frente a SQL*Plus, y por qué un DBA debe dominar ambas?

SQLcl es una herramienta más moderna que SQL*Plus y tiene algunas funcionalidades que hacen más cómodo trabajar desde la terminal. Sin embargo, SQL*Plus sigue siendo muy utilizado y nos permite ejecutar consultas y scripts de administración. Por eso creo que es importante conocer ambas, ya que dependiendo del entorno podemos encontrarnos con una u otra.

## 5. Entorno de trabajo

21. ¿Por qué el curso pasa de Git Bash a Ubuntu en WSL 2? Da al menos dos problemas concretos de Git Bash que desaparecen en Ubuntu.

Porque Ubuntu en WSL 2 nos permite trabajar directamente con un entorno Linux, que es mucho más parecido al que se utiliza en servidores reales. Por ejemplo, evitamos problemas de compatibilidad con determinados comandos de Linux y también problemas relacionados con las rutas y permisos de los archivos. Además, podemos utilizar herramientas como apt para instalar programas directamente.

22. ¿Por qué clonamos el repositorio en ~/oracle-database-lab y no trabajamos sobre la carpeta de Windows (/mnt/c/...)? ¿Y por qué recomendamos bash frente a zsh para los scripts del curso?

Porque trabajar directamente en el sistema de archivos de Ubuntu suele ser más rápido y evita algunos problemas de permisos y compatibilidad que pueden aparecer al utilizar carpetas de Windows desde Linux.

Por otro lado, utilizamos Bash porque es el intérprete que se emplea en los scripts de la práctica y es muy habitual en Linux. Así nos aseguramos de que todos ejecutamos los mismos comandos y evitamos posibles diferencias.

