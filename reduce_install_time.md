#Reduce install time

Installing application on Pepper from Android Studio takes time. It depends on the size of the application, the limitations of ADB and your wifi bandwidth.

There is no magic trick to install an app very quickly but it is possible to reduce the install time by adding the code below in your *build.gradle (Module: app)*

<pre>
splits {
        // Configures multiple APKs based on ABI.
        abi {
            enable true
            reset()
            include "x86", "armeabi-v7a"
            universalApk false
        }
    }
</pre>

This will build your app only for the tablet emulator "x86" and the real one of Pepper "armeabi-v7a", so this will reduce the size of the APK and the install time.

Don't hesitate to share with us if you have other ideas that help to reduce the install time.