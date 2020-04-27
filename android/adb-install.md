# adb install parameters

List of available parameters that can be used when installing an APK on Android using ADB

Look simple, but there're a lot of options hidden behind the simple:

    adb install

This command pushes an Android application (specified as a full path to an .apk file) to an emulator/device.

    adb install [option] <path>
    adb install test.apk
    adb install -l test.apk forward lock application
    adb install -r test.apk replace existing application
    adb install -t test.apk allow test packages
    adb install -s test.apk install application on sdcard
    adb install -d test.apk allow version code downgrade
    adb install -p test.apk partial application install

To this you can add the usual `-S` parameter to specify the serial number of the target device/emulator
  
[Source](http://adbshell.com/commands/adb-install)