### Install and configure Nexus
Git and Nexus serve different purposes in the CI/CD pipeline, and each is designed to address specific needs in the software development lifecycle. Here’s a detailed explanation of why Git cannot replace Nexus in a CI/CD setup:

### Git:
- **Version Control System**: Git is primarily a distributed version control system (DVCS). It is used for tracking changes in the source code during software development.
- **Source Code Management**: Git allows multiple developers to collaborate on the same codebase, managing branches, merging changes, and maintaining the history of code changes.
- **Repositories**: Git repositories store the source code along with its version history.
- **Collaboration and Code Review**: Platforms like GitHub, GitLab, and Bitbucket provide tools for code review, issue tracking, and project management on top of Git repositories.

### Nexus:
- **Artifact Repository**: Nexus is a repository manager that stores, retrieves, and manages binary artifacts created during the build process. This includes compiled code, libraries, dependencies, and other packaged components.
- **Dependency Management**: It handles dependencies for your project. Tools like Maven, Gradle, and npm use Nexus (or other artifact repositories like Artifactory) to download and manage dependencies.
- **Build Artifacts**: Nexus stores build outputs (e.g., JAR files, WAR files, Docker images) that are versioned and can be deployed to different environments.
- **Release Management**: Nexus manages the lifecycle of build artifacts, including snapshot and release versions, ensuring that only tested and approved versions are deployed.

### Key Differences and Use Cases:
1. **Purpose**:
   - **Git** is used for version control of source code.
   - **Nexus** is used for managing build artifacts and dependencies.

2. **Content**:
   - **Git** stores source code and its history.
   - **Nexus** stores compiled binaries, libraries, and other dependencies.

3. **Role in CI/CD**:
   - **Git** is used at the beginning of the CI/CD pipeline to retrieve the latest source code.
   - **Nexus** is used during and after the build process to store and manage the generated artifacts.

4. **Dependency Resolution**:
   - **Git** does not manage project dependencies.
   - **Nexus** provides a central place to store and resolve dependencies, ensuring consistent builds.

5. **Storage and Distribution**:
   - **Git** repositories can become large and unwieldy if used to store binary artifacts.
   - **Nexus** is optimized for storing and distributing large binaries and artifacts efficiently.

### Example Scenario in CI/CD Pipeline:
1. **Source Code Management**:
   - Developers push code to a Git repository.
   
2. **Continuous Integration**:
   - A CI server (e.g., Jenkins, GitLab CI) pulls the latest code from Git, runs tests, and builds the project.

3. **Artifact Management**:
   - The build artifacts (e.g., JAR files, Docker images) are uploaded to Nexus.

4. **Deployment**:
   - Deployment tools pull the necessary artifacts from Nexus to deploy to various environments (e.g., staging, production).

### Conclusion:
Using Git instead of Nexus in a CI/CD pipeline is not feasible because they serve different purposes and are designed to solve different problems in the software development process. Git is essential for source code versioning and collaboration, while Nexus is critical for managing build artifacts and dependencies. Both tools complement each other to create a robust and efficient CI/CD pipeline.

---
Here are some tools similar to Nexus in the market:

1. JFrog Artifactory
2. AWS CodeArtifact
3. GitHub Packages
4. GitLab Package Registry
5. Azure Artifacts
6. Google Artifact Registry
7. Sonatype Repository Manager (Nexus)
8. Bintray (discontinued, previously JFrog Bintray)
9. ProGet
10. Cloudsmith
---
### Install and Configure Nexus
amazon linux

- install java 
   ```sudo yum install java-1.8.0-amazon-corretto-devel```

- create user or continue with default user
- download nexus 
   ```cd /opt
      wget <nexus url> ```
- untar 
- change ownership of nexus ans sonartype repos recursively
- add created/default user to /opt/<nexus>/bin/nexus.rc
- sh nexus start
- with ipa and port 8081

### update in pom file

[Nexus Requirements in the pom.xml](https://www.baeldung.com/maven-deploy-nexus)

```
<distributionManagement>
   <snapshotRepository>
      <id>nexus-snapshots</id>
      <url>http://100.26.170.253:8081/repository/maven-snapshots/</url>
   </snapshotRepository>
   <repository>
      <id>nexus-releases</id>
      <url>http://100.26.170.253:8081/repository/maven-releases/</url>
   <repository>
</distributionManagement>
```

### The Global settings.xml
[The Global settings.xml] (https://www.baeldung.com/maven-deploy-nexus)

in srevers tag
```<server>
      <id>nexus-snapshots</id>
      <username>admin</username>
      <password>Royal#123</password>
   </server>
</servers>
<servers>
   <server>
      <id>nexus-release</id>
      <username>admin</username>
      <password>Royal#123</password>
   </server>
```