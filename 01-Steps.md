- CI server
    - configuration 
        - java 
        - maven
        - Install Jenkins
        - Docker 
        - git 
    - checkout and build project

- Sonarqube server
    - docker install
    - pull sonarqube image
    - map ports and run it 
    - Install plugin and add sonar login Credentials on jenkins Server
    - Add SonarQube to jenkins
    - Pipeline for SonarQube Scanner for Jenkins 
    - Pipeline for success or aborted due to quality gate failure
    - Configure a webhook in your SonarQube Server
        
        ***Real-time Quality Gate Status Feedback:
            A webhook allows SonarQube to send immediate notifications to Jenkins (or another CI/CD tool) when the analysis of a project is complete. This enables Jenkins to react based on the quality gate status (pass or fail) without polling SonarQube for updates.***
    - Add stage in pipeline to create a docker Image using DockerFile
    - Add Plugins - CloudBees AWS, ECR, Docker etc.
    - Add stage in pipeline to Push the Docker Image to AWS ECR
    - Configure SES to send Email Notification
    - Integrate SES with Jenkins using pipeline
    - Receive an Email Notification after the success or failure of Jenkins Pipeline

- CD server
    - Configure a CD Server using Ubuntu Server
    - Install packages on CD Server
        - docker
        - aws CLI
    - establish a connection from CD Server to AWS ECR
    - pull the image from ECR to CD Server
    - run the Container using the Docker Image
    - Access the Springboot Application running on CD Server

