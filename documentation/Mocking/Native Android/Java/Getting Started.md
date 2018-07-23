Follow the instructions below if you want to see how Shifu can be setup. 

**Set dependency in build.gradle:**

```
maven {
    url 'http://gec-maven-nexus.walmart.com/nexus/content/repositories/thirdparty'
}

dependencies {
    androidTestCompile 'com.walmart.otto:shifu:1.8.2'
}
```

**Start Shifu:**
```
@Rule
public ShifuRule shifuRule = new ShifuRule(new Shifu.Config(), InstrumentationRegistry.getTargetContext());
```

**Mock network requests:**

Mocking can be performed by [record & playback](https://gecgithub01.walmart.com/otto/shifu-java/wiki/Record-&-Playback) or by manual mapping:

```
private void exampleOfManualMappingWithShifu() {
 //For a request url matching "/example/example.*" shifu will return ex.json that is located in the assets folder
        
 shifu.mock(get(urlMatching("/example/example.*")).willReturn(aResponse().withStatus(233).withBodyFile("ex.json")));
        
 //WithBodyFileInMockedDirectory can be used when setting Shifu.Config.mockedDirectory 
 so that full urls are not needed, only a path from the folder set in Config.mockedDirectory. 
        
 shifu.mock(post(urlMatching("/example/ex.jsp")).willReturn(aResponse().withBodyFileInMockedDirectory("ex.json)));
                      
}
```

**Boilerplate Project**

Please go here [for an example project](https://gecgithub01.walmart.com/otto/boilerplate-shifu-android)



