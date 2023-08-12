## Nexus Repository Configuration in POM and settings.xml

To seamlessly integrate your project with Nexus Repository Manager, follow these steps to configure your `pom.xml` and `settings.xml` files.

### Configure distributionManagement in pom.xml

Add the following configuration to your `pom.xml` file under the `<distributionManagement>` section. Replace the Nexus server URL (`http://52.66.98.156:8081/repository/maven-releases/`) with your team's actual Nexus server URL:

```xml
<distributionManagement>
  <repository>
    <id>maven-releases</id>
    <url>http://52.66.98.156:8081/repository/maven-releases/</url>
  </repository>
  <snapshotRepository>
    <id>maven-snapshots</id>
    <url>http://52.66.98.156:8081/repository/maven-releases/</url>
  </snapshotRepository>
</distributionManagement>
```

Additionally, include the following `<repository>` element outside the `<distributionManagement>` section in your `pom.xml`:

```xml
<repository>
  <id>maven-releases</id>
  <name>maven-releases</name>
  <url>http://52.66.98.156:8081/repository/maven-releases/</url>
</repository>
```

### Configure Nexus Authentication in settings.xml

To authenticate with Nexus using a `settings.xml` file, add the following configuration inside the `<servers>` section. Replace `your-username` and `your-password` with your Nexus credentials:

```xml
<settings>
  <servers>
    <server>
      <id>nexus-releases</id>
      <username>your-username</username>
      <password>your-password</password>
    </server>
    <server>
      <id>nexus-snapshots</id>
      <username>your-username</username>
      <password>your-password</password>
    </server>
  </servers>
</settings>
```

Make sure to include the `settings.xml` file in the appropriate location on your system.

### Deploy Using Maven Commands

For deploying with Maven on Linux, execute the following command:

```shell
mvn clean deploy
```

### Deploy Using Jenkins Pipeline

In your Jenkins Pipeline, you can use the following configuration to leverage the `settings.xml` file for Maven deployment:

```groovy
configFileProvider([configFile(fileId: '1c322f97-3d77-4302-abe0-7dd0d866eab0', variable: 'mavensettings')]) {
  sh "mvn -s $mavensettings clean deploy -DskipTests=true"
}
```

Ensure that you replace `'1c322f97-3d77-4302-abe0-7dd0d866eab0'` with the actual fileId corresponding to your `settings.xml` configuration.

By following these steps, you'll effectively configure your project to deploy artifacts to your Nexus repository using both the `pom.xml` configuration and the `settings.xml` authentication for Maven.
