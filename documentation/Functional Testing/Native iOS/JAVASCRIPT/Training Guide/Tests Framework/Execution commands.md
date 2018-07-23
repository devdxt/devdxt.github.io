### Execution commands
After getting your tests up and running, you probably have tons of questions regarding how this work, let’s start with the command that we are using to get the tests running in local box, which is:

```bash
$ npm run test:ios
```
 - To understand what is **npm run**, please check [here](https://docs.npmjs.com/cli/run-script).
 - ***test:ios*** is a 'script' defined in **package.json** file, which is:
```bash
"test:ios": "DPRO=ios ./node_modules/.bin/magellan --config magellan.json --local_browser appiumiosapp  --test tests/app.test.js --serial --max_test_attempts=1"
 ```
- Commands parameters ***--test*** , ***--serial***, ***--max_test_attempts***, etc are all magellan arguments. To find all magellan command line arguments and the usages:
```bash
./node_modules/.bin/magellan --help
```
- Magellan is part of the functional JS TDK, and it is designed for running tests in massive scale. 

  Following is an example that telling magellan to run tests with 30 workers, 5 retry attempts per failed test 
```bash
./node_modules/.bin/magellan --max_workers 30 --max_test_attempts 5
```
- ***DPRO=ios*** is telling tests to load data from **./conf/data/ios.js**
  
   **DPRO**  \- data provider, support both .json and .js file. We recommend .js format. 
   Each **.js** data file should return a **json** object. Please check [here](https://github.com/TestArmada/dpro), for more details
```bash
 # Example:
 # To load from ${REPO_ROOT}/config/data/local.js
 DPRO=local ./node_modules/.bin/magellan --test xxxxx ......
 ```
- **--local_browser appiumiosapp** tells tests to use [testarmada-magellan-local-executor](https://github.com/TestArmada/magellan-local-executor) . It loads Desired Capabilities from nightwatch.json.

  **Executor**  \- acts as a middle layer between magellan and test framework to drive test run (via framework) based on a specific need (differentiated by executing environments).