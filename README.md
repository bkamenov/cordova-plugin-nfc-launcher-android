# cordova-plugin-nfc-launcher-android

This plugin will add a new intent to your main Cordova's Andoid activity so your app will launch when a NDEF record with the MIME type scpecified has been read.



## Installation:

For stable relases type:

```shell
cordova plugin add cordova-plugin-nfc-launcher-android --variable MIME_TYPE="text/plain"
```

For latest releases type:

```shell
cordova plugin add https://github.com/bkamenov/cordova-plugin-nfc-launcher-android --variable MIME_TYPE="text/plain"
```



The variable **MIME_TYPE** should be provided upon instalation and should contain the MIME type of the NDEF message which will trigger you app.



**IMPORTANT:** The plugin modifies only the AndroidManifest.xml file and therefore it has no code to be used.



**NOTE:** Normally, Cordova creates the main activity for Android with **launchMode="singleTop"**. However, this is **NOT** sufficient to prevent the second instance of your activity. Furthermore, you want your NDEF message to be fetched by your **onNewIntent** callback, as the plugin [cordova-plugin-nfc-android](https://github.com/bkamenov/cordova-plugin-nfc-android.git) does. The launch mode should be set to **launchMode="singleTask"**. This will create only one instance of the app, or reuse it, if it alredy runs in the background. Because of a bug in the <edit-config>, in plugin.xml  we cannot have two edits of the activity tag in the manifest file. Therefore, the only solution is to add to your **config.xml** following lines in the Android platform:

```xml
<!-- This will disallow second instance to be created and all backgroud scans will be redirected to activity's onNewIntent override -->
<edit-config file="AndroidManifest.xml" mode="merge" target="/manifest/application/activity">
  <activity android:launchMode="singleTask"/>
</edit-config>
```



If you like my work and want more nice plugins, you can get me a [beer or stake](https://www.paypal.com/donate/?business=RXTV6JES35UQW&amount=5&no_recurring=0&item_name=Let+me+create+more+inspiring+Cordova+plugins.&currency_code=EUR).




















































