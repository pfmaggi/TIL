# Using Android local.properties file

In Android Studio every project contains a local.properties file with at least a couple of path for Android SDK and Android NDK.

Given that I usually have in my build.gradle file a reference to Zebra's EMDK, look like a good idea to use this properties instead than hardcodig the path (like I've done for a too much long time).

So, my gradle files now includes:

    Properties properties = new Properties()
    properties.load(project.rootProject.file('local.properties').newDataInputStream())
    def sdkDir = properties.getProperty('sdk.dir')

so that I can the use the `sdkDir` variable like:

        provided fileTree(include: ['com.symbol.emdk.jar'], dir: sdkDir+'/add-ons/addon-symbol_emdk-symbol-19/libs/')

Much cleaner and nice :-)