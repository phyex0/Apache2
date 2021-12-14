# Apache2
Storing Apache2 Logs

Step1: Installing Apache2 server:

<p>
  sudo apt update
  sudo apt install apache2
  sudo echo "ServerName localhost" >> /etc/apache2/apache2.conf
  sudo nano /etc/apache2/ports.conf # replace the Listen 80 with the 8079
  sudo service apache2 start
 </p>
