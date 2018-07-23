#### Prerequisites
* Install [Node.js](https://nodejs.org/en/download/) and **NPM** (npm is distributed with [**Node.js**](https://nodejs.org/)- which means that when you download Node.js, you automatically get npm installed on your computer)
* To get the Walmart internal npm packages, you need to follow the steps: https://sde.walmart.com/docs/proximity/npm.html#downloading-packages
### Achitecture and how it works

![TDK Architecture](../../../images/Flank.png?raw=true)

The TDK connect with Google Firebase to run the tests on cloud based on the configuration provided like devices, shard etc. so in your Android project.

1. **Build project**

    Now we are ready to use Native Android TDK, it uploads built apks to Firebase to run tests, so we need to build the projects into `apks`, sample code:

    ``` bash
    #!/usr/bin/env bash
    ./gradlew assembleDebug
    ./gradlew assembleDebugAndroidTest
    ```

1. **Setup authorization information**

    first we need setup authorization information by `service-account.json` file, the TDK script will create one for you, but you can always create a customized one, details at [here](../../Getting%20Started.md#service-accountjson-optional-but-recommended).

1. **Setup Flank config information**

    After authorize to Google Cloud SDK, we are able to connect to Firebase, the next step we need is config Flank information by a file  `config.properties` under the root directory, all options listed at [here](https://github.com/TestArmada/flank#configure-flank), this will be explained at [Advanced config of the TDK](./Advanced%20config%20of%20the%20TDK.md).

1. **Run tests**

    We have two ways to run the tests:
    1. Simply run `Flank.jar` which explained at [Run Tests](https://github.com/TestArmada/flank#run-tests).
    2. Run TDK script

        export essential envs and run the script.

        ```bash
        export GH_API_TOKEN=${YOUR_GITHUB_TOKEN}
        export APK_PATH=${APK_PATH}
        export TEST_APK_PATH=${TEST_APK_PATH}
        curl --header "Authorization: token ${GH_API_TOKEN}" \
        --header "Accept: application/vnd.github.v3.raw" \
        --location https://gecgithub01.walmart.com/api/v3/repos/otto/scripts/contents/looper/flank/flank.sh?ref=flank_beta \
         | bash
        ```

        The TDK provides well organized scripts to handle all of works left based on files from above, steps in this phase will be explained in [How Flank works](./How%20Flank%20Works.md).

1. **Post actions**

    During the process and after tests done, TDK will provdes detailed logs in the console and XML reports under `./results`.