Solucion para tener acceso en la carpeta Web de OSx

sudo chmod -R o+w /Library/WebServer/Documents

Solucion para actualizar el CURL con soporte nuevo a ssl

brew install --with-openssl curl

instalar aca php55

instalar phpmycript

brew install php55-mcrypt --without-homebrew-php --with-homebrew-curl


For enable .htaccess

LoadModule rewrite_module libexec/apache2/mod_rewrite.so
LoadModule php5_module        libexec/apache2/libphp5.so
are uncommented.

Also ensure that AllowOverride is set to All within the <Directory "/Library/WebServer/Documents"> section.
	
	
http://stackoverflow.com/questions/10717668/magento-installation-uable-to-access-admin-panel