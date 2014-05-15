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
 # si existen cambios por hacer debemos limpiarlos con un git reset
 # (opcional) limpiamos el branch de cambios que se hicieron
 git add .
 git reset --hard HEAD
 # aqui ya no tendriamos que ver cambios
 git st
 # IMPORTANTE jalamos TODOS los cambios actuales
 git fetch origin
 # cambiamos de branch original
 git checkout origin/develop
 # para borrar el branch corrupto
 git branch -D develop
 #aqui deberia mostrarte una linea diciendote que has eliminado el branch develop (Deleted branch develop)
 # creamos el branch nuevo, sin errores
 git checkout -b develop
 #Aqui deberia mostrarte un mensaje diciendoate que has cambiado (switched a new branch/develop)
 # (opcional) si hacemos de nuevo esto no deberia de bajar nada y decir que esta up-date
 git pull --rebase origin develop
 
```

que no instale la documentacion de las gemas
============================================

Esto solo hacerlo UNA VES.

```
echo "gem: --no-ri --no-rdoc" >> ~/.gemrc
```

Guia para configurar los alias de comandos GIT.
===============================================
Copiar el siguiente texto

git config --global alias.co checkout
git config --global alias.ci commit
git config --global alias.st status
git config --global alias.br branch
git config --global alias.hist 'log --pretty=format:"%h %ad | %s%d [%an]" --graph --date=short'
git config --global alias.type 'cat-file -t'
git config --global alias.dump 'cat-file -p'

Y pegarlo en la terminal y darle enter esto añadira el siguiente texto dentro del archivo .gitconfig de $HOME del directorio así

[alias]
	co = checkout
	ci = commit
	st = status
	br = branch
	hist = log --pretty=format:\"%h %ad | %s%d [%an]\" --graph --date=short
	type = cat-file -t
	dump = cat-file -p

Con esto Ud. ya puede llamar la siguiente vez a los comandos GIT con sus abreviaturas correspondientes