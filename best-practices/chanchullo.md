Guia para limpiar el branch.
============================= 
Resulta que puede darse el caso y muchas veces incurrir en ello, que nos encontremos en un branch con conflictos o corrupto por ejemplo en un proyecto 
dentro del branch develo.

Para resolver tal problema se deben seguir los pasos a continuación:

El siguiente ejemplo debemos encontrarnos en la carpeta correspondiente al proyecto desde consola

Los Pasos para limpiar un branch son los siguientes:

```bash
git st
# muestra el branch en el que uno esta...
```

localhost:framin-co zenlabs$ git checkout development
localhost:framin-co zenlabs$ git st
localhost:framin-co zenlabs$ stree
localhost:framin-co zenlabs$ git pull --rebase development
localhost:framin-co zenlabs$ git st
localhost:framin-co zenlabs$ git add .
localhost:framin-co zenlabs$ git reset --hard HEAD
localhost:framin-co zenlabs$ git st
localhost:framin-co zenlabs$ git checkout origin/development
para borrar el branch corrupto
localhost:framin-co zenlabs$ git branch -D development
localhost:framin-co zenlabs$ git checkout -b development

estos ultimos pasos en caso de que se este en medio de un rebase cortado

localhost:framin-co zenlabs$ git pull --rebase development
localhost:framin-co zenlabs$ git pull --rebase origin development
localhost:framin-co zenlabs$

y actualizar en el source tree con windows+R y listo lo tienes en correcto estado!!!!

