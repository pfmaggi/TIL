# Android's package manager

Here're some package manager commands that I find useful in my day-by-day investigation of the Android operative system

## Package Manager from the shell
You can use the package manager from `adb` shell using the command:

    adb shell pm 

This will print the uage guide for the pm command:

    usage: pm list packages [-f] [-d] [-e] [-s] [-3] [-i] [-u] [--user USER_ID] [FILTER]
       pm list permission-groups
       pm list permissions [-g] [-f] [-d] [-u] [GROUP]
       pm list instrumentation [-f] [TARGET-PACKAGE]
       pm list features
       pm list libraries
       pm list users
       pm path PACKAGE
       :   :   :   :
       :   :   :   :
       pm remove-user: remove the user with the given USER_IDENTIFIER,
         deleting all data associated with that user

The same usage guide can be found in [adb's documentation.](https://developer.android.com/studio/command-line/adb.html#pm)

### Download the apk of an installed application


### Get to know better your Android device

#### What are the known permission?

    pm list permissions

If you happen to run adb on a platform with grep, you can see directly which custom permissions are known on Zebra Technologies devices:

    adb shell pm list permissions -f | grep 'symbol\|zebra' -A 3

Running this on a TC56 with Android v6.0.x I see:


    + permission:com.symbol.osx.proxyframework.permission.BIND_HOMESCREEN_DEFAULT
      package:com.symbol.osx.proxyframework
      label:null
      description:null
      protectionLevel:signature|privileged
    --
    + permission:com.symbol.osx.multiuser.permission.MULTIUSER_STATUS
      package:android
      label:null
      description:null
    --
    + permission:com.symbol.osx.proxyframework.permission.MULTIUSER_CHANGE
      package:com.symbol.osx.proxyframework
      label:null
      description:null
      protectionLevel:signature|privileged
    --
    + permission:com.symbol.permission.NET_RAW
      package:android
      label:null
      description:null
    --
    + permission:com.symbol.osx.proxyframework.permission.BIND_USB_MODE_CHANGES
      package:com.symbol.osx.proxyframework
      label:null
      description:null
      protectionLevel:signature|privileged
    --
    + permission:com.symbol.osx.securestorage.permission.SECURE_STORAGE
      package:com.symbol.osx.securestorage
      label:null
      description:null
      protectionLevel:signature|privileged
    --
    + permission:com.symbol.osx.threatdetectionservice.permission.BIND_THREAT_DETECTION_SERVICE_CONTROL
      package:com.symbol.osx.threatdetectionservice
      label:null
      description:null
      protectionLevel:signature|privileged
    --
    + permission:com.symbol.osx.securitystore.permission.TRUSTED_STORE_MANAGEMENT
      package:android
      label:null
      description:null
    --
    + permission:com.symbol.dataanalytics.permission.MESSAGING
      package:com.symbol.dataanalytics
      label:Data Analytics Messaging.
      description:Can send events to Zebra Data Analytics Engine.
      protectionLevel:signature|privileged
    --
    + permission:com.symbol.datawedge.permission.DWPROFILESETTINGS
      package:com.symbol.datawedge
      label:permission_DWPROFILESETTINGS
      description:null
      protectionLevel:dangerous
    --
    + permission:com.symbol.osx.proxyframework.permission.SETTINGS_CHANGE
      package:com.symbol.osx.proxyframework
      label:null
      description:null
      protectionLevel:signature|privileged
    --
    + permission:com.symbol.permission.ENTERPRISE
      package:android
      label:null
      description:null
    --
    + permission:com.symbol.osx.proxyframework.permission.SETTINGS_HELPER
      package:com.symbol.osx.proxyframework.settingshelper
      label:null
      description:null
      protectionLevel:signature|privileged
    --
    + permission:com.symbol.osx.proxyframework.permission.BIND_DEVICE_ADMIN
      package:com.symbol.osx.proxyframework
      label:null
      description:null
      protectionLevel:signature|privileged
    --
    + permission:com.symbol.osx.proxyframework.permission.BIND_PRIVILEGED_COMMAND_RUNNER
      package:com.symbol.osx.proxyframework
      label:null
      description:null
      protectionLevel:signature|privileged
    --
    + permission:com.symbol.osx.lockservice.permission.LOCKPATTERN
      package:android
      label:null
      description:null
    --
    + permission:com.symbol.osx.proxyframework.permission.BIND_BLUETOOTH_MODE_CHANGES
      package:com.symbol.osx.proxyframework
      label:null
      description:null
      protectionLevel:signature|privileged
    --
    + permission:com.symbol.permission.FUSION_ACCESS
      package:com.symbol.fusionservice
      label:Allows an application to monitor information about the Fusion configuration
      description:Access Fusion configuration
      protectionLevel:normal
    --
    + permission:com.symbol.permission.FUSION_CHANGE
      package:com.symbol.fusionservice
      label:Allows an application to modify information about the Fusion configuration
      description:Change Fusion configuration
      protectionLevel:signature|privileged
    --
    + permission:com.symbol.osx.proxyframework.permission.EVENT_INJECTION_HELPER
      package:com.symbol.osx.proxyframework.helper
      label:null
      description:null
      protectionLevel:signature|privileged
    --
    + permission:com.symbol.osx.proxyframework.permission.MXADDONSERVICE_CONTROL
      package:com.symbol.osx.proxyframework
      label:null
      description:null
      protectionLevel:signature|privileged
    --
    + permission:com.symbol.osx.proxyframework.permission.APP_LOCKOUT
      package:com.symbol.osx.proxyframework
      label:null
      description:null
      protectionLevel:signature|privileged
    --
    + permission:com.symbol.mxmf.ACCESS_MX_MANAGEMENT_FRAMEWORK_SERVICE
      package:com.symbol.mxmf
      label:MX Management Framework Permission
      description:Allow an application to access MX Management Framework
      protectionLevel:normal
    --
    + permission:com.symbol.osx.proxyframework.permission.THREATDETECTIONSERVICE_CONTROL
      package:com.symbol.osx.proxyframework
      label:null
      description:null
      protectionLevel:signature|privileged
    --
    + permission:com.symbol.permission.REMOTESERVICE_KEYEVENT
      package:android
      label:null
      description:null
    --
    + permission:com.symbol.permission.GPS
      package:android
      label:null
      description:null
    --
    + permission:com.symbol.osx.proxyframework.permission.BIND_CONNECTIVITY_SETTINGS_CHANGES
      package:com.symbol.osx.proxyframework
      label:null
      description:null
      protectionLevel:signature|privileged
    --
    + permission:com.symbol.osx.proxyframework.settingsparser.permission.SEND_PARSE_ACTION
      package:com.symbol.osx.proxyframework.settingsparser
      label:null
      description:null
      protectionLevel:signature|privileged
    --
    + permission:com.symbol.osx.securitystore.permission.KEYSTORE_ACCESS
      package:android
      label:null
      description:null
    --
    + permission:com.symbol.osx.securitystore.permission.KEYSTORE_CHANGE
      package:android
      label:null
      description:null
    --
    + permission:com.symbol.osx.proxyframework.permission.BIND_CERT_INSTALL_UNINSTALL
      package:com.symbol.osx.proxyframework
      label:null
      description:null
      protectionLevel:signature|privileged
    --
    + permission:com.symbol.datawedge.permission.DWSETTINGS
      package:com.symbol.datawedge
      label:permission_DWSETTINGS
      description:null
      protectionLevel:dangerous
    --
    + permission:com.symbol.osx.mxaddonservice.permission.MXADDONSERVICE_CONTROL
      package:android
      label:null
      description:null
    --
    + permission:com.symbol.permission.FOREGROUND_NOTIFICATON
      package:android
      label:null
      description:null
    --
    + permission:com.symbol.osx.proxyframework.permission.EVENT_INJECTION
      package:com.symbol.osx.proxyframework
      label:null
      description:null
      protectionLevel:signature|privileged
    --
    + permission:com.symbol.permission.RECOVERY_STATUS
      package:android
      label:null
      description:null
    --
    + permission:com.symbol.osx.applist.permission.APP_LIST_MANAGEMENT
      package:android
      label:null
      description:null
    --
    + permission:com.symbol.permission.FUSION_PRIVATE
      package:com.symbol.fusionservice
      label:Allows an application to modify information about the Fusion configuration
      description:Change Fusion configuration
      protectionLevel:signature|privileged
    --
    + permission:com.symbol.dataanalytics.permission.ANALYTICS_ENGINE_SERVICE
      package:com.symbol.dataanalytics
      label:Data Analytics Engine.
      description:Can start the core analytics engine serivce.
      protectionLevel:signature|privileged
    --
    + permission:com.symbol.osx.proxyframework.permission.BIND_APP_INSTALL_UNINSTALL
      package:com.symbol.osx.proxyframework
      label:null
      description:null
      protectionLevel:signature|privileged
    --
    + permission:com.zebra.scandemo.permission.C2D_MESSAGE
      package:com.zebra.scandemo
      label:null
      description:null
      protectionLevel:signature
    --
    + permission:com.symbol.emdk.permission.EMDK
      package:com.symbol.emdk.emdkservice
      label:emdk_permission
      description:null
      protectionLevel:normal
    --
    + permission:com.symbol.osx.multiuser.permission.MULTIUSER_CHANGE
      package:android
      label:null
      description:null
    --
    + permission:com.symbol.osx.proxyframework.permission.BIND_SYSTEM_INFO_REPORTING
      package:com.symbol.osx.proxyframework
      label:null
      description:null
      protectionLevel:signature|privileged
    --
    + permission:com.symbol.zebravolumecontrol.permission.ZVC_PROVIDER
      package:com.symbol.zebravolumecontrol
      label:null
      description:null
      protectionLevel:signature

## Package Manager from your app code
