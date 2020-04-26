# Google Chrome for Android supports launching other application through Intents

Taken from [Chrome for Android documentation](https://developer.chrome.com/multidevice/android/intents).

## Syntax

The best practice is to construct an intent anchor and embed that into the page so the user can launch the app. This gives you a lot more flexibility in controlling how apps are launched, including the ability to pass extra information into the app via Intent Extras.

The basic syntax for an intent-based URI is as follows:

intent:
   HOST/URI-path // Optional host
   #Intent;
      package=[string];
      action=[string];
      category=[string];
      component=[string];
      scheme=[string];
   end;

See the [Android source](https://code.google.com/p/android-source-browsing/source/browse/core/java/android/content/Intent.java?repo=platform--frameworks--base#6514) for parsing details.

## Considerations

If the activity you invoke via an intent contains [extras(http://developer.android.com/guide/components/intents-filters.html#extras)], you can include these as well.

Only activities that have the category filter, `android.intent.category.BROWSABLE` are able to be invoked using this method as it indicates that the application is safe to open from the Browser.
