# OrbitalSonicFCM
[![](https://jitpack.io/v/orbitalsonic/OrbitalSonicFCM.svg)](https://jitpack.io/#orbitalsonic/OrbitalSonicFCM)

OrbitalSonicFCM is a [Firebase Cloud Messaging](https://firebase.google.com/docs/cloud-messaging) Android library that demonstrates registering your Android app for notifications and handling the receipt of a message. Example Send Data Message using the HTTP protocol with [Postman](https://www.postman.com/).

## Getting Started

### Step 1

[Add firebase to your Android App](https://firebase.google.com/docs/android/setup)

#### Note: 
After completion of step one, your project should have a google-services.json file added to the root of your project along with the classpath, plugin and dependecies

#### Classpath in project level build.gradle
```
    classpath 'com.google.gms:google-services:latest-version'
```
or latest
```
    id 'com.google.gms.google-services' version 'latest-version' apply false
```
    
#### Plugin in App level build.gradle
```
    id 'com.google.gms.google-services'
```
#### Dependencies
no dependencies required

### Step 2

Add maven repository in project level build.gradle or in latest project setting.gradle file
```
    repositories {
        google()
        mavenCentral()
        maven { url "https://jitpack.io" }
    }
```  

### Step 3

Add OrbitalSonicFCM dependencies in App level build.gradle.
```
    dependencies {
            implementation 'com.github.orbitalsonic:OrbitalSonicFCM:1.0.1
    }
```  


### Step 4

Finally intialize Firebase and setup FCM in application class or in your "MainActivity"

```
    SonicFCM.setupFCM(this, "YourTopicName")
```


### Remove

If you want to stop receiving notification from the subscribed topic simply call.
```
    SonicFCM.removeFCM("YourTopicName")
```

# Send Data Message using the HTTP protocol with POSTMAN

### Step 1

You have to copy Legacy Server Key from Firebase Console > Project Settings > Cloud Messaging

#### Note: 

Firebase has upgraded our server keys to a new version. You may continue to use your Legacy server key, but it is recommended that you upgrade to the newest version.
If anyone else is facing any issue then First Enabled "Firebase Cloud Messaging API" from Firebase console, follow the following points

* go to the google cloud platform website
* go to APIs and Services
* go to Enabled APIs & Services
* click + Enable APIs and Services
* search for Firebase In-App Messaging API and make sure it's enabled.

### Step 2

* Open Postman, click on Enter request URL textbox, enter firebase url
```
 https://fcm.googleapis.com/fcm/send
```
* Then change request type to "POST"
* Now to click on Header and add two params "Content-Type" and "Authorization"
```
 Content-Type: application/json
 Authorization: key=AAAAp5XtBPY:APA91bG_fypMd0j... //FCM SERVER KEY
```
* Now click on "Body" than select "Raw" and add value as JSON object like below
```
{
      "to":"/topics/YourTopicName", 
      "data":
      {
                "title": "My Application Titile is Here",
	        "short_desc": "My Application Short Description is here",
	        "long_desc": "My Application Long Description is here",
	        "icon": "App Icon link is here",
	        "feature": "App Feature Image Link is here",
	        "package": "Promotional app package name is here"
      }
  }
```
### Postman Screen

#### Header

![alt text](https://github.com/orbitalsonic/OrbitalSonicFCM/blob/master/Screenshots/postman_screen1.png?raw=true)

#### Body

![alt text](https://github.com/orbitalsonic/OrbitalSonicFCM/blob/master/Screenshots/postman_screen2.png?raw=true)

### Note

These Three items are mandatory for notification
* title
* icon
* short_desc

These Three items are optional for notification
* long_desc
* feature
* package (in case of other app promotion)


# LICENSE

Copyright 2022 Engr. Muhammad Yaqoob

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

