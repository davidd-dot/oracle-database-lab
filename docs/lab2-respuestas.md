\# Laboratorio 2 - Preguntas de comprobación



1\. ¿Por qué un Issue sin criterios de aceptación es un problema?



Porque aunque se explique lo que hay que hacer, si no se ponen unos criterios claros, puede que cada persona lo entienda de una forma diferente. Además, sin esos criterios es más difícil saber si la tarea está bien hecha o si falta algo por completar.





2\. Explica la diferencia entre Refs #N y Closes #N en un commit o Pull Request.



La diferencia es que Refs #N sirve para indicar que un cambio está relacionado con un Issue, pero sin cerrarlo. En cambio, Closes #N hace que el Issue se cierre automáticamente cuando los cambios se fusionan con la rama principal.

Por ejemplo, nosotros usamos Refs #1 mientras trabajábamos en el Issue y Closes #1 para que se cerrara al hacer el Merge.





3\. ¿Qué ocurre exactamente si intentas hacer git push directamente sobre una branch main protegida? ¿Es un error tuyo o un fallo del sistema?



GitHub no te deja subir los cambios directamente a main porque tiene una protección que lo impide. No es un fallo del sistema, sino que está funcionando como debería, ya que primero tenemos que crear un Pull Request y conseguir que alguien apruebe los cambios.





4\. Un compañero te dice: "he aprobado el PR sin mirar los archivos, total ya me fío". ¿Qué riesgo tiene esa forma de revisar?



El problema es que puede haber errores que nadie haya detectado. Aunque confíes en la persona que ha hecho los cambios, siempre es mejor revisarlos para comprobar que todo está bien y evitar problemas después.





5\. Si el reviewer pide un cambio y tú ya habías hecho push de tu branch, ¿tienes que abrir un Pull Request nuevo? Explica qué ocurre técnicamente con el PR existente cuando haces un nuevo commit.



No hace falta crear otro Pull Request. Simplemente corriges lo que te han pedido, haces otro commit y lo subes a la misma rama. GitHub actualiza automáticamente el Pull Request que ya tenías abierto con los nuevos cambios.





6\. Describe con tus palabras la diferencia entre Merge commit, Squash and merge y Rebase and merge. ¿Cuál usarías para una branch con commits "wip", "fix", "fix2", "ok ya"?



Merge commit junta las ramas y crea un commit de fusión manteniendo los commits anteriores. Squash and merge junta todos los commits de la rama en uno solo. Rebase and merge incorpora los commits uno detrás de otro, sin crear un commit de fusión.



En el ejemplo usaría Squash and merge, porque los commits tienen nombres poco descriptivos.





7\. ¿Por qué borrar una branch después del merge no elimina el trabajo realizado en ella?



Porque al hacer el merge, los cambios ya se han incorporado a la rama principal. Por eso, aunque eliminemos la rama que hemos utilizado para trabajar, los cambios siguen guardados en main.





8\. ¿Qué información debería contener siempre la descripción de un Pull Request, como mínimo?



Debería explicar qué cambios se han hecho, por qué se han realizado, cómo se ha comprobado que funcionan y con qué Issue están relacionados. Así, la persona que lo revise puede entender el trabajo sin tener que estar preguntando.





9\. Un reviewer escribe solo "esto está mal" como comentario. ¿Qué le falta a ese comentario para ser útil? Reescríbelo tú con un ejemplo inventado.



Le falta explicar qué es exactamente lo que está mal y cómo se podría solucionar. Si solo pone eso, la otra persona puede que no sepa qué tiene que cambiar.



Por ejemplo: "issue (blocking): Creo que falta comprobar si el usuario ha introducido todos los datos antes de guardar el formulario, porque si deja algún campo vacío podría dar un error".





10\. ¿Qué diferencia hay entre que main esté protegida y que simplemente el equipo "se ponga de acuerdo" en no hacer push directo?



La diferencia es que, si main está protegida, GitHub impide que se suban cambios directamente sin cumplir las condiciones. En cambio, si solamente nos ponemos de acuerdo, cualquiera podría equivocarse y subir cambios sin revisarlos.





11\. Explica con un ejemplo propio la diferencia entre un comentario issue: (blocking) y uno nitpick: (if-minor) en formato Conventional Comments.



Un comentario issue (blocking) indica un problema importante que se debería corregir antes de aprobar los cambios. Por ejemplo, si un formulario permite guardar datos sin comprobar que sean correctos.



En cambio, nitpick (if-minor) se utiliza para detalles pequeños que no afectan realmente al funcionamiento, como cambiar el nombre de una variable para que se entienda mejor.





12\. Si tu próximo commit es feat!: cambia la firma de la función principal de la API, ¿qué tipo de versión SemVer se dispara y por qué?



Se produciría un cambio de versión mayor (MAJOR), porque el signo de exclamación indica que se ha realizado un cambio que puede dejar de ser compatible con versiones anteriores. Al cambiar la firma de la función principal, puede que otros programas que la utilizaban dejen de funcionar correctamente.





13\. ¿Por qué abrir un Draft PR desde el primer commit estructural puede ahorrar tiempo al equipo, aunque parezca más lento para el autor individual?



Porque permite que otras personas puedan ver el trabajo desde el principio y avisar si hay algo que se debería cambiar. Así evitamos hacer mucho trabajo y descubrir al final que hay que modificar una parte importante

