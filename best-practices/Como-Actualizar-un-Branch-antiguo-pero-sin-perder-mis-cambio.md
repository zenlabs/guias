Guia para actualizar un branch antiguo por uno nuevo pero sin perder mis cambios.
============================= 


Los Pasos para hacer este procedimiento se realizanlos siguientes:

```bash
git st
# Y nos parece esto ==> "rebase in progress; onto e033b23"
 #luego escribimos lo siguiente
 git commit -am "conlicto en aplicacion.js"
 # luego
 git rebase -- continue
 # luego
 rm -fr "/Users/zenlabs/dev/ruby/folgama/.git/rebase-apply"
 # luego
 git pull origin feature/inventation
 # y finalente
 git st
 # y tenemos actualizado y con nuetros cambios
```