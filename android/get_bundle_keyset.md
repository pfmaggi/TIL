# Get the keyset of a bundle object

## intro
In Android a lot of times Bundle objects are used to persist/pass data between different object instances like Activities.  
Most of the times you know the Key you're looking for in the bundle but, sometimes, may be usefull to take a look at the complete keyset.

## code
As an example, getting an intent, then evaluate all the key/value pair received:


        Bundle extras = getIntent().getExtras();
        int iValue = 0;
        String strValue = "";
        if (extras != null) {
            try {
                for (String key : extras.keySet()) {
                    // Check if key is not all lower case and if it is a key of interest
                    if (key.contentEquals("Settings.System.")) {
                        iValue = extras.getInt(key, -1000);
                        if (-1000 != iValue) {
                            android.provider.Settings.System.putInt(getContentResolver(), key, iValue);
                        } else {
                            strValue = extras.getString(key, "ERROR");
                            if (!strValue.equals("ERROR")) {
                                android.provider.Settings.System.putString(getContentResolver(), key, strValue);
                            }
                        }
                    }
                }
            } catch (ClassCastException e) {
                throw(e);
            }
        }
