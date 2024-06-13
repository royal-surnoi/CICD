pipeline{
    agent any
    tools{
        maven 'maven-3.9.7'
    }
    environment{
        registry ='975050127850.dkr.ecr.us-east-1.amazonaws.com/mysampleproject'
        registryCredential='aws-access'
        dockerimage = ''
    }
    stages{
        stage('checkout project'){
            steps{
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'git-creds', url: 'https://github.com/royal-surnoi/springboot-maven-micro.git']])
            }
        }
        stage('Build and package'){
            steps{
                sh 'mvn clean validate package'
            }
        }
        stage("SonarQube analysis") {
          steps {
                     script{
            		     withSonarQubeEnv(installationName: 'sonar-10.5.1', credentialsId: 'sonar-access') {
            		     sh 'mvn sonar:sonar'
    	    	}
    	    	 timeout(time: 1, unit: 'HOURS') {
                      def qg = waitForQualityGate()
                      if (qg.status != 'OK') {
                          error "Pipeline aborted due to quality gate failure: ${qg.status}"
              }
          }
          }
      }
    }
        stage('Building our image') {
                steps{
                        script {
                        dockerImage = docker.build registry + ":$BUILD_NUMBER"
                        }
                    }
            }
        stage ('Deploy the Image to Amazon ECR') {
           steps {
               script {
               docker.withRegistry("http://" + registry, "ecr:us-east-1:" + registryCredential ) {
               dockerImage.push()
         }
               }
           }
        
    }
}
post {
        success {
            mail bcc: '', body: 'Pipeline build successfully', cc: '', from: 'iamroyalreddy@gmail.com', replyTo: '', subject: 'The Pipeline success', to: 'manu.nandelli@gmail.com'
        }
        failure {  
            mail bcc: '', body: 'Pipeline build not success', cc: '', from: 'iamroyalreddy@gmail.com', replyTo: '', subject: 'The Pipeline failed', to: 'manu.nandelli@gmail.com'
         } 
}
}