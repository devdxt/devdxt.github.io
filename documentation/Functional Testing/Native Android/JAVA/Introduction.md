## Summary

The functional native Android Test Development Kit (TDK) enables you to execute your native Android tests easily, reliably and quickly in the cloud. By using [Flank](https://github.com/TestArmada/flank) which is part of the TDK, users can run their native Android tests in parallell on Firebase test lab in just a few steps.  The TDK will also provide a summarized diagram and logs for each test package and detailed XML test reports are shown in the job directly and also sent to our DI platform to track the results using the Test Armada dashboard. 
 
## Use Case

Flank which is part of the TDK is a Firebase Test Lab tool for massively-scaling your automated Android tests. Run large test suites across many devices/versions/configurations at the same time, in parallel. Flank can easily be used in a CI environment where Gradle (or similar) first builds the APK:s and then Flank is used to execute the tests. By using our Flank API:s in Looper, users can easily get access to Flank and with a few simple API:s setup tests to be run on Firebase Test Lab.

 
## Architecture

![Flank Architecture]

[Flank Architecture]: ../../images/Flank.png?raw=true

## Feature List

The functional native Android TDK has the following features:

* **Sharding** - By executing tests in shards Flank blazes through long test suites in a fraction of the time, aggregating results in one friendly report.

* **Android native tests** - Flank supports execution of native android tests on Firebase Test Lab. 

* **Execution options** - You can specify in which class/package/annotation/testFile you would like tests to run. 

* **Fetches XML results** - After the test is done Flank fetches all test result XML files and stores them in a folder results. 

* **Continous Integration** - Flank is integrated into Looper and can be easily setup using its API:s. 

## Customers

The following teams are using the functional native Android TDK:

* Pickup

* MoneyServices

