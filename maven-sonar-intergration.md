### sonar installation 
[sonar-config](https://mantratech.hashnode.dev/how-to-install-sonarqube-on-ubuntu)

### add plugin od sonarqube
<plugin>
        <groupId>org.sonarsource.scanner.maven</groupId>
        <artifactId>sonar-maven-plugin</artifactId>
        <version>3.7.0.1746</version>
</plugin>
in version need update by recent sonar scanner version

### to integrate sonarqube with maven
- need to generate token for intergration 
- run the below command 
    ```mvn sonar:sonar -Dsonar.host.url=http://<IP>:9000 -Dsonar.login=<token>```