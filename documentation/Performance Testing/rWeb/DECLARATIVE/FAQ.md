## What advantages does Rapido provide over other online performance tools?
    _Answer:_ 

    Here are few advantages : 
    - Rapido provides performanc testing as a part of Contionous Delivery, that is, it integrates with your repo and runs performance tests as part of PR Verify, Master Verify or scheduled build.
    - Rapido gives you an ability to catch the performance regressions of your app right at the gate, which gives you an opportunity to fix any performance bugs where it can be fixed easily.
    - Rapido provides an infrastructure to run web and mweb performance tests in Walmart's environment. The set up is done in Walmart's oneops environment which enables easy integration and on-boarding of any new projects. 
    - Provides data transformation tools and and visualization which comes with the package when you on-board on Rapido.  
    - Easy set up, onboarding takes around 2 hours.
    - Rapido runs the tests in laboratory conditions, meaning, they run on VMs which are monitored for resources (CPU, memory, and network resources). We make sure that the VMs are isolated and are not affected by any noise that affect the tests. 

## How long does it take to onboard on Rapido?
    - Around 2-3 hours if you are an electrode project.

## Can I run Rapido in my local environment?
    - Yes, Rapido can be executed on your local by simply following the above instructions.  You can also use
  https://gecgithub01.walmart.com/rapido/rapido_local to run rapido locally. This repo has interactive features available which sets up rapido on its own to get a head start.

## Are the performance tests reliable?
    - Performance tests are results recieved from the browser API itself. There could be few variances in some of the metrics delivered by sitespeed.io, but mostly the results are reliable when you run the tests with a mock server serving your application. We have seen large variances when a live backend is used for testing and that is because of obvious reasons.  That being said, we understand that performance, for many teams, would mean running tests on whole application with backened services involved. We provide following recommendations when it comes to running web performance tests :

      - PR Verify for front end code  - Run with mock server
      - Master Verify for front end code - Run with mock server
      - Prod Verify for front end code - Run without mock server.

  Please note that the Prod verify tests will have more flakiness in metrics becasue they will be affected by various factors, for example, network delays, geographical location, network speed and availability of third party content. The production tests can give you an idea of how your application is performing in the production and you can look for big fluctuations on the metrics to give you an idea if anything bad is happening with your application.

## How is Rapido results different from Real User Metrics (RUM) results?
    - RUM metrics are measurements which are captured by beacon data when real users browse and perform click actions on the production website. Rapido metrics are measurements produced by synthetic performance testing, in which we create an environment for testing and run the application performance test in tighly monitored environment.  While RUM data is very useful for measuring the performance of your website in real world, it is a completely different measurements from the metrics produced in synthetic testing.  The reasons are obvious, testing in real world brings a lot of factors into play. Some of them are : network availability, geographic location, device resources etc.  In case of synthetic testing, the motive of testing is itself very different. The motivation here is to test performance of the app before it goes out in the real world. This  provides us an opportunity to fix the performance regressions before they are used by real users.
