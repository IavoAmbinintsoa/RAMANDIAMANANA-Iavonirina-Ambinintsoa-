# RAMANDIAMANANA-Iavonirina-Ambinintsoa-
Installation de MYSQL/APACHE/PHP
Avant toute installation procedons d'abord a: 
	:~$ sudo apt install build-essential
La commande sudo apt install build-essential sert à installer :
_ un ensemble d'outils de base nécessaires pour la compilation de logiciels sur un système Linux comme :
 - gcc : Le compilateur C ; g++ : Le compilateur C++ et autre.
//----------------------------------------------------------------------------//
	INSTALLATION PHP
Décompressez et désarchivez le fichier php-8.3.6.tar.gz qui a été téléchargé depuis https://php.net :
	:~$ tar -zxvf php-8.3.6.tar.gz 
Après la décompression et le désarchivage, nous travaillons dans le répertoire du fichier PHP :
	:~$ cd php-8.3.6/
Consultons d'abord les procédures d'installation :
	:~$ less README
	:~$ less INSTALL
Examinons l'aide du fichier configure :
	:~$ ./configure --help
	:~$ ./configure
	:~$ make
Après `make`, s'il y a une erreur indiquant un manque de dépendances, installons d'abord ces paquets avec :
	:~$ sudo apt-get install libpcre3 libpcre3-dev zlib1g zlib1g-dev openssl libssl-dev
	:~$ sudo apt install pkg-config libsqlite3-dev libxml2-dev # pour les dépendances
Puis reprenons :
	:~$ ./configure
	:~$ make
Enfin, procédons à l'installation :
	:~$ sudo make install
Pour le tester :
	:~$ php -v
Affichons le résultat ici.
//------------------------------------------------------------------------------//
	INSTALLATION DE MYSQL
Tout d'abord, téléchargeons le fichier source de MySQL 8.3.0 depuis le site officiel...

Maintenant, vérifions que le fichier est bien présent à l'aide de la commande :
	:~$ ls
...
mysql-8.3.0.tar.gz
	:~$ tar -zxvf mysql-8.3.0.tar.gz
	:~$ cd mysql-8.3.0/
Consultons les fichiers confi.h.cmake, README et INSTALL :
	:~$ ls -l
	:~$ less README
	:~$ less INSTALL
Installons d'abord cmake  pour automatiser le processus de génération de fichiers de construction.
	:~$ sudo apt install cmake
	:~$ mkdir build
	:~$ cd build
	:~$ cmake ..
cmake ..: Cette commande invoque CMake pour générer les fichiers de construction nécessaires dans le répertoire "build" en se basant sur les fichiers CMakeLists.txt présents dans le répertoire parent
	:~$ make
installons les dependances :
sudo apt install -y libssl-dev libcurl4-openssl-dev
puis revenons sur 
	:~$ make
puius procedons a l 'installation 
	:~$ sudo make install
Changeons au répertoire /usr/local/mysql/bin/ :
	:~$ cd /usr/local/mysql/bin/
Vérifions le contenu du répertoire :
	:~$ ls
Essayons d'exécuter MySQL :
	:~$ ./mysql
Ouvrons le fichier bashrc pour y ajouter des configurations :
	:~$ nano ~/.bashrc
Ajoutons la ligne suivante à la fin du fichier :
	```
	export PATH="/usr/local/mysql/bin:$PATH"
	```
Enregistrons et quittons le fichier, puis rechargeons le fichier bashrc :
	:~$ source ~/.bashrc
Vérifions que MySQL est installé correctement :
	:~$ mysql --version
	mysql  Ver 8.3.0 for Linux on x86_64 (source distributions)
Cela nous indique que le fichier a ete installer deuis la code source
//--------------------------------------------------------------------------------//
		INSTALATION DE APACHE
 Met à jour la liste des paquets disponibles et leurs versions
	:~$ sudo apt update
	:~$ tar -xvfz httpd-2.4.59.tar.gz
	:~$ cd httpd-2.4.59/
	:~$ ./configure
	:~$ make
Erreur de manque de bibliotheque
Installe les outils de compilation et les bibliothèques nécessaires
	:~$ sudo apt install build-essential libssl-dev libexpat-dev libpcre3-dev libapr1-dev libaprutil1-dev libncurses5-dev zlib1g-dev
 - libssl-dev : Bibliothèque de développement OpenSSL pour la prise en charge du chiffrement SSL/TLS.
 - libexpat-dev : Bibliothèque de développement Expat pour l'analyse XML.
 - libpcre3-dev : Bibliothèque de développement PCRE (Perl Compatible Regular Expressions) pour le traitement des expressions régulières.
 - libapr1-dev et libaprutil1-dev : Bibliothèques de développement Apache Portable Runtime (APR) pour les fonctionnalités de base d'Apache HTTP Server..
 - libncurses5-dev : Bibliothèque de développement NCurses pour la manipulation d'interfaces utilisateur en mode texte.
 - zlib1g-dev : Bibliothèque de développement zlib pour la compression de données, utilisée par Apache pour la compression des données HTTP.
Accède au répertoire contenant les sources d'Apache
	:~$ cd ~/httpd-2.4.59/
Vérifie si le fichier configure est présent et exécutable
	:~$ ./configure --prefix=/usr/local/apache2
Compile les sources d'Apache
	:~$ make
Installe Apache dans /usr/local/apache2
	:~$ sudo make install
Testons en Démarre le serveur Apache
	:~$ sudo /usr/local/apache2/bin/apachectl -k start

![Capture d’écran du 2024-04-24 09-45-58](https://github.com/IavoAmbinintsoa/RAMANDIAMANANA-Iavonirina-Ambinintsoa-/assets/167605546/482dc0e5-58c1-4008-a163-88a98bcbd2e2)
