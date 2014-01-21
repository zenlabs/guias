Guia para limpiar el branch.
============================= 
Resulta que puede darse el caso y muchas veces incurrir en ello, que nos encontremos en un branch con conflictos o corrupto por ejemplo en un proyecto 
dentro del branch develo.

Para resolver tal problema se deben seguir los pasos a continuación:

El siguiente ejemplo debemos encontrarnos en la carpeta correspondiente al proyecto desde consola

Los Pasos para limpiar un branch son los siguientes:

```bash
git st
# muestra el branch en el que uno esta... si no lo estas haces el checkout develop, pero creo que la mayoria ya se encuentra en ese directorio, entonces te vas
#al comando git add . y siguen con todas sus instrucciones
```
```bash
localhost:framin-co zenlabs$ git checkout develop
```

```bash
 # limpiamos el branch de cambios que se hicieron
 git add .
 git reset --hard HEAD
 # aqui ya no tendriamos que ver cambios
 git st
 # cambiamos de branch original
 git checkout origin/develop
 # para borrar el branch corrupto
 git branch -D develop
 #aqui deberia mostrarte una linea diciendote que has eliminado el branch develop (Deleted branch develop)
 # creamos el branch nuevo, sin errores
 git checkout -b develop
 #Aqui deberia mostrarte un mensaje diciendoate que has cambiado (switched a new branch/develop)

 #estos ultimos pasos en caso de que se este en medio de un rebase cortado
 # si hacemos de nuevo esto no deberia de bajar nada y decir que esta up-date
 git pull --rebase develop
 
```
