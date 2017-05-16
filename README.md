# docker-elastic-stack
Configuration for Docker deployment of Elastic stack (former ELK)

# Prerequisites

## 1. Install docker CE: https://docs.docker.com/engine/installation/linux/ubuntu/#install-using-the-repository

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



## 2. Install docker Compose: https://docs.docker.com/compose/install/

(exit current user) $ sudo -i

$ curl -L https://github.com/docker/compose/releases/download/1.13.0/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose

$ sudo chmod +x /usr/local/bin/docker-compose

$ sudo exit


## 3. Check Prerequisites

$ sudo docker -v

$ sudo docker-compose -v


## 4. Clone this git repository

$ sudo git clone https://github.com/Poort80/docker-elastic-stack.git ~/p80-docker-elastic-stack


## 5. Run docker-compose in detached mode

$ cd ~/p80-docker-elastic-stack

$ sudo docker-compose up -d

(optionally inject log files for Logstash) $ sudo nc localhost 5000 < /path/to/logfile.log

By default, the stack exposes the following ports:

5000: Logstash TCP input.
9200: Elasticsearch HTTP
9300: Elasticsearch TCP transport
5601: Kibana


## 6. Check if containers are running

$ sudo docker ps -a

Kibana should be available in web browser: http://localhost:5601 locally or http://your-project-name.lan.p80.nl:5601


## Official guidelines

https://www.elastic.co/guide/en/elasticsearch/reference/current/docker.html
https://www.elastic.co/guide/en/logstash/5.4/_pulling_the_image.html
https://www.elastic.co/guide/en/kibana/5.4/_configuring_kibana_on_docker.html


## Community guidelines

https://thepracticalsysadmin.com/elk-5-on-docker/

https://github.com/jmreicha/elk-docker/
https://github.com/deviantony/docker-elk

https://elk-docker.readthedocs.io/
https://github.com/spujadas/elk-docker
https://hub.docker.com/r/sebp/elk/~/dockerfile/


## Override for specific project

Every P80 project could have it's own Git repository with custom overrides for docker-compose.yml

If provided the file 'docker-compose.override.yml' will be automatically used by docker-compose according as described: https://docs.docker.com/compose/extends/#example-use-case

Moreover, we can speficy custom overrides (i.e. Production-like) by adding custom files:

'docker-compose.<environment>.yml' and then inject them as follows:

$ sudo docker-compose -f docker-compose.yml -f docker-compose.<environment>.yml up -d


