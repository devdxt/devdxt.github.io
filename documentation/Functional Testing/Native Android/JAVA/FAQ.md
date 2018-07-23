## How can I use Flank to begin my Android tests?

See [Getting started](https://gecgithub01.walmart.com/otto/docs/blob/new-portal/Functional%20Testing/Native%20Android/JAVA/GettingStarted.md) and [Developer Guide](https://gecgithub01.walmart.com/otto/docs/blob/new-portal/Functional%20Testing/Native%20Android/JAVA/DeveloperGuide.md) for help.

<br>

## Are there any example projects I can have a look at?

Yes please see [boilerplate-android-espresso-automation](https://gecgithub01.walmart.com/otto/boilerplate-android-espresso-automation/tree/looper) and follow the `README`, also please see [this looper example job](https://ci.walmart.com/view/Mobile%20looper%20test/job/boilerplate-android-espresso-automation/). 

<br>

## Where can I download `flank.jar`?

You can either download flank from [here](https://dl.bintray.com/flank1/Flank/Flank-1.5.0.jar) or use the following command:

``` bash
curl -o Flank.jar --proxy http://gec-proxy-svr.homeoffice.wal-mart.com:8080/ \
--location --fail https://dl.bintray.com/flank1/Flank/Flank-1.5.0.jar
```

<br>

## Why does gradle timeout in looper?

Please inherit the flank base looper job in your `.looper.yml` file `inherit: 'job://otto-Android_native'` or specify your own proxy via `JAVA_OPTS` variable, `gradle.org` is not whitelisted yet, some dependencies cannot be retrieved from [gradle tool in looper](http://looper.walmart.com/docs/tools/gradle.html).

<br>

## Where do I go to ask questions?

Please join our Slack channel [#otto_flank](https://walmart.slack.com/messages/otto_flank) for more help.