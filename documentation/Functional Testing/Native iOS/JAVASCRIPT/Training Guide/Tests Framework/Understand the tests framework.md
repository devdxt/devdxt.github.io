### Tests framework structure

####  Recommend practice is **Page Objects Model** Design Pattern. 

In our sample boilerplate: 
 1. Command parameter **--test tests/app.test.js** executes tests in **app.test.js** file. 
2. **Tests** are defined in **.js** files under **.tests/** folder, each file is a test.
3. Locators and function commands are grouped by page/screen, and are put in **./lib/pages/device/** folder.
     E.g in **app.test**, the login step would require elements and commands that are defined in **./lib/pages/ios/login.js** file.  
4. Profiles that are used to execute tests in remote, e.g. SauceLabs, are defined in magellan.json fine.
5. Local browsers are defined in nightwatch.json file, they are used for local simulator tests, and they are not supported in profiles.

####  Where to find mobile commands
 1. When look at commands in page files, e.g. **setMobileElValue()** may look new to you. Those mobile commands are defined in ***./node_modules/testarmada-nightwatch-extra/lib/commands/mobile***.
 2. Assertions, e.g. **mobileElAttrContains()**, are defined in ***./node_modules/testarmada-nightwatch-extra/lib/assertions/mobile***.
 3. To use those mobile commands and assertions, need to add the following lines in nightwatch.json file: 
```bash
  "custom_commands_path": [
    "./node_modules/testarmada-nightwatch-extra/lib/commands/mobile"
  ],
  "custom_assertions_path": [
    "./node_modules/testarmada-nightwatch-extra/lib/assertions/mobile"
  ],
```
 4. You can also add your customized commands into folder **./lib/custom_commands**, to increase code reusability. And please remember to add the path to nightwatch.json file, e.g. 
```bash
  "custom_commands_path": [
    "./node_modules/testarmada-nightwatch-extra/lib/commands/mobile",
    "./lib/custom_commands"
  ],
```

### Quiz
Run mocked iOS app sample test in the local box with a different iOS simulator. 