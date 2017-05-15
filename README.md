# docker-elastic-stack
Configuration for Docker deployment of Elastic stack (former ELK)

#Prerequisites

##1. Install docker CE: https://docs.docker.com/engine/installation/linux/ubuntu/#install-using-the-repository

$ sudo apt-get remove docker docker-engine

$ sudo apt-get update

(optional) $ sudo apt-get install linux-image-extra-$(uname -r) linux-image-extra-virtual

$ sudo apt-get install apt-transport-https ca-certificates curl software-properties-common

$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

$ sudo apt-key fingerprint 0EBFCD88

$ sudo add-apt-repository "deb [arch=armhf] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"

(again !!!)$ sudo apt-get update


$ sudo apt-get install docker-ce
(or specific version) $ sudo apt-get install docker-ce=<VERSION>

$ sudo docker run hello-world



##2. Install docker Compose: https://docs.docker.com/compose/install/

(exit current user) sudo -i

curl -L https://github.com/docker/compose/releases/download/1.13.0/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose

sudo chmod +x /usr/local/bin/docker-compose

exit


##3. Check Prerequisites
$ sudodocker -v
$ sudodocker-compose -v



##Official guidelines:
E https://www.elastic.co/guide/en/elasticsearch/reference/current/docker.html
L https://www.elastic.co/guide/en/logstash/5.4/_pulling_the_image.html
K https://www.elastic.co/guide/en/kibana/5.4/_configuring_kibana_on_docker.html





