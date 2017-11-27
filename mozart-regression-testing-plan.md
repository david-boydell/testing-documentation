---
layout: page
title: Mozart Regression Testing Plan
---

Table of Contents
-------

-   [Purpose](#purpose)
-   [Browser Support](#browser-support)
-   [Release on Test](#release-on-test)
    -   [Release PR Testing](#release-pr-testing)
    -   [Manual Checks](#manual-checks-on-test)


-   [Release on Live](#release-on-live)
    -   [Manual Checks](#manual-checks-on-live)


Purpose
-------

The aim of this regression testing plan is to outline all of the things which will be tested on each of the environments as Mozart releases progress through the deployment environments to live. This document should be modified and adapted as required by each of the testers in order to keep the document relevant and useful.

Browser Support
---------------

Regression testing across browsers should be performed based on the [latest stats for News & World Service](https://confluence.dev.bbc.co.uk/display/news/Supported+Browser+Versions)

Based on the stats regression testing will cover the top 3 most popular mobile and desktop browser:

**Mobile:** Opera Mini, Chrome on Android, Safari on iOS
**Desktop:** Chrome, Firefox, IE11

Release on Test
---------------

#### Manual checks on test

-   General Functionality

    -   Check that the site is rendered without any issues - <http://www.test.bbc.co.uk/news>
    -   Check that there are no 500 errors.This can be done by opening firebug>console tab - <http://www.test.bbc.co.uk/news>
    -   Check if there are any JS errors on the page - <http://www.test.bbc.co.uk/news>
    -   Check adverts are only displayed on the international page (using VPN tool)- <http://www.test.bbc.com/news>
    -   Disable JS and check that the site is rendered without issues.
    -   Check share tools work as expected

    -   Topic pages

    -   <http://www.test.bbc.com/gahuza/topics/ba90754a-9033-4e9c-990b-d1139e5070a3>
    -   <http://www.test.bbc.com/gahuza/topics/e68c5b82-50e8-47d8-953c-bf61a2de0a85>


#### Release PR Testing

-   **ACTION** : The PR(s) needing to be released should be discussed between the testers on #web_testers on Slack or via the developer in the appropriate channel and it should be agreed which ones require an additional check on the test environment based on risk, tester resource and time.
-   **VERIFY** : The PR(s) which require additional testing on test should be retested by the tester who originally tested them, unless they are unavailable in which case it will have been agreed between the testers as to who will cover what.

Release on Live
---------------

#### Manual Checks on live

-   Regression on LIVE just requires a quick sanity check across the News Front Page and topic pages that are currently live to ensure that nothing has broken.

-   Run sanity checks on device and desktop browsers for playback on Video and Audio files

-   Sanity Check Sites

	- 	News Front Page

    -   <http://www.bbc.co.uk/news>


    -   Topic pages

    -   <http://www.bbc.com/gahuza/topics/ba90754a-9033-4e9c-990b-d1139e5070a3>
    -   <http://www.bbc.com/gahuza/topics/e68c5b82-50e8-47d8-953c-bf61a2de0a85>

