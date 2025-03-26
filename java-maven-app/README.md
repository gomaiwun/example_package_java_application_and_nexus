 ##### User Credential configuration for maven project
In order to use the nexus repository, you need to configure the user credentials in the `~/.m2/settings.xml` file. The following is an example of the `settings.xml` file:

```xml
<settings>
  <servers>
    <server>
      <id>nexus-releases</id>
      <username>admin</username>
      <password>admin123</password>
    </server>
    <server>
      <id>nexus-snapshots</id>
      <username>admin</username>
      <password>admin123</password>
    </server>
  </servers>
</settings>
```

The `id` tag is the id of the server in the `pom.xml` file. The `username` and `password` are the credentials to access the nexus repository. The `nexus-releases` id is used to deploy the release version of the project, and the `nexus-snapshots` id is used to deploy the snapshot version of the project.

##### To package the project
To package the project, you need to run the following command:

```bash
mvn package
```


##### Deploy the project to the nexus repository
To deploy the project to the nexus repository, you need to run the following command:

```bash
mvn deploy
```

##### Build the project
To build the project, you need to run the following command:

```bash
mvn clean install
```

##### Download Artifacts from Nexus Repository
To download the artifacts from the nexus repository, you need to run the following command:

```bash
mvn dependency:get -Dartifact=groupId:artifactId:version
```


##### Notes about the nexus api
The nexus api is a RESTful api that allows you to interact with the nexus repository. You can use the api to upload, download, and delete artifacts from the nexus repository. The api is documented in the nexus repository manager documentation.