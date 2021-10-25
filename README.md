# DBpedia (docker image) deployment on AWS EC2

Docker CE Install::
1. sudo amazon-linux-extras install docker
2. sudo service docker start
3. sudo usermod -a -G docker ec2-user
4. sudo chkconfig docker on
5. sudo yum install -y git
6. sudo reboot

Docker-compose install::
1. sudo curl -L https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m) -o /usr/local/bin/docker-compose
2. sudo chmod +x /usr/local/bin/docker-compose
3. docker-compose version

Git clone::
1. git clone git@github.com:spmunna/dbpedia.git
2. docker volume create --name=spotlight-models
3. docker-compose -f docker-compose.yml up -d
4. docker-compose -f spotlight-compose.yml stop [to stop]
5. docker stats dbpedia-spotlight.en [to check the stats]
