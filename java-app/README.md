##### build the project

    gradle build

##### push the application to the nexus repository

    gradle publish 

##### run the application

    gradle run

##### test the application

    gradle test

##### clean the project

    gradle clean

##### generate the javadoc

    gradle javadoc

# How to authenticate to the nexus artifact repository

In order to use the nexus repository, create a `gradle.properties` file with the content of your nexus user credentials. The following is an example of the `gradle.properties` file:

```properties
repoUser = *******
repoPassword = ******
```