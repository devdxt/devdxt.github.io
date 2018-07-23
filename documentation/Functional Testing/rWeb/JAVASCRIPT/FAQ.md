## I'm having npm install failure, what should I do?

Please make sure that you're using compatible node and npm. Check versions by node -v and npm -v

To install Node and NPM, click [here](https://nodejs.org/en/download/). **NPM** is distributed with [**Node.js**](https://nodejs.org/)- which means that when you download Node.js, you automatically get npm installed on your computer.

## Which magellan command should I use to launch my test?

Please read magellan help by ./node_modules/.bin/magellan --help first. If you cannot find what you want there, or if you're still not sure, please reach us in slack channel lised below

## How should I run my test in different browsers?

If you want to test locally, Firefox and Chrome would be supported by default no matter which OS you're using. To run test in Safari, you need to follow this article. To run in IE serie, you need a Windows. Or, just simply invoke your test on saucelabs.

## How should I run my test in mobile browser?

Please use Saucelabs.

## How should I debug my test?

Right now we don't have fancy feature like block current execution --> do some variable watch --> resume your test. However, you can add a .pause() command before the command you want to debug, run your test and check selector from either developer tool or firebug from browser. Another option is adding tons of console.log() in your test.

## Why my test passes in one browser but fails in another one?

There are couple of things can impact the test results. Page rendering speed, css selector compatibility, viewport size or even the way element's being rendered. However in most cases the descrepancy is because we're not really simulating user behaviors in the test. For instance, please make sure your code is not clicking on an element that is not in the viewport.

## Can I have this feature?

If you are asking for a customized command, please check if similar command exists in testarmada.io#API and nightwatch first. Or, if you are asking for a feature like data tools, or any other stuff that you think is useful, please ping us in slack channel.

## What to do if I cannot download and install some certain node packages

If it's Walmart internal npm packages are the problem ones, please follow the steps listed [here](https://sde.walmart.com/docs/proximity/npm.html#downloading-packages).

**Bentonville**: if you cannot reach a certain public npm packages because of the proxy issue. You can either use the sample project setup on looper to get your tests run on CI, or ask people to share their node packages via Box.

## Cannot check in your changes

Please make sure you have write access for the repo, and you need to set the SSH key right. To check for exiting SSH Keys, click [here](https://help.github.com/articles/checking-for-existing-ssh-keys/).  Generate a new SSH key and adding it to the ssh-agent, click [here](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/).  Add a new SSH key to your GitHub account, click [here](https://help.github.com/articles/adding-a-new-ssh-key-to-your-github-account/).