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

```bash
git st
# añadir uno a uno por cada alias
 git config --global alias.co checkout 
 git config --global alias.ci commit
 git config --global alias.st status
 git config --global alias.co checkout
 git config --global alias.ci commit
 git config --global alias.st status
 git config --global alias.br branch
 git config --global alias.hist 'log --pretty=format:"%h %ad | %s%d [%an]" --graph --date=short'
 git config --global alias.type 'cat-file -t'
 git config --global alias.dump 'cat-file -p'
```


Y pegarlo en la terminal y darle enter esto añadira el siguiente texto dentro del archivo .gitconfig de $HOME del directorio así

Con esto Ud. ya puede llamar la siguiente vez a los comandos GIT con sus abreviaturas correspondientes

Guia para matar el proceso del server de rails
==============================================

```bash
# añadir uno a uno por cada alias
lsof -wni tcp:3000
#muestra lo siguiente 
COMMAND     PID    USER   FD   TYPE             DEVICE SIZE/OFF NODE NAME
Google      429 zenlabs   59u  IPv4 0x945528c7b8ca9d89      0t0  TCP 127.0.0.1:51441->127.0.0.1:hbci (ESTABLISHED)
ruby      20180 zenlabs   12u  IPv4 0x945528c7ba147d89      0t0  TCP *:hbci (LISTEN)
ruby      20180 zenlabs   13u  IPv4 0x945528c7ba2e1d89      0t0  TCP 127.0.0.1:hbci->127.0.0.1:51157 (CLOSE_WAIT)
#colocar
kill -9 20180
#luego al hacer corre de nuevo 
lsof -wni tcp:3000
#no deberia mostrar nada
```

Guía para iniciar un nuevo proyecto desde cero en rails
=======================================================
Primero colocar esto
```bash
rvm use 2.1.2@rails41
#luego crear el nuevo proyecto con 
rails new my_project_name
#una vez listo entrar al directorio del proyecto y configurar el .rvmrc de la sigte manera
mate .rvmrc
#dentro colocar rvm use 2.1.2@rails41 --create guardar y salir del directorio y volver a entrar
#al mensaje colocar y
********************************************************************************************************************
* NOTICE                                                                                                           *
********************************************************************************************************************
* RVM has encountered a new or modified .rvmrc file in the current directory, this is a shell script and           *
* therefore may contain any shell commands.                                                                        *
*                                                                                                                  *
* Examine the contents of this file carefully to be sure the contents are safe before trusting it!                 *
* Do you wish to trust '/Users/zenlabs/dev/ruby/.rvmrc'?                                                           *
* Choose v[iew] below to view the contents                                                                         *
********************************************************************************************************************
y[es], n[o], v[iew], c[ancel]> y
# luego configurar el archivo database.yml dentor del proyecto 
#luego darle un bundle por consola al proyecto
bundle
#y por ultimo crear la BD develop y hacer correr
rake db:migrate
#preparar el proyecto para usar GIT, en el archivo .gitignore colocar todo esto
*******************************************************************
#----------------------------------------------------------------------------
# Ignore these files when commiting to a git repository.
#
# See http://help.github.com/ignore-files/ for more about ignoring files.
#
# The original version of this file is found here:
# https://github.com/RailsApps/rails-composer/blob/master/files/gitignore.txt
#
# Corrections? Improvements? Create a GitHub issue:
# http://github.com/RailsApps/rails-composer/issues
#----------------------------------------------------------------------------

# bundler state
/.bundle
/vendor/bundle/
/vendor/ruby/

# minimal Rails specific artifacts
db/*.sqlite3
/db/*.sqlite3-journal
/log/*
/tmp/*

# configuration file introduced in Rails 4.1
/config/secrets.yml

# various artifacts
**.war
*.rbc
*.sassc
.rspec
.redcar/
.sass-cache
/config/config.yml
/config/database.yml
/coverage.data
/coverage/
/db/*.javadb/
/db/*.sqlite3
/doc/api/
/doc/app/
/doc/features.html
/doc/specs.html
/public/cache
/public/stylesheets/compiled
/public/system/*
/spec/tmp/*
/cache
/capybara*
/capybara-*.html
/gems
/specifications
rerun.txt
pickle-email-*.html
.zeus.sock
.rvmrc
config/database.yml

# If you find yourself ignoring temporary files generated by your text editor
# or operating system, you probably want to add a global ignore instead:
#   git config --global core.excludesfile ~/.gitignore_global
#
# Here are some files you may want to ignore globally:

# scm revert files
**.orig

# Mac finder artifacts
.DS_Store

# Netbeans project directory
/nbproject/

# RubyMine project files
.idea

# Textmate project files
/*.tmproj

# vim artifacts
**.swp

.rvmrc

public/uploads
*******************************************************************
#por ultimo hacer en consola
git init
git st
git add .
git ci -am "My comment commit"
git st
#creamos el branch develop
git checkout -b develop
#abrimos el source tree e iniciamos el git flow
stree
#por ultimo para colocar todos los cambios dentro del gitlab.zenlabs hacemos correr por consola lo sigte
git remote add origin [_url_del_repo_]
#luego 
git push origin develop
```