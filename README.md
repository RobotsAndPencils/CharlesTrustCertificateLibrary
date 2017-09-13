# Charles Trust

This is an android library to trust user installed CA certificates (e.g. the Charles Root Certificate).

## Synopsis
The cleaner solution to share Charles proxy settings is to create a classless android library with an android manifest and network security config file.

I did create a groovy plugin to apply to any app build.gradle file.  The resulting logic would modify all the app project files to integrate the Charles proxy settings.

However, the integration of an android library is much simpler.  Then, the bulk of the integration work can be left to Android Studio.

## Getting Started

The library is uploaded on bintray, and shared on jcenter.

To use this library, modify your project's build.gradle file.

Add jcenter() to the following closures.

```
buildscript {
    
    repositories {
        ...
        jcenter()
        ...
    }

}


allprojects {

    repositories {
        ...
        jcenter()
        ...
    }

}
```

Add the following dependency to your app module's build.gradle file.

```
dependencies {

    ...
    compile 'com.robotsandpencils.charles:CharlesLibrary:0.0.1'
    ...

}
```

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes.

### Prerequisites

To use this library, you need an Android app running on Android OS version N or greater.

### Installing

The library is installed by leveraging Android Studio's integration with jcenter.

No installation steps are needed.

# Configuration for Tests

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

## Running the tests

There are no code tests, since this library only contains configuration settings in AndroidManifest.xml and network_security_config.xml.

The test is add this library to an app that has HTTPS api calls.

If you see your GET/POST/PUT/UPDATE/DELETE calls getting logged in Charles, then the Charles certificate is trusted because the library is present.

## Deployment

This project is pre-configured to communicate with the appropriate package on bintray.

If any properties must be modified, then the developer would get this project.

eg) promote version
```
git clone git@github.com:RobotsAndPencils/CharlesTrustCertificateLibrary.git
git checkout -d promote_version
```

This library project is intended to be edited in Android Studio

Open the library module's build.gradle, and modify:

```
ext {

    ...
    libraryVersion = '0.0.2'
    ...

}
```

Open the Terminal tab, and execute the following:

```
> ./gradlew clean build
> ./gradlew install
> ./gradlew bintrayUpload
```

## Built With

* [bintray](https://bintray.com) - The SaaS repository
  https://inthecheesefactory.com/blog/how-to-upload-library-to-jcenter-maven-central-as-dependency/en
* [Maven](https://maven.apache.org/) - Dependency Management

## Authors

* **Phillip Wray** - *Initial work* - [CharlesTrust](https://github.com/RobotsAndPencils/CharlesTrustCertificateLibrary)

See also the list of [contributors](https://github.com/RobotsAndPencils/CharlesTrustCertificateLibrary/graphs/contributors) who participated in this project.

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

## Acknowledgments

* https://www.charlesproxy.com/documentation/using-charles/ssl-certificates/
* https://medium.com/@hackupstate/using-charles-proxy-to-debug-android-ssl-traffic-e61fc38760f7
* https://inthecheesefactory.com/blog/how-to-upload-library-to-jcenter-maven-central-as-dependency/en
* Farhan Khan
* Neal Sanche
* Uche Okeke
* Vitaly Nikolaychuk
* Les Friesen
