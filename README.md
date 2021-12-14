# Apache2
Storing Apache2 Logs

# Step1: Installing Apache2 server:

  <p>
  
    sudo apt update

    sudo apt install apache2

    sudo echo "ServerName localhost" >> /etc/apache2/apache2.conf

    sudo nano /etc/apache2/ports.conf # replace the Listen 80 with the 8079

    sudo service apache2 start
   </p>

# Step2: Writing a bash script that checks the APACHE2 servers logs and compres them

<p>
  
    nano apache2_log_compress.bash
    
</p>

  <h6>
    
        #!/bin/bash
        compress () {
                if [ "$(wc -l < $1)" -ge 20 ]
                then
                        DATE=`date +%d-%m-%y_%H-%M-%S`
                        sudo gzip -S "_$DATE.gz" $1
                fi

        }

        go_directory () {
                if [ -d "/var/log/apache2" ]
                then
                        if [ -f  "$1" ]
                        then
                                compress $1
                        fi
                fi
        }

        go_directory "/var/log/apache2/access.log"
        go_directory "/var/log/apache2/error.log"
        go_directory "/var/log/apache2/other_vhosts_access.log"
  </h6>
                  
 <p>  
                  
    sudo chmod 764 apache2_log_compress.bash
                  
</p>            
                  
                  
                  
                  
                  
                  
                  
                  
                  
                  
