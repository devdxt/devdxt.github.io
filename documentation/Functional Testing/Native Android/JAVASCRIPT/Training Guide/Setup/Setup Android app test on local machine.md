
### Run Android app test in local emulator

- Get the sample code and install the node package dependencies:
```bash
# Create a workspace and get the smaple code
$ git clone git@gecgithub01.walmart.com:dxt/boilerplate-nightwatch-mobile.git
$ cd boilerplate-nightwatch-mobile 
$ npm install
$ npm install appium@1.7.2
```
- Verify all the required items are setup properly by running appium-doctor (only needed for the first time using):
```bash
# install appium-doctor (may require sudo)
$ npm install appium-doctor -g
# check that all Android dependencies are set up correctly
$ appium-doctor --android
```
- Download **Walmart.apk** file from the download link provided in slack channel #builds-wmandroid-core and move it to ./app directory
- Launch the **a71_API_25** AVD in the emulator 
- Try the sample test:
```bash
$ npm run android:app:test
```
- You should be able to see the login test running on the Android Emulator
* If you don't have SauceLabs credential , please remove this line in ***./magellan.json*** file:
```bash
"testarmada-magellan-saucelabs-executor"
```
- In the sample, there is another way to automatically download the Walmart Android app, launch emulator and start the sample test: 
```bash
ANDROID_HOME=AAA AVD_NAME=BBB npm run test:android
```
Please note: the AVD_NAME may different from the AVD manager you see from Android Studio, you can find the right name from the following command:
```bash
${ANDROID_HOME}/platform-tools/emulator -list-avds
```
To know more about emulator commands, please read [this](https://developer.android.com/studio/run/emulator-commandline.html).
