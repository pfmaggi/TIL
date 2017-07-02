# React Native boilerplate

## Project creation and dependencies
Once you've installed react-native, starting a new project can be done using the command line utility:

    react-native init <project_name>

then you can enter the folder and start to add the dependencies:

    cd <project_name>
    npm install --save react-redux redux

wanting to use `eslint` could be a good idea to have a rule file, in my case I use the one from an udemy course. My `.eslintrc` file is:

    {
        "extends": "rallycoding"
    }

and this requires to install this `rallycoding` dependency:

    npm install --savedev eslint-config-rallycoding

## Setup FireBase
If we want to connect our react native application to a Firebase backend, it's very easy, first install the dependencies:

    npm install --save firebase

then go to the [firebase console](https://console.firebase.google.com) and setup the backend.