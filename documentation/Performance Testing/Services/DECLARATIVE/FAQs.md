### **FAQs**

**1.	Where can I store my JMeter test artifacts? <br/>**
Jmeter test artifacts should be in your project repository under the test/performance folder as depicted in the image:<br/>
![](images/FolderStructure.png)
<br/>
**2.	Running my test errors out or does not produce results. How do I debug? <br/>**
Ensure the location of JMX complies to the diagram above and the Kafka Listener is added to your test plan. Without the Kafka listener, the results will not flow into the Data Insights module.

**3.	I have developed custom plugin for my test. How do I get this on my load agents?<br/>**
Dedicated load agents are required for any customization. Reach out to the Otto team on **#testautomation** channel to create dedicated agent and to add custom plugins to it.

**4.	I have custom jars I use in my test client. How do I add these to my load agents?<br/>**
Dedicated load agents are required for any customization. Reach out to the Otto team on **#testautomation** channel to create dedicated agent and to add custom jar files to it.

**5.	I want to use custom listeners to stream test results to my database. How do I do that?<br/>**
This is not supported on the Test Armada platform. We mandate all tests run on our platform stream results into Data Insights module.

**6.	I want to use only the Data Insights module of Test Armada to maintain my test results. How can I do this?<br/>**
This is possible after **Q3** of **FY19**. Reach out to Otto team on **#testautomation** channel for more details.

**7.	Can I use my own JMeter load agents?<br/>**
Yes you can. Test agents in our internal data centers can be added and tied to your project. Your load agents will have to use JMeter available for download on [getLatestVersionOfJmeter](http://gec-maven-nexus.walmart.com/content/repositories/pangaea_releases/otto/nextgen/nextgenjmeter/nextgenplatformjmeter/). 

**8.	Can I run performance tests from load agents in public cloud?<br/>**
Currently we do not have test agents setup in public cloud. This is in our roadmap for **Q3** & **Q4** of **FY19** to have agents setup in three US regions.

**9.	Can I get help with JMeter scripting?<br/>**
Debugging and troubleshooting help with existing scripts is possible. Test Armada team does not undertake new scripting work.

