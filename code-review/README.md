Flujo de trabajo para Zenlabs.
===

Este es el flujo de trabajo que siempre se utilizara dentro de Zenlabs en cualquiera de sus proyectos, tomar debida nota:
Cuando se les registre dentro de el sitio http://gitlab.zenlabs.net/ recibiran un email con el usuario y contraseña o de lo contrario preguntar al administrador del mismo.
Luego de esto se tiene que registrar la llave ssh dentro del site para que la maquina en que trabaja pueda tener acceso a los repositorios de código, si no se registra esto no podrá realizar ningún trabajo.
1 Configuracion
Generacion de los SSH Keys

Para generar una llave dentro de su maquina haga el siguiente comando:
````
ssh-keygen -t rsa -C "info@zenlabs.net"
# Generating public/private rsa key pair...
````
lo siguiente es copiar y pegar el contenido de la llave publica en su perfil, dentro de la sección SSH Keys
````
cat ~/.ssh/id_rsa.pub
# ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC6eNtGpNGwstc....
````
Importante: usted puede registrar todas las maquinas que requiera.
Configurar el email y el usuario dentro de git:
Para asignar el nombre de usuario:
git config --global user.name "Pepe botellas"
# Setear el nombre
git config --global user.name
# Verificar que este asignado correctamente # Pepe botellas
Para asignar el email:
git config --global user.email "tu_cuenta@zenlabs.net"
# Setea el nuevo email
git config --global user.email
# Verificar el nuevo email #tu_cuenta@zenlabs.net

como paso final esta probar que funcione el acceso para esto ejecuta este comando:
````
ssh git@zenlabs.net
hello cr_zenlabs_net_1356734671, this is git@vps-1103321-10687 running gitolite3 v3.04-42-g2d29cf7 on git 1.7.11.2

 R W	develoft/auxiliumart
 R W	develoft/auxrails
 R W	develoft/calvirug
 R W	zenlabs/goola
Connection to zenlabs.net closed.
````
Si da otro tipo de respuesta consulte con el administrador.
Instalacion de git flow
Seguir los siguientes pasos https://github.com/nvie/gitflow/wiki/Installation



2 Flujo de trabajo:
dentro de los proyectos en Zenlabs se manejan dos branchs, uno el de producción o versión final es el branch “master” y otro de desarrollo que esta en “develop”.
Tener una copia del proyecto en su maquina:
git  clone git@zenlabs.net:ruta_al_repositorio.git

la ruta del repositorio se le facilitara dentro de gitlab.
Una ves completo, ejecutara:

````
git fetch origin
````

para crear el branch develop, que todavía no lo tiene, si lo tiene puede saltarse este paso:
git checkout develop
si tiene que crear nuevas funcionalidades dentro del repositorio, lo que deberá hacer es:

````
git checkout develop
git pull --rebase origin develop
git flow feature start nueva_funcionalidad
git commit --am “descripción de la funcionalidad”
git commit …. # aquí diferentes commits
git push origin feature/nueva_funcionalidad
````

luego dentro de gitlab tiene que iniciar un nuevo merge request:


se va a la opción dentro del proyecto Merge Requests => New Merge Request

aquí elegimos el branch feature que anteriormente se realizo un push y este SIEMPRE debe de pedirse un merge a develop, como en la figura.
Luego añada un descripción corta de la característica que acaba de realizar, y además seleccione a su code review siempre, normalmente es el líder del grupo.
Una ves que se hayan hecho la revisión si pasa el líder de grupo hara el merge automatico a develop, sino entonces le dira las cosas que tiene que arreglar para que pueda pasar su código.
Importante: desde que crea su feature ya no realizara pull ni a develop o master dentro del mismo, esto corromperá su codigo.
Nota: cuando este trabajando en su feature, es recomendable que no exceda de 3 dias laborables, ya que al desactualizar el código por esos tres días al momento de mergear dentro de develop será difícil para el líder mergear su código, además haga commits con menos de 10 archivos modificados por commit, y menos de 10 commits por merge request.







Tips:
Resetear su branch o limpiarlo: cuando al momento de hacer pull no le deja o no desaparecen archivos que ya los commiteo o simplemente piensa que corrompio su código, haga lo siguiente:
esto borrara TODOS su cambios que tenga, tenga mucho cuidado, en este caso limpiaremos el branch develop:

````
git fetch origin
git checkout origin/develop
git branch -D develop
git checkout -b develop
````








