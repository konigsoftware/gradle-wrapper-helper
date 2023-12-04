# gradle-wrapper-helper

### Motivations:

Typical Gradle projects include a [gradle wrapper](https://docs.gradle.org/current/userguide/gradle_wrapper.html) in the `gradlew` binary file.
Using the wrapper has the following benefits (as described in the official Gradle docs):
- Standardizes a project on a given Gradle version, leading to more reliable and robust builds.
- Provisioning a new Gradle version to different users and execution environment (e.g. IDEs or Continuous Integration servers) is as simple as changing the Wrapper definition.
- Developers can get up and running with a Gradle project quickly without having to follow manual installation processes saving your company time and money.

However, running commands with the Gradle wrapper can be a bit clunky and might encourage your developers to download a local version
of Gradle themselves anyway. If you have the following project directory structure:
```
root:
 gradlew
 some-module:
   some-sub-module:
     even-deeper-submodule:
       src/main/...
       build.gradle
```
Building the `even-deeper-submodule` module with the Gradle wrapper would require running the command `../../../gradlew build`, which is quite verbose and easy to mistype.
If you download a local version of gradle you could simply run `gradle build` instead from the `even-deeper-submodule` directory.

If we could access the Gradle wrapper with commands as simple as the local Gradle version, we would get the best of both worlds. That is what this project attempts to solve.

### Installation:

Clone this repo to any local directory. `cd` into the cloned repository and run `./gw install`. 

If the installation succeeds, you should see `gw install complete!` in the console.

You will need to restart your terminal following installation before usage.

You can feel free to delete the cloned repository after installation has completed, although re-installation will require
re-cloning this repo.

### Usage:

To execute a Gradle task using the Gradle wrapper, simply run `gw [cmd]` from any Gradle project or submodule. If you have the following project directory strucute:
```
root:
 gradlew
 some-module:
   some-sub-module:
     even-deeper-submodule:
       src/main/...
       build.gradle
```
To build the `even-deeper-submodule` you can simply run `gw build` from the `even-deeper-submodule` directory instead of running
`../../../gradlew build`.
