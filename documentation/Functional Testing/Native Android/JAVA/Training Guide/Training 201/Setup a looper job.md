1. **Login to looper system**

    Open any link of https://ci.electrode.walmart.com/ or https://ci.walmart.com/, and login with your SSO credentials

1. **Create a looper job**

    ![new item on looper](../../img/New%20item%20on%20looper.png)
    ![looper name ok](../../img/looper%20name%20ok.png)

1. **Config looper job**

    After create a empty looper job, you'll be automatically redirect to configuration page, drag down to `Looper` section, we'll do some essential configrations here.

    ![config looper](../../img/config%20looper.png)

1. **Config `.looper.yml`**

    Now you're on the page of the looper job you just created, you may see there's an issue here

    ![no looper file issue](../../img/no%20looper%20file%20issue.png)

    This is because the repo and branch you provided just now doesn't has a file named `.looper.yml`, now let's create one in your project, follow next chapter [Config .looper.yml](./Config%20.looper.yml.md).