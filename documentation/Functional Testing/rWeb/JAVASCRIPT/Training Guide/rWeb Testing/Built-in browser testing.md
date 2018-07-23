### Built-in browser testing

- The sample project has some pre-configured browsers that you can use via `--local_browser` command. 
- For example, the following command triggers your test in the local Firefox.
```bash
HOST=dev.walmart.com MOCK_PORT=12000 DPRO_LOCATION=./test/automation/conf/data ./node_modules/.bin/magellan --nightwatch_config ./test/automation/conf/nightwatch.json --config ./test/automation/magellan.json --local_browser firefox
```
- Full list of built in browser can be found at ***test_settings*** part in **test/automation/conf/nightwatch.json** file
- To run test with a **new browser**, you can just create a new entry in **test_settings** part

#### Quiz
- Can you make the sample test run on your local simulator's safari browser?
- Hint: here's the sample Capability:
```bash
    "appiummweb": {
      "desiredCapabilities": {
        "browserName": "safari",
        "appiumVersion": "1.7.2",
        "automationName": "xcuitest",
        "platformName": "iOS",
        "platformVersion": "11.2",
        "deviceName": "iPhone 8",
        "waitForAppScript": "true"
      },
      "selenium": {
        "start_process": false
      },
      "appium": {
        "start_process": true
      }
   },
```