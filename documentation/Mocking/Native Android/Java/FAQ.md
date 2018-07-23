## What Is Shifu? 
Shifu is a mocking tool for Android that is run on the emulator/device. It's a library that is is setup and controlled from the Android tests. It has full support for http & https and also supports record and playback.

<br>

## What Are The Benefits Of Shifu? 

* Easy to setup and use
* No dependencies to extra APK or computer. Its a simple jar that works on both emulators and devices
* Shifu can be built into the test APK by using androidTestCompile
* Completely tailored for Android with a rich set of API:s
* Full support for http & https 
* Supports Record & Replay 

<br>

## How Do I Get Started? 

Please see [getting started](https://gecgithub01.walmart.com/otto/shifu-java/wiki/Getting-Started) 

<br>

## Where Can I Download a Boilerplate Project? 

Please download an [example project here](https://gecgithub01.walmart.com/otto/boilerplate-shifu-android) 

<br>


## How Does Record & Replay Work?

Please see this page on [record & playback](https://gecgithub01.walmart.com/otto/shifu-java/wiki/Record-&-Playback) 

<br>

## What Can Be Mocked? 
Any Restful service API can be mocked such as:

 - GET
 - POST
 - PUT
 - DELETE
 - OPTIONS
 - and so on..

<br>

## Can AJAX Calls Be Mocked?
Yes - It is same as for any other backend service. For AJAX call, point it to the mocked server instance instead of 
the actual back end service and add a mocked route in the file containing mocked routes for mock server.

<br>

## What Are The Pre-Requisites?
 * Android API level 16

<br>

## How Can I Add Mock Server Dependency To My Android Project?

**Set dependency in build.gradle:**

```
maven {
    url 'http://gec-maven-nexus.walmart.com/nexus/content/repositories/thirdparty'
}

dependencies {
    androidTestCompile 'com.walmart.otto:shifu:1.8.2'
}
```

<br>

## How Do I Start Shifu?
Add the following code in your test class

```
@Rule
public ShifuRule shifuRule = new ShifuRule(new Shifu.Config(), InstrumentationRegistry.getTargetContext());
```

<br>

## How Do I Add A Mock?
```
//For a request url matching "/example/example.*" shifu will return ex.json that is located in the assets folder
        
shifu.mock(get(urlMatching("/example/example.*")).willReturn(aResponse().withStatus(233).withBodyFile("ex.json")));
```     


<br>

## How Do I Mock A Complete Directory?

```
//WithBodyFileInMockedDirectory can be used when setting Shifu.Config.mockedDirectory 
so that full urls are not needed, only a path from the folder set in Config.mockedDirectory. 
        
shifu.mock(post(urlMatching("/example/ex.jsp")).willReturn(aResponse().withBodyFileInMockedDirectory("ex.json)));
        
```

