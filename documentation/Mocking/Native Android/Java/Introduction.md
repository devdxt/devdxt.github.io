## Summary

Most apps rely on one or many back end services. For successful test execution and fast development, all the dependent backend services should be reliable 100% of the time. However that is not possible as the backend services may be down from time to time for various reasons or may have data inconsistency issues which makes testing/development against live services inefficient and time consuming.

Shifu is a Java solution that enables you to quickly stub the API calls done by your app. During testing Shifu is deployed on the device/emulator enabling the app to point to the device localhost instead of calling live services. Pre-recorded responses are then returned for various endpoints from Shifu.

## Use Case

As Shifu is deployed on the emulator/device there are no dependencies to a computer that might be on a secure hard to reach network. Shifu is also integrated directly with the tests and built into the test APK. Instrumentation testing frameworks like Espresso can be used. Shifu provides Espresso with an idling resource which further enhances your tests.

*   Provides an easy way to mock services
*	Execute same test cases against mock or live service
*   Easy to set up 
*	Ability to use same JSON response file and change data dynamically for mocked response for various variants
*	No dependencies to extra APK or computer. Its a simple jar that works on both emulators and devices  
*	Shifu can be built into the test APK by using androidTestCompile
*	Supports Record & Replay
*	HTTPS Support: HTTPS support for all the urls

## Impact
Higher quality apps due to deterministic tests. As Shifu is easy to setup and use it also saves development time. Shifu supports record & replay. 
 
## Work Flow
The following is the work flow when mock server is used:<br/>
*	Identify REST endpoints that needs to be mocked<br/>
*	Gather or record mocked data for those REST endpoints<br/>
*	Setup an instrumentation test that initiates Shifu<br/>
*	Setup mocks with Shifu<br/>
*	Configure app to communicate with Shifu<br/>
*	Run your instrumentation test and the mocked data will be returned for mocked routes.<br/>

## Features List:

|Features	|Status|
| ------------- | ------------- |
|Return multiple responses for same rest end point|	Yes | 
|Support for HTTP (for mocking)	| Yes |
|Support for HTTPS (for mocking)|	 Yes |
|Ease of SetUp	| Yes |
|Mock Java Services	| Yes |
|Run tests manually against mock service|	 Yes|
|Read request (body, query parameters, etc) for mocked routes|	 Yes |
|Supports server states	| Yes |
|Test Reuse	 | Yes |
|Dynamic Transposition of Mock Data (JSON)	| Yes |
|Variants support for mocked REST APIs	 | Yes |
|Mocked data response from specific folder irrespective of Rest APIs|	 Yes |
|Support for record & replay|	 Yes |


## Customers

The following teams are using Shifu:

* Android Core

* Omnichannel 


