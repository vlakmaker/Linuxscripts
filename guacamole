#!/bin/bash

#Update system
Echo "updating system"
sudo apt-get update

#Installing Dependencies
echo "installing dependencies"
sudo apt-get  -y install libcairo2-dev libjpeg62-dev libpng12-dev libossp-uuid-dev libfreerdp-dev libpango1.0-dev libssh2-1-dev libssh-dev tomcat7 tomcat7-admin tomcat7-user libavcodec-dev libavutil-dev libswscale-dev libfreerdp-dev libpango1.0-dev libssh2-1-dev 	libtelnet-dev libvncserver-dev libpulse-dev 	libssl-dev libvorbis-dev libwebp-dev

#Downloading Guacamole server + installing Guacamole server
echo "Downloading and installing Guacamole server"
wget http://apache.org/dyn/closer.cgi?action=download&filename=guacamole/0.9.14/source/guacamole-server-0.9.14.tar.gz
sudo tar -xzf guacamole-server-0.9.14.tar.gz
sudo cd guacamole-server-0.9.14/
sudo ./configure --with-init-dir=/etc/init.d
sudo make
sudo make install

#Downloading Guacamole client + installing Guacamole client
echo "Downloading and installing Guacamole client"
wget http://apache.org/dyn/closer.cgi?action=download&filename=guacamole/0.9.14/source/guacamole-client-0.9.14.tar.gz
sudo tar -xzf guacamole-client-0.9.14.tar.gz
sudo cd guacamole-client-0.9.14/
sudo mvn package

#copying Guacamole.war to Tomcat
echo "Copying Guacamole.war to Tomcat"
sudo cp guacamole.war /var/lib/tomcat/webapps

#Restarting everything
sudo /etc/init.d/tomcat7 restart
sudo /etc/init.d/guacd start
