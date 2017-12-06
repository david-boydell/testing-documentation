---
layout: page
title: P1 Regression Testing Split
---

WHEN SHOULD THE P1 SCRIPT BE USED?
---------------------------------

This aim of this script is to provide a high level regression across BBC News and World Services during an expedited release.

WHICH BROWSERS SHOULD BE TESTED ON?
---------------------------------
Based on the stats regression testing will cover the most popular mobile and desktop browser:

**Mobile for News:** Safari (iOS)
**Mobile for World Service:** Chrome (Android)
**Desktop for News & World Service :** Chrome

TEST
----
-   Automation
    -   Salvo
    -   Linkey
    -   Automation Regression Tests
-   Release PR Testing
    -   Any PRs which make up the P1 release should be tested again to ensure everything is working as expected.
-   Functionality Set A:
    -   General Functionality
    -   AV Page
    -   Live Event Component
    -   Topic pages
STAGE
-----
-   Automation
    -   Salvo
    -   Linkey
-   Functionality Set A:
    -   General Functionality
    -   AV Page
-   Functionality Set B:
    -   Sanity Check Sites
LIVE
-----
-   Automation
    -   Linkey
-   Functionality Set A:
    -   Video & Audio
    -   Sanity Check Sites


Linkey and Salvo
---------------

When performing regression across TEST and STAGE make sure to run the Linkey and Salvo tests. On Live we just need to run Linkey.

-   Salvo (Test) :

    -   **INFO** : The salvo test may have already been run as part of the build to test process. If they have then the 'Last Success' time against each of the jobs in the [Salvo Workspace](https://jenkins.news.tools.bbc.co.uk/view/Responsive%20News%20-%20Salvo%20Tests%20-%20TEST/) will indicate this.
    -   **ACTION** : **IF** the Salvo tests have **NOT** already been run then the [salvo-test--runner](https://jenkins.news.tools.bbc.co.uk/view/Responsive%20News%20-%20Salvo%20Tests%20-%20TEST/job/salvo-test--runner/) job should be run, this job kicks off all of the salvo tests which run against the test environment.
    -   **VERIFY** : That each of the salvo test jobs have run successfully. They can be seen here: [Salvo Workspace](https://jenkins.news.tools.bbc.co.uk/view/Responsive%20News%20-%20Salvo%20Tests%20-%20TEST/)
    -   **COMMUNICATE** : Assuming all of the tests pass then a message should be posted on the #release channel on Slack to state that the salvo tests have passed.

-   Linkey (Test):

    -   **ACTION** : The linkey tests should be run by clicking on 'Build Now' against the [Linkey test job](https://jenkins.bbc.co.uk/job/linkey-test/)
    -   **VERIFY** : That the job completes successfully
    -   **COMMUNICATE** : Assuming the tests pass then a message should be posted on the #release channel on Slack to state that the linkey tests have passed.

-   Salvo (Stage):

    -   **ACTION** : Run then the [salvo-stage--runner](https://jenkins.news.tools.bbc.co.uk/view/Responsive%20News%20-%20Salvo%20Tests%20-%20STAGE/job/salvo-stage--runner/) job should be run, this job kicks off all of the salvo tests which run against the stage environment.
    -   **VERIFY** : That each of the salvo test jobs have run successfully. They can be seen here: [Salvo Workspace](https://jenkins.news.tools.bbc.co.uk/view/Responsive%20News%20-%20Salvo%20Tests%20-%20STAGE/)
    -   **COMMUNICATE** : Assuming all of the tests pass then a message should be posted on the #release channel on Slack to state that the salvo tests have passed.

-   Linkey (Stage):

    -   **ACTION** : The linkey tests should be run by clicking on 'Build Now' against the [Linkey stage job](https://jenkins.bbc.co.uk/job/linkey-stage/)
    -   **VERIFY** : That the job completes successfully
    -   **COMMUNICATE** : Assuming the tests pass then a message should be posted on the #release channel on Slack to state that the linkey tests have passed.

-   Linkey (Live):

    -   **ACTION** : The linkey tests should be run by clicking on 'Build Now' against the [Linkey live job](https://jenkins.bbc.co.uk/job/linkey-live/)
    -   **VERIFY** : That the job completes successfully
    -   **COMMUNICATE** : Assuming the tests pass then a message should be posted on the #release channel on Slack to state that the linkey tests have passed.

Services
-------

-   [Politics](#politics)
-   [News](#news)
-   [World Service](#world-service)