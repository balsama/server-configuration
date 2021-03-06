## Install LAMP ##

Install a compiler

    $ sudo aptitude install build-essential

Install MySQL

    $ sudo aptitude install mysql-server libmysqlclient-dev

Implement secure mysql install

    $ mysql_secure_installation

> Answer yes to everything exept the first question (assumin you set a root
> password during installation).

Setup mysqlcheck to run regularly

    $ crontab -e

> Add the following line:

    @weekly mysqlcheck -o --user=root --password=<your msql root password here> -A

> The first time you run crontab, you will be asked to select the default
> editor. Choose 3 (vim).

Tweak mysql settings

    $ sudo vi /etc/mysql/conf.d/drupal.cnf

> Enter the following in the new drupal.cnf file and save (this increases the
> mysql query cache to 128M):

    [mysqld]
    query_cache_size = 134217728

Install Apache

    $ sudo aptitude install apache2

Install PHP

    $ sudo aptitude install php5 libapache2-mod-php5 php5-mysql

Install PHP cURL

    $ sudo aptitude install curl libcurl3 libcurl3-dev php5-curl
    
Install PHP GD

    $ sudo aptitude install php5-gd

Install Pear and PECL for file upload progress

    $ sudo aptitude install php5-dev
    $ sudo aptitude install php-pear
    $ sudo pecl install uploadprogress

> Add the upload progress extension to php configuration

    $ sudo vi /etc/php5/apache2/php.ini

> In the `File Uploads` sectionPaste the following line below ` file_uploads = On`:

    extension=uploadprogress.so

Install git:

    $ sudo aptitude install git

Install Drush:

    $ sudo aptitude install drush

Install postfix 

    $ sudo aptitude install postfix

Add mail config file

    $ sudo vi /etc/php5/conf.d/mailconfig.ini

> Place the following in the file (substitute email address):

    sendmail_from = noreply@domain.com
    sendmail_path = /usr/sbin/sendmail -t -i -f noreplay@domain.com

Restart the server

    $ sudo reboot

