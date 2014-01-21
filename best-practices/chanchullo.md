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
```bash
localhost:framin-co zenlabs$ git checkout development
```
```bash
localhost:framin-co zenlabs$ git st
```
```bash
localhost:framin-co zenlabs$ stree
```
```bash
localhost:framin-co zenlabs$ git pull --rebase development
```
```bash
localhost:framin-co zenlabs$ git st
```
```bash
localhost:framin-co zenlabs$ git add .
```
```bash
localhost:framin-co zenlabs$ git reset --hard HEAD
```
```bash
localhost:framin-co zenlabs$ git st
```
```bash
localhost:framin-co zenlabs$ git checkout origin/develop
```
```bash
#para borrar el branch corrupto
localhost:framin-co zenlabs$ git branch -D develop
#aqui deberia mostrarte una linea diciendote que has eliminado el branch develop (Deleted branch develop)
```
```bash
localhost:framin-co zenlabs$ git checkout -b develop
#Aqui deberia mostrarte un mensaje diciendoate que has cambiado (switched a new branch/develop)
```
```bash

#estos ultimos pasos en caso de que se este en medio de un rebase cortado

localhost:framin-co zenlabs$ git pull --rebase develop
```
```bash
localhost:framin-co zenlabs$ git pull --rebase origin develop
```
```bash
localhost:framin-co zenlabs$


#y actualizar en el source tree con windows+R y listo lo tienes en correcto estado!!!!
```