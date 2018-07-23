1. **Install and setup GCloud SDK**

    Flank will download GCloud SDK, unzip and install it, to make sure all components in installation phase works, TDK sets proxy for GCloud SDK.

1. **Setup required envs by default**

    To make TDK works with essential components, Flank setup required envs by default, which could be easily override by user, env list at [here](../../API%20Guide.md#Environment%20variables).

1. **Download GCloud Auth json file**

    Download default Auth info file which described at [here](../../API%20Guide.md#service-account.json), define your own auth json file and put the file url on Github to env `SERVICE_ACCOUNT_URL`.

1. **Auth GCloud SDK**

    Once the auth file is downloaded, it will auth the GCloud SDK by the info provided by the file.

1. **Install Flank.jar**

    Download `Flank.jar` to run tests by Flank.

1. **Initialize Flank configurations**

    This step will check if any default/required configurations has not set, if so, the script will set them to default values.

1. **Run tests by Flank**

    Run tests by Flank, and output all logs from Flank.

1. **Post results to Slack and UI dashboard**

    After tests done, TDK will post the result xml files to designated Slack channel (#android_test by default) and TestArmada UI dashboard.

