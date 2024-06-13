### pre-requists 
- install java - amazon-linux

  ```sudo yum install java-17-amazon-corretto-headless```

- java version 
  ```java --version```

### maven tool
- check index of maven and select latest version in index
  from binaries 
  source : https://archive.apache.org/dist/maven/maven-3/

  ```wget https://archive.apache.org/dist/maven/maven-3/3.9.7/binaries/apache-maven-3.9.7-bin.tar.gz -d /opt```

- untar file in /opt location 
  ```tar -xvf apache-maven-3.9.7-bin.tar.gz```

- export path of maven file address envs
  ```export PATH=$PATH:/opt/apache-maven-3.9.7/bin```

- maven version 
  ```mvn --version```

### clone source code repository 
- ```git clone <URL>```

### to run mvn stages
- ```mvn validate```
- ```mvn clean```
- ```mvn package```

### to run package
- ```java -jar <package>```