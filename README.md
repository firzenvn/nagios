# run nagios in docker container
docker run -dit --name nagios4 --restart=unless-stopped -v /data/nagios/etc/:/opt/nagios/etc/ -p 0.0.0.0:8888:80 jasonrivers/nagios:latest

# install nrpe on remote servers
sudo apt-get install nagios-nrpe-server nagios-plugins

# config allowed_hosts for nrpe: /etc/nagios/nrpe.cfg
allowed_hosts=127.0.0.1, 192.168.1.100

# restart nrpe agent
/etc/init.d/nagios-nrpe-server restart
