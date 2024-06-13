### Jenkins
Jenkins is an open-source automation server that helps in building, testing, and deploying software projects automatically. Here's a simple breakdown of what it is and its benefits:

### What is Jenkins?
- **Automation Server**: Jenkins automates repetitive tasks in the software development process.
- **Integration**: It integrates with many tools and platforms, supporting various stages of development.
- **Continuous Integration (CI) and Continuous Delivery (CD)**: Jenkins is often used to implement CI/CD practices, where code changes are automatically tested and deployed.

### Benefits of Jenkins:
1. **Efficiency**: Automates repetitive tasks, saving developers time and effort.
2. **Consistency**: Ensures consistent build and deployment processes, reducing human error.
3. **Faster Feedback**: Provides quick feedback on code changes, allowing for faster identification and fixing of issues.
4. **Scalability**: Can handle multiple projects and pipelines simultaneously, making it suitable for large teams and organizations.
5. **Flexibility**: Supports a wide range of plugins, making it adaptable to various needs and tools.
6. **Open Source**: Free to use and has a large community for support and development.

In summary, Jenkins helps teams deliver software more efficiently and reliably by automating parts of the development process.

---
# Integrating jenkins with git
<img src="/home/lenovo/Desktop/Learning/Udemy/CICD/pictures/Screenshot from 2024-06-02 05-55-46.png">

---
### Install of jenkins, java Maven and Git 
AMI: Amazon Linux

Instance type : t2.medium

- install git
- install java 1.8.0
- install maven 
- install jenkins fom official website 
    - long term support release 
    - repo file is going to copy here cd /etc/yum.repos.d/
    - gpg check.
    - amazon-linux-extras install epel.
    - enable port 8080.
    - connect with ip
    - login with default password
    - just go through prompt
    user:admin
    pw:admin123
---
### Configure github credentials and mavan on jenkins
- github configure in jenkins
    - manage-jenkins -> security-Manage credentials -> jekins-global credentials -> username&Pass -> provide github credentials 
- Location maven provide
    - manage-jenkins -> global tool configuration -> maven -> provide maven home path
---
### create & build project the java based project using maven tool(Freestyle)
    - create new item    with name of project name -> description -> SCM -> git -> repo URL -> shikhar82/springboot-webapplication -> select credentials -> branch (check main/master) -> Build Environment -> Add timestamp to the console output ->maven version -> clean package goals  -> build now
---
### Adding maven plugin in jenkins
- Plugin maven Manage jenkins -> Manage plugins -> install maven integration -> new item -> name -> select maven project -> description -> git -> repo URL -> shikhar82/springboot-webapplication -> select credentials -> branch (check main/master) -> Build -> goal -> clean install -> save -> build it

- check in maven workspace in maven jen kins server 