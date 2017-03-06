# Cordova Cheat Sheet

Create a new app

`cordova create hello com.example.hello HelloWorld`

Add a platform

`cordova platform add ios --save`
`cordova platform add android --save`

List platforms

`cordova platform ls`

Check build requirements

`cordova requirements`

Build everything

`cordova build`

Build one platform

`cordova build android`

Emulate the app

`cordova emulate android`

Build for the play store

`cordova build android --release -- --keystore="<key-file>" --storePassword=<password> --alias=<alias>`