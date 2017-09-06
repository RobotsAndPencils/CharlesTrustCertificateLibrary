# Charles
An android library to trust user installed CA certificates (e.g. the Charles Root Certificate).

# Synopsis
The cleaner solution to share Charles proxy settings is to create a classless android library with an android manifest and network security config file.

I did create a groovy plugin to apply to any app build.gradle file.  The resulting logic would modify all the app project files to integrate the Charles proxy settings.

However, the integration of an android library is much simpler.  Then, the bulk of the integration work can be left to Android Studio.

# Details

The library defines an AndroidManifest.xml file with one setting.

<application
        android:networkSecurityConfig="@xml/network_security_config"/>
        
The library also contains a resource file, network_security_config.xml, that tells an android device running an app with this library to trust user certificates, like the Charles trust certificate, for Android N onwards.

The other key setting is in the app build.gradle file.  This line makes it a library.

apply plugin: 'com.android.library'

# Deployment

Ibid: https://docs.gradle.org/current/userguide/publishing_maven.html

Maven makes the sharing of the library very easy.

The key part to enable this is this line in the app build.gradle file.

apply plugin: 'maven-publish'

Then, all the details in publishing closure in the app build.gradle defines how to identify the library, and where to put the library.

The deployment is easy, as well.  Go to the terminal.  The recipe is:

> ./gradlew clean build
> ./gradlew publishToMavenLocal

# Configuration

Ibid: https://www.charlesproxy.com/documentation/using-charles/ssl-certificates/
Ibid: https://www.charlesproxy.com/documentation/proxying/ssl-proxying/
Ibid: https://medium.com/@hackupstate/using-charles-proxy-to-debug-android-ssl-traffic-e61fc38760f7

These three web pages do a good job of defining how to configure both physical and emulator devices to try out the Charles proxy SSL functionality.

There were a few gotchas.

On the physical android device, the pem certificate file would download but not install (read error).

To work around that, we installed it manually.

Steps to manually install the pem certificate file are:
1) Open Settings app
2) Tap Security
3) Tap Install from storage
4) Choose the downloaded file in downloads
5) This requires a screen lock to be set; use a PIN lock.

On the emulator, it is not obvious where to enter the proxy IP address and port needed to located Charles on your computer.

Steps to set the proxy IP address and port on the emulator are:
1) Open the Settings app on emulator device.
2) Tap Network & Internet.
3) Tap Mobile network.
4) Tap Access Point Names.
5) Tap the default APN (eg. mine was T-Mobile US).
6) Edit two values.
7) Set Proxy to LOCAL_IP.
8) Set Port to 8888 (charles port).
9) Tap 3-dot menu (top-right).
10) Click Save menu item.
11) Tap back button 2x.
12) Toggle WiFi off/on.
