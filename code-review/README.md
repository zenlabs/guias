Flujo de trabajo para Zenlabs.
=============================

Este es el flujo de trabajo que siempre se utilizara dentro de Zenlabs en cualquiera de sus proyectos, tomar debida nota:
Cuando se les registre dentro de el sitio http://gitlab.zenlabs.net/ recibiran un email con el usuario y contraseña o de lo contrario preguntar al administrador del mismo.
Luego de esto se tiene que registrar la llave ssh dentro del site para que la maquina en que trabaja pueda tener acceso a los repositorios de código, si no se registra esto no podrá realizar ningún trabajo.


## 1 Configuracion de Git y Gitlab


### 1.1 Generacion de los SSH Keys

Para generar una llave dentro de su maquina haga el siguiente comando:

```bash
ssh-keygen -t rsa -C "info@zenlabs.net"
# Generating public/private rsa key pair...

# despues de esto preguntara donde lo creara, por defecto es en /home/username/.ssh/id_rsa esta bien por defecto en esa carpeta
# Luego pedira la contraseña de la llave publica, por defecto sin contraseña 
# confirmen la contraseña en blanco.
```

### 1.2 Ver/copiar tu llave publica.

lo siguiente es copiar y pegar el contenido de la llave publica en su perfil, dentro de la sección SSH Keys, con este comando se logra mostrar el contenido y luego este mismo se lo copia.

```bash
cat ~/.ssh/id_rsa.pub
# ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC6eNtGpNGwstc....
```

### 1.3 Adicion de tu SSH KEY a tu cuanta en gitlab

![Adicion de llave ssh](http://gitlab.zenlabs.net/zenlabs/guias/raw/master/images/add-ssh-gitlab.jpg "Title")

Importante: usted puede registrar todas las maquinas que requiera.

### 1.4 Configurar el email y el usuario dentro de git:

Para asignar el nombre de usuario:

```bash
git config --global user.name "Pepe botellas"
# Setear el nombre
git config --global user.name
# Verificar que este asignado correctamente # Pepe botellas
Para asignar el email:
git config --global user.email "tu_cuenta@zenlabs.net"
# Setea el nuevo email
git config --global user.email
# Verificar el nuevo email #tu_cuenta@zenlabs.net
```
### 1.5 verificacion de que configuro correctamente su cuenta

Como paso final esta probar que funcione el acceso para esto ejecuta este comando:

```bash
ssh git@gitlab.zenlabs.net
Welcome to GitLab, USERNAME!
Connection to zenlabs.net closed.
```

Si da otro tipo de respuesta consulte con el administrador.

## 2 Instalacion de Gitflow

Seguir los siguientes pasos https://github.com/petervanderdoes/gitflow/wiki (NUEVO)


## 3 Flujo de trabajo:

dentro de los proyectos en Zenlabs se manejan dos branchs, uno el de producción o versión final es el branch “master” y otro de desarrollo que esta en “develop”.
Tener una copia del proyecto en su maquina:

```bash
git  clone git@zenlabs.net:ruta_al_repositorio.git
```

la ruta del repositorio se le facilitara dentro de gitlab.
Una ves completo, ejecutara:

```bash
git fetch origin
```

para crear el branch develop, que todavía no lo tiene, si lo tiene puede saltarse este paso:

```bash
git checkout develop
```

si tiene que crear nuevas funcionalidades dentro del repositorio, lo que deberá hacer es:

```bash
git checkout develop
git pull --rebase origin develop
git flow feature start nueva_funcionalidad
git commit --am “descripción de la funcionalidad”
git commit ... # aquí diferentes commits
git push origin feature/nueva_funcionalidad
```

luego dentro de gitlab tiene que iniciar un nuevo merge request:

![Nuevo Merge Request](http://gitlab.zenlabs.net/zenlabs/guias/raw/master/images/merge-request.jpg "Title")

se va a la opción dentro del proyecto Merge Requests => New Merge Request

![Nuevo Merge Request](http://gitlab.zenlabs.net/zenlabs/guias/raw/master/images/new-merge-request.jpg "Title")

aquí elegimos el branch feature que anteriormente se realizo un push y este **SIEMPRE** debe de pedirse un merge a develop, como en la figura.
Luego añada un descripción corta de la característica que acaba de realizar, y además seleccione a su code review siempre, normalmente es el líder del grupo.
Una ves que se hayan hecho la revisión si pasa el líder de grupo hara el merge automatico a develop, sino entonces le dira las cosas que tiene que arreglar para que pueda pasar su código.

##### OJO

Una ves que se termine el code review de un feature y este se haya mergeado al branch **develop** este branch tiene que ser borrado de la maquina local como del servidor remoto __(principalmente del remoto)__, Tiene que estar seguro que se a mergeado a develop por que sus cambios se perderan

**Procedimiento**

borrado del branch local:

```bash
git branch -d feature/nombre_del_feature
```

borrado del branch remoto:

```bash
git push origin :feature/nombre_del_feature
```


##### Importante:

Desde que crea su feature ya no realizara pull ni a develop o master dentro del mismo, esto corromperá su codigo.

#### Nota:

Cuando este trabajando en su feature, es recomendable que no exceda de 3 dias laborables, ya que al desactualizar el código por esos tres días al momento de mergear dentro de develop será difícil para el líder de grupo mergear su código, además haga commits con menos de 10 archivos modificados por commit, y menos de 10 commits por merge request.

#### Nota 2:

Usted puede todo el momento hacer push a su feature, y este puede ser revisado por su lider de grupo en cualquier momento, pero una ves que se ponga al Merge request el comentario **Code Review** este indicara que el lider ya puede hacer la revision de codigo y ademas el merge a develop,  el merge solo se debe de realizar una solo ves ya que sino traera problemas dentro del proyecto.

Tips:
-----

Resetear su branch o limpiarlo: cuando al momento de hacer pull no le deja o no desaparecen archivos que ya los commiteo o simplemente piensa que corrompio su código, haga lo siguiente:
esto borrara **TODOS** su cambios que tenga, tenga mucho cuidado, en este caso limpiaremos el branch develop:

```bash
git fetch origin
git checkout origin/develop
git branch -D develop
git checkout -b develop
```