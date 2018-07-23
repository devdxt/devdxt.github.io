
### 1. Updating run-mock-server-console.js to enable HTTPS

```js
require('./endpoints');
var fs = require('fs');
var shifu = require('@walmart/shifu');
 
shifu.start({
  host: "localhost",  
  mockedDirectory: "./resources/mocked-data",
  port: 8000,
  httpsPort: 4444,
  project: 'HelloShifu',
  metricsDB: 'http://kairos.prod.rapido.globalproducts.prod.walmart.com/api/v1/datapoints'
});
```
> The default port for HTTPS is `4444`

### 2. Starting mock server with HTTPS enabled

Once you add the above code, the mock server will provide the HTTPS and HTTPS support by default. Hence when the mock server starts up, you will see both the ports open. Note that the mock server auto generates the certificates (key.pem and cert.pem). If you want to provide your own key and certificate, you can provide it under the mocked data directory.
