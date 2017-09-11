# Charles Trust

This is an android library to trust user installed CA certificates (e.g. the Charles Root Certificate).

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

## Running the tests

There are no code tests, since this library only contains configuration settings in AndroidManifest.xml and network_security_config.xml.

The test is add this library to an app that has HTTPS api calls.

Following this article on how to monitor SSL traffic, you can infer that the library augmented your app correctly.

```
https://medium.com/@hackupstate/using-charles-proxy-to-debug-android-ssl-traffic-e61fc38760f7
```

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
