Estos comandos debes de colocar para realizar un testeo...

1. Crear las 3 bases de datos de tu proyecto :
   - Para development
   - Para production
   - Para test
 Con estas lineas de comando...
```
  rake db:create:all

```

2. Inicializar el testeo con la siguiente instruccion:
 
```
  spring rake db:test:prepare

```

3. Luego
```
  spring rspec spec/models/multimedia_spec.rb

```
4. Despues definimos que model/*_spec.rb queremos testear, ejemplo: multimedia, entonces debemos de colocar en la linea de comandos
```
  spring rspec spec/models/multimedia_spec.rb

```
5. Y luego si hay errores apareceran y si no los hay... le mostrara las siguientes lineas....en la consola

   2/2 |========================= 100 ==========================>| Time: 00:00:01

   Finished in 1.88 seconds
   2 examples, 0 failures

   Randomized with seed 38745
   
   Algo parecido....

