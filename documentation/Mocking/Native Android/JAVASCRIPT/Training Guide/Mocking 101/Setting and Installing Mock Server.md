### 1. Pre-requisites

- node.js 4+ (npm is included in the package)
- If inside of Walmart you need npm access to the [internal nexus/npm repo](https://sde.walmart.com/docs/proximity/npm.html)

### 2. Add mock dependency to `package.json`

```json
"dependencies": {
  "@walmart/shifu": "^3.0.4"
}
```

### 3. Add `.npmrc` file to the project

```bash
registry=https://npme.walmart.com/
strict-ssl=false
```

### 4. Install mock dependency with `npm install`

Run `npm install` command to install mock related dependencies.

### 5. Add `resources/endpoints.js` and create `./resources/mocked-data` directory to store the mock data.

```js
require('./endpoints');
require('@walmart/shifu').start({
  host: "localhost",
  mockedDirectory: "./resources/mocked-data",
  port: 8000,
  project: 'HelloShifu',
  metricsDB: 'http://kairos.prod.rapido.globalproducts.prod.walmart.com/api/v1/datapoints'
});
```

### 6. Add `resources/run-mock-server-console.js`

```js
require('./endpoints');
require('@walmart/shifu').start({
  host: "localhost",
  mockedDirectory: "./resources/mocked-data",
  port: 8000,
  project: 'HelloShifu',
  metricsDB: 'http://kairos.prod.rapido.globalproducts.prod.walmart.com/api/v1/datapoints'
});
```
Please note that you will need to replace `HelloShifu` for key `project` field with your project name(without dashes). Once you add that, you will be able to see the [usage statistics for your project](https://prod.rapido.walmart.com/dashboard/db/shifu-usage) under your project. If you don't have access to this dashboard, please [file a ticket](https://jira.walmart.com/servicedesk/customer/portal/1403).

### 7. Add script to start mock server in `package.json`

``` json
"scripts": {
  "lint": "eslint . --ext .js",
  "start-server": "node ./resources/run-mock-server-console.js"
},
```

### 8. Test mock server can be started

``` bash
npm run start-server
```