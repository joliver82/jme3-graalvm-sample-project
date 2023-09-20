# jme3-graalvm-sample-project

** NOTE: this build uses lwjgl 3.3.3-snapshot instead of 3.3.2 which is the default in jme3.6.1 because this release fails with graalvm

Based in the lwjgl example at https://github.com/chirontt/lwjgl3-helloworld-native
Also mixed gradle stuff from both jme3-sdk new project and jme3 website project initializer

# Buiding and Running

From project folder:
* #export JAVA_HOME=<Where you installed graalvm ce for java11>
* export JAVA_HOME=~/Descargas/graalvm-ce-java11-22.3.2/
* ./gradlew clean
* ./gradlew releaseJar
* ./gradlew nativeCompile
* #Run the game
* ./build/native-image-<OS>/GradleGame

# Working on your own project

Note the content of graalconfig/run0 is the configuration for graalvm. If adding any new library, asset, jni call, reflection usage, etc you may need to manually edit the files hosted there (refer to graalvm documentation) or run the native image agent as follows: 

* cd build/libs
* $JAVA_HOME/bin/java -agentlib:native-image-agent=config-output-dir=../../graalconfig/run0 -jar GradleGame-1.0.jar

Note that you may need to go through all your game to get everything in place

Also you can create multiple folders with different executions and add all in build.gradle, at graalvmNative section -> configurationFileDirectories.from(file("<The desired path>"))

