## S.S. Portal: What is Self-Service Portal?

Please find details about Self-Service Portal (S.S. Portal) [here](/documentation/SS%20Portal%20Introduction)

## S.S. Portal: How to get started on Self-Service Portal?

To get started please follow our [Getting Started Guide](/documentation/SS%20Portal%20Getting%20Started)

Also, for the tunnels issues I am planning to add this faq: 

## Tunnels: Unable to start tunnels locally, what should I do?
There are various reasons that may cause this issue. Please see below:
* Previous process not exited: There are times where a process is running the tunnel will hang and will not allow you to connect or create tunnel again though you have already stopped your test cases. Please check any active tunnel using the below command and then and killing any id's that seem like they are still running.
  
  ```$ ps aux | grep tunnel```
  
* SauceLabs has reached maximum tunnel count: Currently we have a limit of 60 tunnels with sauce-labs. If we have reached this limit, you will not be able to establish a new tunnel. To check total active tunnels [click here](http://stats.dxt.walmartlabs.com/data?filter=tunnels.walmartLabs.totalActiveTunnels)

## Functional Testing: I’m having npm install failure, what should I do?

Please make sure that you’re using compatible node and npm. Check versions by node -v and npm -v

## Functional Testing: Which magellan command should I use to launch my test?

Please read magellan help by ./node_modules/.bin/magellan –help first. If you cannot find what you want there, or if you’re still not sure, please reach us in slack channel lised below

## Functional Testing: Why my test passes in one browser but fails in another one?

There are couple of things can impact the test results. Page rendering speed, css selector compatibility, viewport size or even the way element’s being rendered. However in most cases the descrepancy is because we’re not really simulating user behaviors in the test. For instance, please make sure your code is not clicking on an element that is not in the viewport.

## Mocking: How To Read Dynamic URLs In Request?

```javascript
var shifu = require('@walmart/shifu');
shifu.route({
  path: '/get/customerInfo/{customerid}/{zipcode}'
  handler: function(request, reply) {
    var params = request.params;
    var customerid = params.customerid; // customerid is 123 if request is "/get/customerInfo/123/92127"
    var zipcode = params.zipcode;       // zipcode is 92127 if request is "/get/customerInfo/123/92127"
  }
});
```

## Mocking: How To Read Query Parameters In Request?

```javascript
var shifu = require('@walmart/shifu');
shifu.route({
  path: '/api/getCart'
  handler: function(request, reply) {
    var queryParams = request.query;
    // foo would be "bar" if incoming request is "/api/getCart?foo=bar"
    var foo = queryParams.foo;
  }
});
```

## Mocking: How To Set CORS Headers?

The [Cross-Origin Resource Sharing](https://www.w3.org/TR/cors/) protocol allows browsers to make cross-origin API calls. CORS is required by web application running inside a browser which are loaded from a different domain than the API server. CORS headers are disabled by default. To enable, set `cors` to true, or to an object with the following options:

| Option | Description |
| ------- | :-----------: |
| origin | a string array of allowed origin servers `Access-Control-Allow-Origin`. Defaults to any origin ['*'] |
| maxAge | number of seconds the browser should cache the CORS response ('Access-Control-Max-Age'). The greater the value, the longer it will take before the browser checks for changes in policy. Defaults to 86400 (one day). |
| headers | string array of allowed headers `Access-Control-Allow-Headers`. Defaults to `['Authorization', 'Content-Type', 'If-None-Match']`. |
| additionalHeaders | string array of additional headers to headers. Use this to keep the default headers in place. |
| methods | string array of allowed HTTP methods Access-Control-Allow-Methods. Defaults to `['GET', 'HEAD', 'POST', 'PUT', 'DELETE', 'OPTIONS']` |
| additionalMethods | string array of additional methods to methods. Use this to keep the default methods in place |
| exposedHeaders | string array of exposed headers Access-Control-Expose-Headers. Defaults to `['WWW-Authenticate', 'Server-Authorization'` |
| additionalExposedHeaders | a string array of additional headers to exposedHeaders. Use this to keep the default headers in place. |
| credentials | if true, allows user credentials to be sent Access-Control-Allow-Credentials. Defaults to false. |


```javascript
var corsHeaders = {
  origin: ['*'],
  headers: ["Access-Control-Allow-Headers", "Origin, X-Requested-With, Content-Type, Accept"],
  credentials: true,
}

// Items
shifu.route({
  id: 'tempo',
  label: 'Tempo',
  path: '/tempo1',
    
  config: {
    cors: corsHeaders
  },
  handler: function(req, reply) {
    shifu.util.respondWithFile(this, reply);
  }
});
```

## Saucelabs: Why we need to whitelist internal services for DMZ ?
Due to network restrictions, Saucelabs cannot access Walmart's internal services through DMZ. For Saucelabs to be able to make requests to these services, we need to whitelist these through Info Sec team.

## Saucelabs: How to whitelist internal services to enable inbound traffic from Saucelabs through DMZ for functional testing ?

1) Create SRCR  (Security Risk and Compliance Review) from [here](https://egrc.wal-mart.com/archer/apps/ArcherApp/Home.aspx#workspace/74).Please follow this [document](https://share.wal-mart.com/Sites/SecurityCRM/Shared%20Documents/Firewall%20Rule%20Documents/ISD%20Network%20Security%20Firewall%20Rule%20Guidelines.pdf) for further details.For any help on SRCR, please follow up on the Slack channel #help_srcr

    Architecture diagram for Saucelabs/TestObject DMZ setup is [here](https://confluence.walmart.com/pages/viewpage.action?pageId=163647559)

2) Once the SRCR is approved, please visit the firewall rule request [service desk](https://jira.walmart.com/servicedesk/customer/portal/521/create/1002) to create a firewall request.

     * "Application and Project Name" : Use your team's name + "SauceLabs DMZ Network Access".  For example "Grocery - SauceLabs DMZ Network Access"

     * Team Name: Your team name.  For example "Checkout"

     * Technical Lead Contact: Someone on your team who is familiar with the system under test.

     * Data Classification
   Refer to the Data Classification Chart linked from the help text next to this field.  This refers to the nature of the data available on the system under test.  If you're unsure, please email InfoSec risk team : InfosecIA@email.wal-mart.com

     * SRCR Number: Approved SRCR

     * Business justification
You can say something like "To allow the SauceLabs DMZ Network Proxy to reach an internal system under test." as well as a description of what the system under test does, for example, "To allow the SauceLabs DMZ Network Proxy to reach an internal system under test. This system is a QA staging environment for previewing upcoming releases of the Walmart Grocery app."

     * Firewall rules requested:

        Source Address and Hostname: – support both Saucelabs and TestObject devices

        For Saucelabs, the addresses will be *.saucelabs.com

        For TestObject, the addresses will be *.testobject.com

        Destination Address and Hostname:
        IP of the internal system under test and Hostname of the internal system under test

	      Port: <Ports to open> e.g 80 and 443

        Protocol: <Prototol> e.g HTTP and HTTPS
	    Please refer [here](https://jira.walmart.com/browse/ISFWREQ-5508) for sample ticket

     * Type of request:
        Temporary or permanent based on your needs

     * Team DL Email Address:
        Your team's email address

**Please note that the whitelisting processs can take longer time to complete. We recommend to work closely with Info Sec team to expedite the process.**