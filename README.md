


JenkinsAdmin
HOSTNAME-DNS: ec2-52-88-230-11.us-west-2.compute.amazonaws.com
IP: 52.88.230.11

wget -q -O - http://pkg.jenkins-ci.org/debian/jenkins-ci.org.key | sudo apt-key add -
 echo "deb http://pkg.jenkins-ci.org/debian binary/" | sudo tee -a /etc/apt/sources.list.d/jenkins.list

sudo apt-get update
sudo apt-get install jenkins

ps -ef | grep jenkins


sudo apt-get install apache2

sudo a2enmod proxy
sudo a2enmod proxy_http

sudo vim /etc/apache2/sites-available/jenkins.conf


<virtualHost *:80>
        ServerName HOSTNAME*
        ProxyRequests Off
        <Proxy *>
                Order deny,allow
                Allow from all
        </Proxy>
        ProxyPreserveHost on
        ProxyPass / http://localhost:8080/

</VirtualHost>



ps -ef |grep apache
sudo a2ensite jenkins
sudo service apache2 reload
ps -ef |grep jenkins



/usr/lib/jvm/java-7-oracle/bin/javac
/usr/share/maven/bin/mvn
/usr/bin/git
