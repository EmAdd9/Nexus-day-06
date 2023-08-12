## Maven Deploy to Nexus

To deploy artifacts to Nexus Repository Manager using a Jenkins Pipeline, you can utilize the following Groovy script as an example:

```groovy
stage("Maven Deploy to Nexus") {
    steps {
        configFileProvider([configFile(fileId: '1812d04d-4ec8-4ca0-8160-81ab8707c458', variable: 'mavensettings')]) {
            sh "mvn -s $mavensettings clean deploy -DskipTest=true"
        }
    }
}
```

This script outlines the process of deploying artifacts using Maven to the Nexus repository. Here's what the script does step by step:

1. `stage("Maven Deploy to Nexus")`: Defines a pipeline stage named "Maven Deploy to Nexus."

2. `steps`: Encompasses the actions to be executed within this stage.

3. `configFileProvider`: Utilizes the `configFileProvider` plugin to access the `settings.xml` configuration file for Maven.

4. `sh "mvn -s $mavensettings clean deploy -DskipTest=true"`: Executes a shell command (`sh`) to run the Maven deploy command. The `-s $mavensettings` flag specifies the path to the provided `settings.xml` configuration. The `clean deploy` flags indicate a clean build and deployment, and `-DskipTest=true` skips running tests during the deployment process.

By incorporating this Groovy script into your Jenkins Pipeline, you can automate the process of deploying artifacts to Nexus Repository Manager. Make sure to replace the `fileId` in the `configFileProvider` block with the actual fileId corresponding to your `settings.xml` configuration.
