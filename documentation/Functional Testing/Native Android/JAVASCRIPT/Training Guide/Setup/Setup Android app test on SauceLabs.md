### Run Android app test on SauceLabs
- Apply Sauce Labs access: [here](http://qm.otto.walmartlabs.com:8080)
- Open terminal: (or add them into .bash_profile)
```bash
$ export SAUCE_USERNAME=${USERNAME}
$ export SAUCE_ACCESS_KEY=${ACCESSKEY}
```
- Upload ./app/Walmart.apk to SauceLabs via following curl
```bash
$ curl -u ${SAUCE_USERNAME}:${SAUCE_ACCESS_KEY} -X POST "http://saucelabs.com/rest/v1/storage/${SAUCE_USERNAME}/Walmart_app.apk?overwrite=true" -H "Content-Type: application/octet-stream" --data-binary @./app/Walmart.apk
```
- Run the Android sample app test on SauceLabs
```bash
$ DPRO=android ./node_modules/.bin/magellan --nightwatch_config conf/nightwatch.json --profile appium-android-app --test tests/app-android.test.js --max_test_attempts=1
```
- You can view your tests running at: https://saucelabs.com/beta/dashboard/tests


### Quiz
Please create a new AVD, e.g. Nexus S phone, Nougat 25, Android 7.1.1, name it as: Nexus_S_API_25, and run the sample test on this new created emulator.
