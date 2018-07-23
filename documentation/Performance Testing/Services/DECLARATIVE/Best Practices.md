### **JMeter Scripting best practices**

1.	Avoid excessive logging as it severely impacts the throughput of load agents. Restrict your logging to error conditions only.
2.	Total number of users in the test plan is per load agent. Number of users defined in the test plan and the number of load agents used is what defines the total number of users in the test.
3.	JMeter versions are not forward compatible. To avoid compatibility issues, download the JMeter bundle from TestArmada self-service portal.
4.	For web-based application testing, do not download the static assets on the pages. These assets are downloaded from CDN or are served from a separate web server which do not have any bearing on the application under test. Enabling this will significantly impact the test results and throughput of load agents.
5.	Choose think time and pacing time between two successive transactions wisely. This is essential for mimicking real time usage.
6.	For service level performance testing, think time and pacing time do not matter much as the focus of testing is on application throughput and latency.
7.	JMeter captures response times for all calls within a transaction including individual API calls. Wrapping sub-transactions around each call within a transaction is not required.
8.	Avoid unnecessary pre and post processors as they consume resources on the load agent
9.	Randomize selection of test data from data files for unique data in each iteration. JMeter controllers do not assign unique test data to each user as is the case with few other tools.


### **Execution best practices**

1.	Avoid running JMeter console on your desktop or any machine on the corpnet. This will produce inaccurate results. JMeter console should only be used to unit test your scripts by running with 2 or more users.
2.	Limit the number of virtual users to a maximum of 300 per load agent. Assumption here is the agent runs on a large VM and does not have any memory intensive computation within the script.
3.	View Results tree listener should be disabled as results are available in the portal
4.	Do not add any listeners to your script other than the specified Kafka listener. This is essential to view live results during the course of test execution.
5.	Disable all graphs and JTL file generation from your test plan. Test results can be viewed live in the portal and the same is archived in the Data Insights DB.
6.	Monitor test logs and test agent resource utilization for your test on the links below:<br/>
a.	**Splunk:** [http://dfw-logsearch01.prod.walmart.com](http://dfw-logsearch01.prod.walmart.com) <br/>
b.	**Medusa:** [https://medusa.walmart.com/](https://medusa.walmart.com/dashboard/db/nextgen-perf_prod?refresh=5m&orgId=1) <br/>
7.	Save test logs locally from Splunk if you need it beyond 14 days from the execution date <br/>

