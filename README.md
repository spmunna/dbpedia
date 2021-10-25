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

Steps::
1. git clone git@github.com:spmunna/dbpedia.git
2. docker volume create --name=spotlight-models
3. docker-compose -f docker-compose.yml up -d
4. docker-compose -f spotlight-compose.yml stop [to stop]
5. docker stats dbpedia-spotlight.en [to check the stats]
6. docker logs dbpedia-spotlight.en [to check the logs]

Example Curl commands:
1. To get JSON output >> 
curl http://localhost:2222/rest/annotate \
    --data-urlencode "text=President Obama called Wednesday on Congress to extend a tax break for students included in last year's economic stimulus package, arguing that the policy provides more generous assistance." \
    --data "confidence=0.35" \
    -H "Accept: application/json"
    
 2. To get Turtle/NIF output >> 
curl http://localhost:2222/rest/annotate \
    --data-urlencode "text=President Obama called Wednesday on Congress to extend a tax break for students included in last year's economic stimulus package, arguing that the policy provides more generous assistance." \
    --data "confidence=0.35" \
    -H "Accept: text/turtle"
  
