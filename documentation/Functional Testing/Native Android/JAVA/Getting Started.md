### Prerequisite
Before configuring Flank and starting your Android test jobs, ensure [Python (>= 2.7.x)](https://www.python.org/downloads/) is installed on your local or CI slave, learn more [here](https://cloud.google.com/sdk/downloads). 
 
### Configuration files

#### config.properties (optional but recommended)
The `config.properties` file is used when you need to customize the Flank tests, all options can be seen [here](https://github.com/TestArmada/flank#configure-flank).

#### service-account.json (optional but recommended)
The file to provide `GCloud/Firebase` auth information, [learn more](https://cloud.google.com/sdk/gcloud/reference/auth/activate-service-account). Sample:
```json
{
  "type": "service_account",
  "project_id": "Your Firebase project id",
  "private_key_id": "Your private key id",
  "private_key": "Your private key",
  "client_email": "The client email in Firebase",
  "client_id": "The client id in Firebase",
  "auth_uri": "https://accounts.google.com/o/oauth2/auth",
  "token_uri": "https://accounts.google.com/o/oauth2/token",
  "auth_provider_x509_cert_url": "https://www.googleapis.com/oauth2/v1/certs",
  "client_x509_cert_url": "https://www.googleapis.com/robot/v1/metadata/x509/walmart-fb668%40appspot.gserviceaccount.com"
}
```
If not set, the Flank test will default point to default Walmart Firebase project `walmart-fb668`.

#### .looper.yml (required in looper) 
If you need run your test in a CI environment like looper, a looper config file is needed, learn more [here](http://looper.walmart.com/docs/general/looper-yml.html).
 
#### Environment variables 
All environment variables can be found in the [Developer Guide](https://gecgithub01.walmart.com/otto/docs/blob/new-portal/Functional%20Testing/Native%20Android/JAVA/DeveloperGuide.md#environment-variables)
 
#### Looper integration: 
In looper you can inherit from the Flank base looper job in your `.yml` file: `inherit: 'job://otto-Android_native'` it will include all default environment variables, can override them in your `.yml` anytime, or customize environment variables yourself from the beginning. 
 
##### .looper.yml sample
```yml
inherit: 'job://otto-Android_native'

envs:
  global:
    variables:
      APK_PATH: ./ExampleTestProject_AndroidStudio/app/build/outputs/apk/app-debug.apk
      TEST_APK_PATH: ./ExampleTestProject_AndroidStudio/app/build/outputs/apk/app-debug-androidTest.apk
      PACKAGE: ''
      #FAIL_JOB_ON_TEST_FAIL: false

flows:
  default:
    - ./apk_build.sh
    - shell (name run_tests): |
           curl --header "Authorization: token ${GH_API_TOKEN}" \
           --header "Accept: application/vnd.github.v3.raw" \
           --location https://gecgithub01.walmart.com/api/v3/repos/otto/scripts/contents/looper/flank/flank.sh?ref=${BUILD_URL_REF} | bash

```

##### Tests results
The results are published to [slack](https://walmart.slack.com/messages/android_test).

Script will exit with error code 1 if there are any test failures, which means that it will fail the looper build.

### Manual setup
Manual setup is as easy as automation, just follow steps:

1. Export all required environment variables
1. **Recommended step:** Create `config.properties` followed above instruction
1. **Recommended step:** Create `service-account.json` followed above instruction
1. Run scripts `curl --header "Authorization: token ${GH_API_TOKEN}" --header "Accept: application/vnd.github.v3.raw" --location https://gecgithub01.walmart.com/api/v3/repos/otto/scripts/contents/looper/flank/flank.sh?ref=${BUILD_URL_REF} | bash`

#### Manual setup sample
``` 
#!/usr/bin/env bash
export GH_API_TOKEN=2a73a73566c54ee7152e1698374b9fd497c635df
export APK_PATH=./build/outputs/apk/*-debug.apk
export TEST_APK_PATH=./build/outputs/apk/*-debug-androidTest.apk
export PACKAGE=''
#export FAIL_JOB_ON_TEST_FAIL=false
export BUILD_URL_REF='flank_beta'
curl --header "Authorization: token ${GH_API_TOKEN}" \
--header "Accept: application/vnd.github.v3.raw" \
--location https://gecgithub01.walmart.com/api/v3/repos/otto/scripts/contents/looper/flank/flank.sh?ref=${BUILD_URL_REF} | bash
```