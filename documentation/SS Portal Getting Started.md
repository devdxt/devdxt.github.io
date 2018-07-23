## Self Service Portal Getting Started Guide

### Access

Use of the Self-Service Portal (S.S. Portal) requires logging in with the same credentials you use to log in to JIRA, GEC Github and other internal services. Users must be granted permissions to view the UI, which is handled when a team is onboarded.

If you are having issues logging in, please file a ticket on the DXT [service desk](https://jira.walmart.com/servicedesk/customer/portal/1422/create/3640) with your user ID and the repository of your team (e.g. *R-Discovery/product*).

### Viewing your project

After logging in, a list of projects is presented in the left menu.

![list_of_projects]

Clicking on your project name will display a workspace view offering access to your configured test plans:

![workspace_view]

### Reporting

From the workspace view, you can access the reporting view for any test plan by clicking "View Reporting" on the test plan card.

This will show a summary view of the test plan:

![summary_view]

#### Test Case Health

This panel shows a breakdown of test case passes and fails for the time period displayed on the panel. This gives you insight in to the overall health of your test suite in recent runs and how the results are trending.

#### Test Run Execution Time

Displays a comparison of the runs in the time period denoted on the panel, showing how long each run took in the testing phase.

#### Test Cases

Shows the number of test cases executed across each run in the time period displayed on the panel.

#### All Test Runs

A list of test runs in reverse chronological order (latest to oldest) with overall result of the run displayed.

You can use the "Filter Test Runs by Date" option to show only test runs on a specified date (click on "Filter Test Runs by Date" to show a date picker):

![date_picker]

Additionally, typing in the "Search by Test Run Name, Commit ID or PR #" field allows you to easily locate a specific run:

![search_by_test_run]

Clicking on a run will show the reporting view for that run specifically:

![reporting_view]

#### Health Across Test Cases

Shows the breakdown of passing and failing test cases in the run.

#### Test Case Performance

On the left, this shows the 5 test cases that took the longest to execute. Hover over the browser icon to the right of the execution time to see which browser the test case ran in.

On the right, this shows the 5 test cases that required the most retries to complete. Again, hovering over the browser icon shows the browser that the test case ran in.

![test_case_performance]

#### Test Cases

This panel shows the individual test cases in the run, and a summary of pass/fail per browser.

Clicking "All Status" will allow filtering to show Passing, Failing or All test cases.

![test_case_status]

Clicking "All browsers and devices" shows a list of the browsers in the run, which allows filtering to just the results from that browser.

![all_browsers_and_devices]

The pagination controls at the bottom of the panel provide access to further results:

Clicking on an individual test case provides the summary view for that test case:

![pr_verify]

The browser icons on the left can be clicked to show a summary of the result for that browser.

Clicking "Results | CI Jobs" will take you to the Looper job for the run, and "Play Recording" will take you to the video recording of the test execution on SauceLabs.

![results_ci_jobs]

[list_of_projects]: ./images/self-service/list_of_projects.png?raw=true "List of Projects"
[workspace_view]: ./images/self-service/workspace_view.png?raw=true "Workspace View"
[summary_view]: ./images/self-service/summary_view.png?raw=true "Summary View"
[date_picker]: ./images/self-service/date_picker.png?raw=true "Date Picker"
[search_by_test_run]: ./images/self-service/search_by_test_run_name.png?raw=true "Search by Test Run"
[reporting_view]: ./images/self-service/reporting_view.png?raw=true "Reporting View"
[test_case_performance]: ./images/self-service/test_case_performance.png?raw=true "Test Case Performance"
[test_case_status]: ./images/self-service/test_case_status.png?raw=true "Test Case Status"
[all_browsers_and_devices]: ./images/self-service/all_browsers_and_devices.png?raw=true "All Browsers and Devices"
[pagination]: ./images/self-service/pagination.png?raw=true "Pagination"
[pr_verify]: ./images/self-service/pr_verify.png?raw=true "PR Verify"
[results_ci_jobs]: ./images/self-service/results_ci_jobs.png?raw=true "Results CI Jobs"

### Support

The Self Service UI is supported by the DXT team via the [service desk](https://jira.walmart.com/servicedesk/customer/portal/1422) and for questions, please see #testautomation on Slack.
