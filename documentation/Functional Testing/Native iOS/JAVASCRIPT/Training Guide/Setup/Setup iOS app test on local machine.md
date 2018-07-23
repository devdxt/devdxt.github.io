New to native iOS app testing? No worry, you don’t need to know much to set it up. Let's get your first native iOS app test up and running in a couple of minutes.

###  Setup iOS app test on local machine

#### Prerequisites:
* Install [Xcode 9.2](https://developer.apple.com/download/)
* Install [Node.js](https://nodejs.org/en/download/) and **NPM** (npm is distributed with [**Node.js**](https://nodejs.org/)- which means that when you download Node.js, you automatically get npm installed on your computer)
* Check that you have at least **npm** version 3 or above (required by *appium@1.7.x*):
```bash
$ npm --version
# If not, install npm3
$ npm install -g npm@3
```
* To get the Walmart internal npm packages, you need to follow the steps: https://sde.walmart.com/docs/proximity/npm.html#downloading-packages
* Please map **dev.walmart.com** to **127.0.0.1** in your host file

#### Setup Steps:
* Get the sample code and install the node package dependencies:
```bash
# Create a workspace and get the smaple code
$ git clone git@gecgithub01.walmart.com:dxt/boilerplate-nightwatch-mobile.git
$ cd boilerplate-nightwatch-mobile 
$ npm install
$ npm install appium@1.7.2
$ npm install wd
```
* Verify all the required items are setup properly by running appium-doctor:
```bash
# install appium-doctor (may require sudo)
$ npm install appium-doctor -g
# check that all iOS dependencies are set up correctly
$ appium-doctor --ios
```
* Download [Walmart app](http://gec-maven-nexus.walmart.com/nexus/service/local/artifact/maven/redirect?r=pangaea_snapshots&g=com.walmart.ios.development-qa-nightly&a=Walmart.app&v=LATEST&p=zip) and renamed to **Walmart.zip**. Unzip it under **./app** directory, delete ***Users*** folder. Compress ***./app/Walmart*** to **./app/Walmart.zip**, replace the the original one
* Or get the Walmart.app by using the following command option:
``` bash
curl -L 'http://gec-maven-nexus.walmart.com/nexus/service/local/artifact/maven/redirect?r=pangaea_snapshots&g=com.walmart.ios.development-qa-nightly&a=Walmart.app&v=LATEST&p=zip' > app/Walmart.zip && unzip -o app/Walmart.zip -d app/ && rm -rf app/Users app/Walmart.zip && zip -r app/Walmart.zip app/Walmart.app
```
* Please make sure you have iPhone 8, iOS 11.2 simulator before execute the sample test. 
* If you would like to try out some different simulators, please modify the ***appiumiosapp*** part in **.conf/nightwatch.json** file.
* Try the sample test:
```bash
$ npm run test:ios
```
* If you don't have SauceLabs credential , please remove this line in ***./magellan.json*** file:
```bash
"testarmada-magellan-saucelabs-executor"
```