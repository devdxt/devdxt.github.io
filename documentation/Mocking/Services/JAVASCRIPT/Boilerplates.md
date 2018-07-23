
## Boilerplate with a web app
This [boilerplate](https://gecgithub01.walmart.com/otto/boilerplate-mocking) application is a web app built using Walmart's public APIs to locate stores near a zip code. The responses are mocked using the Mock Server. 

1. To run against live-service, use the following commad:
    
    `npm run start-live`

1. To run against mock-service, use the following commad:
    
    `npm run start-mock`
   
More details could be found in the `README` for the [boilerplate](https://gecgithub01.walmart.com/otto/boilerplate-mocking)

<br>

## Parallel Sessions boilerplate/demo
This [Boilerplates](https://gecgithub01.walmart.com/otto/boilerplate-mocking-demo) starts a mock server and demonstrates how the same rest end point could be used to return different datasets while running test cases in parallel. In this example, two test cases execute in parallel and access the Rest endpoint `/api/homepage` after setting two different variants on the same route using sessions. 

Test cases receives mocked `html` responses, one for `jet.com` homepage and other for `walmart.com` homepage.

<br>

## Project Reference
This is an actual [project](https://gecgithub01.walmart.com/R-Discovery/home) for your reference from disocery team that uses mock server to run test cases.
