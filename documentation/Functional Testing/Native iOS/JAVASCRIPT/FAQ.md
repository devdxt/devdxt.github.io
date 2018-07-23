## I'm having npm install failure, what should I do?

Please make sure that you're using compatible node and npm. Check versions by node -v and npm -v

To install Node and NPM, click [here](https://nodejs.org/en/download/). **NPM** is distributed with [**Node.js**](https://nodejs.org/)- which means that when you download Node.js, you automatically get npm installed on your computer.

## Which magellan command should I use to launch my test?

Please read magellan help by ./node_modules/.bin/magellan --help first. If you cannot find what you want there, or if you're still not sure, please reach us in slack channel lised below

## How should I run my test in different devices?

If you want to test locally, please make sure corresponding dev tools are installed correctly. Also for android please make sure a proper AVD is set.

## How should I debug my test?

Please use [appium desktop app](https://github.com/appium/appium-desktop) to get your element or coordinates.

## Can I have this feature?

If you are asking for a customized command, please check if similar command exists in testarmada.io#API and nightwatch first. Or, if you are asking for a feature like data tools, or any other stuff that you think is useful, please ping us in slack channel.

## What to do if I cannot download and install some certain node packages

If it's Walmart internal npm packages are the problem ones, please follow the steps listed [here](https://sde.walmart.com/docs/proximity/npm.html#downloading-packages).

**Bentonville**: if you cannot reach a certain public npm packages because of the proxy issue. You can either use the sample project setup on looper to get your tests run on CI, or ask people to share their node packages via Box.

## Cannot check in your changes

Please make sure you have write access for the repo, and you need to set the SSH key right. To check for exiting SSH Keys, click [here](https://help.github.com/articles/checking-for-existing-ssh-keys/).  Generate a new SSH key and adding it to the ssh-agent, click [here](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/).  Add a new SSH key to your GitHub account, click [here](https://help.github.com/articles/adding-a-new-ssh-key-to-your-github-account/).