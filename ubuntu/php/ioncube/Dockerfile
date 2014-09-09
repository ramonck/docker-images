FROM ubuntu:14.04

# Install packages
RUN sudo apt-get update 
RUN DEBIAN_FRONTEND=noninteractive sudo apt-get -y install supervisor curl apache2 libapache2-mod-php5 php5-gd php5-curl php-pear php-apc
RUN sudo curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin && sudo mv /usr/local/bin/composer.phar /usr/local/bin/composer
RUN sudo sed -i "s/variables_order.*/variables_order = \"EGPCS\"/g" /etc/php5/apache2/php.ini

RUN sudo cd /usr/local/ && sudo wget http://downloads3.ioncube.com/loader_downloads/ioncube_loaders_lin_x86-64.tar.gz && sudo tar xzf ioncube_loaders_lin_x86-64.tar.gz && sudo rm -f ioncube_loaders_lin_x86-64.tar.gz
RUN sudo echo "zend_extension=/usr/local/ioncube/ioncube_loader_lin_5.5.so" > /etc/php5/mods-available/ioncube.ini
RUN sudo ln -s /etc/php5/mods-available/ioncube.ini /etc/php5/cli/conf.d/01-ioncube.ini
RUN sudo ln -s /etc/php5/mods-available/ioncube.ini /etc/php5/apache2/conf.d/01-ioncube.ini

EXPOSE 80
EXPOSE 22
