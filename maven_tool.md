### built-in life cycle in maven
There are three built-in build lifecycles: default, clean and site. 
- The ***default*** lifecycle handles your project deployment, 
- The ***clean*** lifecycle handles project cleaning,
- The ***site*** lifecycle handles the creation of your project's web site.

in Default lifecycle there seven steps
- **validate** - validate the project is correct and all necessary information is available , validate POM.xml
- **compile** - compile the source code of the project
- **test** - test the compiled source code using a suitable unit testing framework. These tests should not require the code be packaged or deployed
- **package** - take the compiled code and package it in its distributable format, such as a JAR.
- **verify** - run any checks on results of integration tests to ensure quality criteria are met check quality of package.
- **install** - install the package into the local repository, for use as a dependency in other projects locally 
- **deploy** - done in the build environment, copies the final package to the remote repository for sharing with other developers and projects. [jfrog/nexus].

### Repositories in Maven
while package , lot of dependencies , libraries , plugins are required , so that all these dependences are taken maven tool from below order,
There are three kinds of repositories in maven 
- local :- when initially packages has been done, for first time all dependencies downloaded here, how future purpose , check here primarily , if here not found , go for next repository

    **Default location: ~/.m2/repository (on Unix-based systems) or C:\Users\{username}\.m2\repository (on Windows).**
- Remote/private: These are repositories located on remote servers other than the central repository. They can be hosted by third-party organizations or within an organization for internal artifacts.
Remote repositories can be specified in the project's pom.xml file or in the Maven settings.xml file.

    Jfrog/nexus.
- Central/public: from maven website.