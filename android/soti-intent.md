# SOTI allows to send and intent from the script
As you can find on SOTI documentation, there's a [nice support in the scripting language](https://www.soti.net/mc/help/v13/en/Content/ScriptCmdSet.htm).

Then I got a request on how to send this indent:

    am start -n com.zebra.customupdater/.UpdaterActivity --es "package" "/storage/sdcard1/SPR31256.zip" it works

This became:
    
    sendintent -a "intent :x Intent;action=android.intent.action.MAIN;component=com.zebra.customupdater/.UpdaterActivity;S.package=/storage/sdcard1/SPR31256.zip;end;"
    