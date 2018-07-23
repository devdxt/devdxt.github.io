### Config `.looper.yml` in your project

First let's see how a minimum full config looks like:

```yaml
    inherit: 'job://otto-Android_native'

    tools:
        android:
            - tools
            - platform-tools
            - android-25
            - build-tools;25.0.1
            - extras;android;m2repository
        gradle: 4.2.1

    envs:
        global:
            variables:
                APK_PATH: ${YOUR_APK_PATH}
                TEST_APK_PATH: ${YOUR_TEST_APK_PATH}
                PACKAGE: ''
                #ADMIRAL_PROJECT: Boilerplate Android
                #FAIL_JOB_ON_TEST_FAIL: false

    flows:
        default:
            - if not prepare apks, build them here, make sure they are under ${YOUR_APK_PATH} and ${YOUR_TEST_APK_PATH}
            - shell (name run_tests): |
                curl --header "Authorization: token ${GH_API_TOKEN}" \
                --header "Accept: application/vnd.github.v3.raw" \
                --location https://gecgithub01.walmart.com/api/v3/repos/otto/scripts/contents/looper/flank/flank.sh?ref=${BUILD_URL_REF} \
                | bash
```
1. First, it's recommended that add `inherit: 'job://otto-Android_native'` at the first line of your `.looper.yml` it will handle all default envs for you if you missed some essential envs.

1. Next add Android and Gradle tool stack in looper as described for [Android tool](http://looper.walmart.com/docs/tools/android.html) and [Gradle tool](http://looper.walmart.com/docs/tools/gradle.html).

1. Setup essential `envs`, reference by the [env list](../../API%20Guide.md#Environment%20variables), `APK_PATH` and `TEST_APK_PATH` is the two you must provided, `FAIL_JOB_ON_TEST_FAIL` is used when results chart plugin is installed in the looper job, and it needs the build at least passed once.

    If setup env `ADMIRAL_PROJECT`, e.g. `Boilerplate Android`, TDK will report to admiral2 dashboard after tests done, and you can check at http://admiral2.walmart.com/.

1. Call looper flows
    1. Build your apk and test apk under the path same under `env` variables
    1. Call TDK scripts as it is, recommend define your own `GH_API_TOKEN`.

1. Last step, commit and push your `.looper.yml` to the repo, then let's goto [Build the looper job](./Build%20the%20looper%20job.md).