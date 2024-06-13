### CI server configuration 
AMI: Amazon-linux
Instance-Type: t2.medium

- install java 8 
- install maven
- install git and clone code
- mvn clean validate package
- install docker

---
Sonarqube-server
AMI: Ubuntu
Instance-Type: t2.medium

- install java 8 
- install sonarqube install and configure

---
### sonar installation 
[sonar-config](https://mantratech.hashnode.dev/how-to-install-sonarqube-on-ubuntu)

### add plugin od sonarqube
<plugin>
        <groupId>org.sonarsource.scanner.maven</groupId>
        <artifactId>sonar-maven-plugin</artifactId>
        <version>3.7.0.1746</version>
</plugin>
in version need update by recent sonar scanner version

- generate access token of sonarqube 

### to integrate sonarqube with maven
- need to generate token for intergration 
- run the below command 
    ```mvn sonar:sonar -Dsonar.host.url=http://<IP>:9000 -Dsonar.login=<token>```

### Create ECR repos in aws and Create IAM role and attached CI server along wit that and excutet ECR - instruction command in scr repository
---
### Create CD-server 
AMI: Ubuntu
Instance-Type: t2.micro

- Install Docker 
- Install AWSCLI 
- excute ECR first command but before need to add
IAM role to CD server

---
### docker commands for next execution
- ```docker container run --name=demodatarepo -p 8088:8080 --detach 975050127850.dkr.ecr.us-east-1.amazonaws.com/demodatarepo:latest```

- ```docker container ls```
- ```docker ps```

- ```docker image ls```
---
###
http://<IP>:8080/couse-svc/getAllDevopsTools

couse-svc: check in src main/resouces/application