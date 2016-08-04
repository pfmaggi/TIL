# Gradle properties file

It is possible to keep private information of a project (as for example API KEY) out of the project source code (and so out of the code repository), using the gradle property file.

This is really down to create a `~/.gradle/gradle.property` file and put there the information we need in our project but we cannot commit to a repository.

The we can retrieve the information using some gradle magic.  
As an example:

Starting with this information in the `gradle.properties` file:

    MyOpenWeatherMapApiKey="1c3ae96f93a0094e8a7chsjdgfid04aed3f1"
   
And then in `build.gradle(module:app)` we add the following lines:

    buildTypes.each {
            it.buildConfigField 'String', 'OPEN_WEATHER_MAP_API_KEY', MyOpenWeatherMapApiKey
    }
    
So, in my main program we can access the data using the `BuildConfig` object:
                  
    final String FORECAST_BASE_URL = "http://api.openweathermap.org/data/2.5/forecast/daily?";
    final String QUERY_PARAM = "q";
    final String FORMAT_PARAM = "mode";
    final String UNITS_PARAM = "units";
    final String DAYS_PARAM = "cnt";
    final String APPID_PARAM = "APPID";
    Uri builtUri = Uri.parse(FORECAST_BASE_URL).buildUpon()
        .appendQueryParameter(QUERY_PARAM, params[0])
        .appendQueryParameter(FORMAT_PARAM, format)
        .appendQueryParameter(UNITS_PARAM, units)
        .appendQueryParameter(DAYS_PARAM, Integer.toString(numDays))
        .appendQueryParameter(APPID_PARAM, BuildConfig.OPEN_WEATHER_MAP_API_KEY)
        .build();
        
    URL url = new URL(builtUri.toString());

  
[Source](http://stackoverflow.com/questions/35722904/saving-the-api-key-in-gradle-properties)
