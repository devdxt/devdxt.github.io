#### Environment variables

Variable | Description | Required | Default Value
-------- | ----------- | -------- | -------------
GH_API_TOKEN | Token used to fetch files in github | Yes
APK_PATH | Path of the main apk file | Yes
TEST_APK_PATH | Path of the test apk file | Yes
PACKAGE | Package name of test cases to execute, if not defined all tests are executed
JAVA_OPTS | Path to set proxy for gradle connection | Yes in Looper and not `inherit: 'job://otto-Android_native'`
FLANK_VERSION | Version of Flank | | 1.5.0
GCLOUD_VERSION | Version of google-cloud-sdk | | 176.0.0
OSTYPE | OS type, support `linux-gnu` and `darwin` | | linux-gnu
SLACK_TOKEN | Bot token to use to publish the test results to slack. Default to token of android_test_bot.
SLACK_CHANNEL | Slack channel to publish the test results. Defaults to [#android_test]((https://walmart.slack.com/messages/android_test)).
FAIL_JOB_ON_TEST_FAIL | when set to `false`, the looper job will not fail if no error in Flank scripts and even there's failed test cases, this is used when need to show the Junit tests results in looper job main page for the first time. | | true
BUILD_URL_REF | branch to specify version of Flank scripts | | flank_beta (only one valid for now)
SERVICE_ACCOUNT_URL | the URL to download the service_account.json for tests. | recommended


#### conifg.properties
The config.properties file is used when you need to customize the Flank tests, all options can be seen at [configure-flank](https://github.com/TestArmada/flank#configure-flank).

#### service-account.json
All options in `service-account.json` are in thi sample:
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
Learn more at [GCould auth doc](https://cloud.google.com/sdk/gcloud/reference/auth/activate-service-account).