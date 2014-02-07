Estos comandos debes de colocar para realizar un testeo...

1. Crear la base de datos de testeo y esta se encuentra en el archivo database.yml:
   # MySQL.  Versions 4.1 and 5.0 are recommended.
#
# Install the MYSQL driver
#   gem install mysql2
#
# Ensure the MySQL gem is defined in your Gemfile
#   gem 'mysql2'
#
# And be sure to use new-style password hashing:
#   http://dev.mysql.com/doc/refman/5.0/en/old-client.html
development:
  adapter: mysql2
  encoding: utf8
  reconnect: false
  database: folgama_development
  pool: 5
  username: root
  password: 
  host: localhost

# Warning: The database defined as "test" will be erased and
# re-generated from your development database when you run "rake".
# Do not set this db to the same as development or production.
test:
  adapter: mysql2
  encoding: utf8
  reconnect: false
  database: folgama_test
  pool: 5
  username: root
  password: 
  host: localhost

production:
  adapter: mysql2
  encoding: utf8
  reconnect: false
  database: folgama_development
  pool: 5
  username: root
  password: 
  host: localhost

 Con estas lineas de comando... 
 NOTA: Con esta instruccion creas las tres bases de datos (Production, Development, Test)
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