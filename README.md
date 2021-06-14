![Preview image](media/media-tilt.png)

# Pix (WhatsApp Style Image and Video Picker)

Pix is a WhatsApp image picker replica. with this you can integrate a image picker just like WhatsApp.

[![Codacy Badge](https://api.codacy.com/project/badge/Grade/887abd593a5a499495c4f071accb132a)](https://app.codacy.com/app/akshay2211/PixImagePicker?utm_source=github.com&utm_medium=referral&utm_content=akshay2211/PixImagePicker&utm_campaign=Badge_Grade_Dashboard)
[![](https://img.shields.io/badge/Android%20Arsenal-PixImagePicker-blue.svg?style=flat-square)](https://android-arsenal.com/details/1/6935)
[![](https://jitpack.io/v/akshay2211/PixImagePicker.svg?style=flat-square)](https://jitpack.io/#akshay2211/PixImagePicker)
[![](https://img.shields.io/badge/Medium-Pix-black.svg?style=flat-square)](https://medium.com/@fxn769/pix-media-picker-android-library-1ec3c5e5f91a)
[![](https://img.shields.io/badge/API-16%2B-orange.svg?style=flat-square)](https://android-arsenal.com/api?level=16)
[![](https://img.shields.io/badge/Awesome%20Android-PixImagePicker-green.svg?style=flat-square)](https://android.libhunt.com/piximagepicker-alternatives)
[![Pix Image Picker](https://www.appbrain.com/stats/libraries/shield/pix-image-picker.svg)](https://www.appbrain.com/stats/libraries/details/pix-image-picker/pix-image-picker)
<img src="http://img.shields.io/liberapay/receives/akshay2211.svg?logo=liberapay">
[![xscode](https://img.shields.io/badge/Available%20on-xs%3Acode-blue?style=?style=plastic&logo=appveyor&logo=data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAEAAAABACAMAAACdt4HsAAAAGXRFWHRTb2Z0d2FyZQBBZG9iZSBJbWFnZVJlYWR5ccllPAAAAAZQTFRF////////VXz1bAAAAAJ0Uk5T/wDltzBKAAAAlUlEQVR42uzXSwqAMAwE0Mn9L+3Ggtgkk35QwcnSJo9S+yGwM9DCooCbgn4YrJ4CIPUcQF7/XSBbx2TEz4sAZ2q1RAECBAiYBlCtvwN+KiYAlG7UDGj59MViT9hOwEqAhYCtAsUZvL6I6W8c2wcbd+LIWSCHSTeSAAECngN4xxIDSK9f4B9t377Wd7H5Nt7/Xz8eAgwAvesLRjYYPuUAAAAASUVORK5CYII=)](https://xscode.com/akshay2211/piximagepicker)

## Upcoming 
### These changes including re-structuring from scratch are in progress
1. Androidx Camera API integration
2. Scoped storage to support Android Version 30
3. Minimum SDK from 19 to 21
4. Migration from Java to Kotlin
5. Ability to use it as a Fragment


 
## Demo
![](media/media.gif)
![](media/one.png)

## Usage
```java
Options options = Options.init()
      .setRequestCode(100)                                           //Request code for activity results
      .setCount(3)                                                   //Number of images to restict selection count
      .setFrontfacing(false)                                         //Front Facing camera on start
      .setPreSelectedUrls(returnValue)                               //Pre selected Image Urls
      .setSpanCount(4)                                               //Span count for gallery min 1 & max 5
      .setMode(Options.Mode.All)                                     //Option to select only pictures or videos or both
      .setVideoDurationLimitinSeconds(30)                            //Duration for video recording
      .setScreenOrientation(Options.SCREEN_ORIENTATION_PORTRAIT)     //Orientaion
      .setPath("/pix/images");                                       //Custom Path For media Storage
    
Pix.start(MainActivity.this, options);
```
or just use with minimal config
```java
Pix.start(context, Options.init().setRequestCode(100));
```
for fetching only a single picture.

Use onActivityResult method to get results
```java
@Override
public void onActivityResult(int requestCode, int resultCode, Intent data) {
    super.onActivityResult(requestCode, resultCode, data);
    if (resultCode == Activity.RESULT_OK && requestCode == RequestCode) {
        ArrayList<String> returnValue = data.getStringArrayListExtra(Pix.IMAGE_RESULTS);
    }
}
```
## Customise
### Theme
include these items in colors.xml with custom color codes
```xml
<resources>
    <color name="colorPrimaryPix">#075e54</color>
    <color name="colorPrimaryLightPix">#80075e54</color>
</resources>
```

## Permission Handling
include onRequestPermissionsResult method in your Activity/Fragment for permission selection
```java
@Override
public void onRequestPermissionsResult(int requestCode, String permissions[], int[] grantResults) {
    switch (requestCode) {
        case PermUtil.REQUEST_CODE_ASK_MULTIPLE_PERMISSIONS: {
            // If request is cancelled, the result arrays are empty.
            if (grantResults.length > 0 && grantResults[0] == PackageManager.PERMISSION_GRANTED) {
                Pix.start(context, Options.init().setRequestCode(100));
            } else {
                Toast.makeText(MainActivity.this, "Approve permissions to open Pix ImagePicker", Toast.LENGTH_LONG).show();
            }
            return;
        }
    }
}
```

## Thanks to
  - [Glide]
  - [FastScroll]
  - [Header-decor]
  - [CameraView]
  
## Backers
Become a backer and help us sustain our activities! 🙏🙏
<a href="https://opencollective.com/piximagepicker#backers" target="_blank"><img src="https://opencollective.com/piximagepicker/backers.svg?width=890"></a>

## Download
[![Download](https://api.bintray.com/packages/fxn769/android_projects/Pix/images/download.svg)](https://bintray.com/fxn769/android_projects/Pix/_latestVersion) or grab via Gradle:
 
include in app level build.gradle
 ```groovy
repositories {
   maven { url 'https://jitpack.io' }
}
 ```
```groovy
implementation  'com.fxn769:pix:1.5.6'
```
or Maven:
```xml
<dependency>
  <groupId>com.fxn769</groupId>
  <artifactId>pix</artifactId>
  <version>1.5.6</version>
  <type>pom</type>
</dependency>
```
or ivy:
```xml
<dependency org='com.fxn769' name='pix' rev='1.5.6'>
  <artifact name='pix' ext='pom' ></artifact>
</dependency>
```

Snapshots of the development version are available in [Sonatype's `snapshots` repository][snap].

## Updates
[Pix](https://github.com/akshay2211/PixImagePicker) is using the new Material library with the legacy Support Library. You have to migrate to android.support to androidx in order to use com.google.android.material. 

With Android Studio 3.2 and higher, you can quickly migrate an existing project to use AndroidX by selecting *Refactor > Migrate* to AndroidX from the menu bar.

For more details kindly refer [Migrating to AndroidX](https://developer.android.com/jetpack/androidx/migrate#migrate)

### for Version 1.2.5 refer [here](https://github.com/akshay2211/PixImagePicker/wiki/Documendation-ver-1.2.5)

## License
Licensed under the Apache License, Version 2.0, [click here for the full license](/LICENSE).

## Author & support
This project was created by [Akshay Sharma](https://akshay2211.github.io/).

> If you appreciate my work, consider buying me a cup of :coffee: to keep me recharged :metal: by [PayPal](https://www.paypal.me/akshay2211)

> I love using my work and I'm available for contract work. Freelancing helps to maintain and keep [my open source projects](https://github.com/akshay2211/) up to date!

[Glide]: <https://github.com/bumptech/glide>
[FastScroll]: <https://github.com/L4Digital/FastScroll>
[Header-decor]: <https://github.com/edubarr/header-decor>
[CameraView]: <https://github.com/natario1/CameraView>
