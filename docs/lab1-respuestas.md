\#7. Preguntas de comprobación 



David Gonzalez Gonzalez 





Responde con tus propias palabras. El objetivo no es memorizar comandos, sino demostrar que entiendes qué ocurre en cada zona de Git.





1). ¿Cuál es la diferencia entre Working Directory, Staging Area y Local Repository? Da un ejemplo de un archivo pasando por las tres.

\-El working directory es la carpeta del proyecto donde tengo todos los archivos y los voy cambiando . La Staging Area es como la zona intermedia donde pongo los cambios para el próximo commit . Y la Local Repository es donde se guardan los commits ya hechos.

Por ejemplo: Modifico README.md lo que es Working Directory, luego hago ( git add README.md) y pasa al Standing Area y por último con (git commit) se guarda en el historial. 





2). Si modificas un archivo pero no haces git add, ¿aparece ese cambio en tu próximo commit? Explica porqué.

\-No sino hago git add, no aparece en el commit, ya que no permitimos que pase del Standing Areaal Local Repository





3). ¿Por qué git status no mostraba las carpetas vacías que creaste en la Parte C? ¿Qué truco usamos para solucionarlo?

\-Porque git no guarda capetas vacías, sino archivos.  Para solucionarlo guardamos dentro de estas carpetas archivos llamados .gitkeep, así ya se guardaba algo dentro de estas carpetas. 





4). Explica con tus palabras qué es HEAD.

\-Es básicamente como una referencia que me dice en que rama me encuentro ahora  mismo. 





5). ¿Qué diferencia hay entre crear una branch con git switch -c y crear una carpeta nueva con mkdir?

\-Con git switch -c se crea una nueva rama y me cambia a ella, mientras que mkdir crea una carpeta nueva en el ordenador. 



¿Cómo lo comprobamos en la Parte G?

\-Lo comprobamos ya que no apareció ninguna carpeta llamada feature, ya que la rama existe dentro de Git, no como una carpeta.





6). Durante el conflicto de la Parte H, ¿qué representaba el contenido entre <<<<<<< HEAD y =======? ¿Y entre ======= y >>>>>>>?

\-La primera de ellas era la versión que ya tenía la rama en la que estaba, mientras que la parte de abajo era la versión de la otra rama.  Borrando los símbolos, actualizando el texto y después hacer un commit, solucionamos el conflicto.





7). ¿Por qué NO se debe hacer git commit --amend sobre un commit que ya se subió con git push?

\-Porque el commit amend cambia elúltimo commit y también el identificador, a la hora de que alguien descargase ese commit, se podría crear un conflicto ya que el historial de ambos es distinto. 





8). Si borras por accidente la carpeta .git de tu proyecto, ¿qué se pierde exactamente? ¿Se pierde también el código fuente que está en el disco?

\-Se perderían todo lo relacionado con GIT , es decir, los commits, ramas o el historial.  Pero los archivos seguirían estando en la carpeta. Es decir, no se perderían ni el código, ni los documentos, pero si dejaría esa carpeta de tener el historial de Git. 







9). Explica con tus propias palabras la diferencia entre Git y GitHub, sin usar la palabra "nube".

\-Git es el programa de mi ordenador donde creo versiones, hago ramas, commits etc, mientras el GitHub es el sitio donde puedo subir ese repositorio y asi poder guardarlo en un servidor y poder compartirlo con otras personas. 





10). ¿Por qué no se debe subir un archivo .env con contraseñas reales a un repositorio, aunque el repositorio sea privado?

\-Porque esas contraseñas se pueden quedar guardadas en el historial de Git.





11). Un compañero te dice: "hice push y ahora GitHub me rechaza el segundo push con 'non-fast-forward'". ¿Qué ha ocurrido probablemente y qué comando ejecutarías primero?

\-Pues probablemente significa que en GitHub hay cambios que no tiene en su ordenador, es decir, que alguien ha realizado cambios desde GitHub o desde otro ordenador y el no lo tiene “actualizado”. Para solucionarlo haría un Git pull y ya luego haría el Git push de nuevo. 





12). ¿Qué tipo de Conventional Commit (feat, fix, docs, test…) usarías para: añadir un índice de rendimiento a una tabla, corregir una restricción mal definida, y actualizar el README?

\-Para añadir un índice de rendimento usaría perf, para corregir una restricción mal definida fix y para actualizar el README docs



