# FAQ

## Development
### Why did you not implement the extension with Kotlin?
If implemented with Kotlin we'd need to bundle the Kotlin runtime libraries which would increase the size. Therefore we stay with Java. However, this does not prevent you from implementing your application with Kotlin and still use this extension.

### Why are you not using Lombok?
We're not depending on the Lombok to simplify the setup of the development environment - otherwise this would require a plugin for the IDE.

### What about warnings regarding illegal reflective access operations?
When starting the application you will see:
```
WARNING: An illegal reflective access operation has occurred
WARNING: Illegal reflective access by org.apache.ibatis.reflection.Reflector (file:/home/tos/.m2/repository/org/mybatis/mybatis/3.4.4/mybatis-3.4.4.jar) to method java.lang.Object.finalize()
WARNING: Please consider reporting this to the maintainers of org.apache.ibatis.reflection.Reflector
WARNING: Use --illegal-access=warn to enable warnings of further illegal reflective access operations
WARNING: All illegal access operations will be denied in a future release
```
This warning is shown when using JDK 9 and later. It will need to be fixed by MyBatis.

### How do I create and publish a new release?

1. Trigger the release
   1. Open https://github.com/NovatecConsulting/micronaut-camunda-bpm/releases
   2. Click "Draft a new release"
   3. Enter a tag version of the master branch, e.g. v0.1.0 considering the last tag and https://semver.org/
   4. Click on "Publish release"
2. Verify that version is built and uploaded to OSSRH successfully
   1. Open https://github.com/NovatecConsulting/micronaut-camunda-bpm/actions?query=workflow%3A%22Publish+to+OSSRH+when+released%22
   2. Wait for build to succeed
3. Publish to Maven Central (see also [Detailed instructions](https://central.sonatype.org/pages/releasing-the-deployment.html))
   1. Open https://oss.sonatype.org/#stagingRepositories
   2. Start verification by selecting the repository and clicking on "Close"
   3. Wait a few minutes and click on "Refresh" for the status to update
   4. Release version to Maven Central by selecting the repository and clicking on "Release"
4. Check Maven Central
   1. The new release should appear on https://search.maven.org/search?q=micronaut-camunda-bpm-feature after a few minutes
   2. Update README.md to include the new version of the dependency for Gradle and Maven.
   3. That's all :-) There is no need to update the version in the project. It will stay at 0.0.1-SNAPSHOT.
