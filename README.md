# artifactory-plugin
A plugin for uploading gradle artifacts to artifactory

Since the offical artifactory plugin is so hard to configure, I created this plugin to upload artifacts based on their rest api.

##Example use in gradle build script
``` groovy
artifactory{
  folder "foo"
  url = "http://<artifactoryServer>:<PORT>/artifactory" //the url of artifactory
  repository = "rdc-snapshots" //which repository to upload to
  username = "${artifactory_username}" //the user to authenticate with. Property should be located in your private gradle properties file (~/.gradle/gradle.properies)
  password = "${artifactory_password}" //password of the user. Property should be located in your private gradle properties file (~/.gradle/gradle.properies)
}
```

##Adding more artifacts to be uploaded
``` groovy
task myJar(type: Jar)

artifacts {
    archives myJar //register the output of the myJar task as an artifact. All registered artifacts are automatically uploaded.
}
```