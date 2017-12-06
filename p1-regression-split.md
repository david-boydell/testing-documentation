---
layout: page
title: P1 Regression Testing Split
---

WHEN SHOULD THE P1 SCRIPT BE USED?
---------------------------------

The aim of this script is to provide a high level regression across BBC News and World Services during an expedited release.

WHICH BROWSERS SHOULD BE TESTED ON?
---------------------------------
Based on the stats regression testing will cover the most popular mobile and desktop browser:

**Mobile for News:** Latest Safari (iOS)
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
