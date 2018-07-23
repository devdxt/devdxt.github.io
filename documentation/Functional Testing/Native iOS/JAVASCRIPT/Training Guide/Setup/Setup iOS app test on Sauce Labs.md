### Setup iOS app sample test on Sauce Labs
* Apply Sauce Labs access: [here](http://qm.otto.walmartlabs.com:8080)
* Open terminal: (or add them into .bash_profile)
```bash
$ export SAUCE_USERNAME=${USERNAME}
$ export SAUCE_ACCESS_KEY=${ACCESSKEY}
```
* Upload the testing iOS app to Sauce Labs
```bash
# Download Walmart app
$ curl -L 'http://gec-maven-nexus.walmart.com/nexus/service/local/artifact/maven/redirect?r=pangaea_snapshots&g=com.walmart.ios.development-qa-nightly&a=Walmart.app&v=LATEST&p=zip' > app/Walmart.zip && unzip -o app/Walmart.zip -d app/ && rm -rf app/Users app/Walmart.zip && zip -r app/Walmart.zip app/Walmart.app

# Upload Walmart app to SauceLabs, and name it: Walmart_app.zip
$ curl -u ${SAUCE_USERNAME}:${SAUCE_ACCESS_KEY} -X POST "http://saucelabs.com/rest/v1/storage/${SAUCE_USERNAME}/Walmart_app.zip?overwrite=true" -H "Content-Type: application/octet-stream" --data-binary @./app/Walmart.zip
```
* To run tests with live services, use command:
```bash
DPRO=ios ./node_modules/.bin/magellan --config magellan.json --profile appium-ios-app  --test tests/app.test.js --serial -- max_test_attempts=1
``` 
* To run tests with mocked services, use command:
```bash
DPRO=ios ./node_modules/.bin/magellan --config magellan.json --profile appium-ios-app-mock-sauce  --test tests/app-mock.test.js --serial --max_test_attempts=1 --sauce_create_tunnels
```
* You can view your tests running at: https://saucelabs.com/beta/dashboard/tests
