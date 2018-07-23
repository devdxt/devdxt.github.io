
You are welcome to contribute to our repo. Our main repos are :

- https://gecgithub01.walmart.com/rapido/operaio
- https://gecgithub01.walmart.com/rapido/plugin-sitespeed  (captures the data from sitespeed and saves it in kairos db)
- https://gecgithub01.walmart.com/rapido/annesso (transforms the sitespeed.io result data to be kairos compatible)

Below is the architecture of how the components of rapido interact with each other:

![architecture](./images/rapido_arch_contribute.png)

## Understanding Rapido Process Flow in Jenkins:
. A Jenkins job is triggered by a change in the application's repository :
  * That job can only run in a specific set of slaves, provisioned to run performance jobs;
  * These slaves are OneOps VMs that include Docker engine, a command line tool named [operaio](https://gecgithub01.walmart.com/rapido/operaio) and the following Docker images:
    * [electrode-app-builder](https://gecgithub01.walmart.com/rapido/pilot/blob/extended/docker/electrode-app-builder/Dockerfile);
    * [otto-mock-server](https://gecgithub01.walmart.com/rapido/pilot/blob/extended/docker/otto-mock-server/Dockerfile): runs the mocking server from the source stored in a given volume;
    * [electrode-app](https://gecgithub01.walmart.com/rapido/pilot/blob/extended/docker/electrode-app/Dockerfile): runs the application from the source stored in a given volume;
    * [sitespeed.io](https://hub.docker.com/r/sitespeedio/sitespeed.io/builds/bwtaeag2jnxi2xk3urfg3tj/): measures application performance;
1. __operaio__ takes a few arguments from the Jenkins jobs and automates the performance measurement workflow; 
1. A Docker container is started from an __electrode-app-builder__ image, where:
  1. Application source is pulled from GitHub;
  1. Dependencies are installed via `npm install`;
  1. Application is built via command provided by app team. As an example `NODE_ENV=production npm run build`;
  1. Result is made available to specified volume;
1. A Docker container is started from an __otto-mock-server__ image, where the mock server is started via `npm run mock-server`;
1. A Docker container is started from an __electrode-app__ image, where:
  1. Environment variables tell the application to run optimized code against mocked services, example: 
    * `NODE_ENV=production`
    * `NODE_APP_INSTANCE=mock`
  1. The host __dev.walmart.com__ is mapped to __otto-mock-server__'s IP;
  1. Application is started command provided by app team. As an example,  `node server/index.js` or `npm run start`
1. A Docker container is started from a __sitespeed.io__ image, which uses Chrome browser to measure performance from the __electrode-app__ container;
1. The collected metrics are forwared to a KairosDB cluster, which is backed by a Cassandra cluster;
1. The collected HAR files are stored into the Cassandra cluster;
1. The __sitespeed.io__ container stops and cleans up;
1. Other containers are stopped and cleaned-up:
  * electrode-app;
  * otto-mock-server;
  * electrode-app-builder;
1. Job stops and Jenkins slave is freed-up;
1. The results can visualized from a Grafana dashboards hosted at https://prod.rapido.walmart.com/;

### Our main modules where you can contribute :
- *Operaio* (https://gecgithub01.walmart.com/rapido/operaio) - This is the runner of the performance tests. It basically starts all the docker containers : electrode-app-builder, electrode-app, otto-mock-server and sitespeed.io to run the performance tests and deliver the test resuls to the kairos db.  If you need to change the way process runs, please contribute to this project.

- *Plugin-sitespeed* (https://gecgithub01.walmart.com/rapido/plugin-sitespeed) - This is the module which captures the data from sitespeed.io and passes it along to *annesso* module to transform the data and publish it to the Kairos db

- *Annsesso*  (https://gecgithub01.walmart.com/rapido/annesso)  - This is the module which transforms the sitespeed results data and does a POST to Kairos db to publish the data.

Contributors are encouraged to make changes and write test cases for any new functionality introduced.