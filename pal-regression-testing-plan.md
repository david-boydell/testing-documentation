---
layout: page
title: PAL Regression testing Plan
---

Table of Contents
-------

- [Purpose](#purpose)
- [Browser Support](#browser-support)
- [Release on Test](#release-on-test)
	- [General checks](#general-checks)
   - [Release PR Testing](#release-pr-testing)
   -  [Manual Checks](#manual-checks)
   		- [General Functionality](#general-functionality)
       - [AV Page](#av-page)
       - [Live Event Component](#live-event-component)
       - [ORB Header and Footer lins](#orb-header-and-footer-links)
       - [Search](#search)
       - [Topic pages](#topic-pages)
       - [RSS Feeds](#rss-feeds)
       - [Contact Us Form](#contact-us-forms)
       - [New Picture Gallery](#new-picture-gallery)
       - [Most Read](#most-read)
       - [Atlas](#atlas)
       - [Sitemaps](#site-maps)
       - [Fonts](#fonts)
       - [CPS Preview](#cps-preview)

- [Release on Stage](#release-on-stage)
	- [General checks](#general-checks)
   -  [Manual Checks](#manual-checks)
   		- [General Functionality](#general-functionality)
       - [AV Page](#av-page)
       - [Live Event Component](#live-event-component)
       - [RSS Feeds](#rss-feeds)
       - [Sanity Check Sites](#sanity-check-sites)

- [Release on Live](#release-on-live)
	- [General checks](#general-checks)
   -  [Manual Checks](#manual-checks)
       - [Sanity Check Sites](#sanity-check-sites)
       - [Check CPS preview for MAPs not retuning 404s](check-cps-preview-for-maps-not-returning-404s)
       - [CPS Preview](cps-preview)


Purpose
-------

The aim of this regression testing plan is to outline all of the things which will be tested on each of the environments as PAL releases progress through the deployment environments to live. This document should be modified and adapted as required by each of the testers in order to keep the document relevant and useful.

Browser Support
---------------

Regression testing across browsers should be performed based on the [latest stats for News & World Service](https://confluence.dev.bbc.co.uk/display/news/Supported+Browser+Versions)

Release on Test
---------------

#### General checks

-   Salvo :

    -   **INFO** : The salvo test may have already been run as part of the build to test process. If they have then the 'Last Success' time against each of the jobs in the [Salvo Workspace](https://jenkins.news.tools.bbc.co.uk/view/Responsive%20News%20-%20Salvo%20Tests%20-%20TEST/) will indicate this.
    -   **ACTION** : **IF** the Salvo tests have **NOT** already been run then the [salvo-test--runner](https://jenkins.news.tools.bbc.co.uk/view/Responsive%20News%20-%20Salvo%20Tests%20-%20TEST/job/salvo-test--runner/) job should be run, this job kicks off all of the salvo tests which run against the test environment.
    -   **VERIFY** : That each of the salvo test jobs have run successfully. They can be seen here: [Salvo Workspace](https://jenkins.news.tools.bbc.co.uk/view/Responsive%20News%20-%20Salvo%20Tests%20-%20TEST/)
    -   **COMMUNICATE** : Assuming all of the tests pass then a message should be posted on the #release channel on Slack to state that the salvo tests have passed.

-   Linkey :

    -   **ACTION** : The linkey tests should be run by clicking on 'Build Now' against the [Linkey test job](https://jenkins.bbc.co.uk/job/linkey-test/)
    -   **VERIFY** : That the job completes successfully
    -   **COMMUNICATE** : Assuming the tests pass then a message should be posted on the #release channel on Slack to state that the linkey tests have passed.

-   Wraith :

    -   **ACTION** : The following Wraith jobs should be started for [News](https://jenkins.news.tools.bbc.co.uk/job/wraith_news_test/) and [World Service](https://jenkins.news.tools.bbc.co.uk/job/wraith_ws_test/)
    -   **VERIFY** : Check the screenshots and investigate any differences highlighted

-   Automated Regression Tests :

    -   **ACTION** : The automated regression checks should be started here: [Regression Testing Browserstack](https://jenkins.news.tools.bbc.co.uk/job/regression-testing-browserstack/build?delay=0sec)
    -   **VERIFY** : View the results and ensure all of the test pass. A link to the results can be seen here: [Automated Regression Results](https://www.browserstack.com/automate/builds/b50af56704de855c096efffe4f72c95990622222)

#### Release PR Testing

-   **INFO** : The PRs can be found under the relevant [milestone](https://github.com/BBC-News/responsive-news/milestones)
-   **ACTION** : The PRs in the current release should be discussed between the testers on #web_testers on Slack and it should be agreed which ones require an additional check on the test environment based on risk, tester resource and time.
-   **VERIFY** : The PRs which require additional testing on test should be retested by the tester who originally tested them, unless they are unavailable in which case it will have been agreed between the testers as to who will cover what.

#### Manual Checks

-    General Functionality

    -   Check that the site is rendered without any issues - [http://www.test.bbc.co.uk/news](http://www.stage.bbc.co.uk/news)
    -   Check that there are no 500 errors.This can be done by opening firebug>console tab - [http://www.test.bbc.co.uk/news](http://www.stage.bbc.co.uk/news)
    -   Check if there are any JS errors on the page - [http://www.test.bbc.co.uk/news](http://www.stage.bbc.co.uk/news)
    -   Check adverts are only displayed on the international page - [http://www.test.bbc.com/news](http://www.stage.bbc.co.uk/news)
    -   Check various indexes work as expected mainly business index which has live event mostly and special reports,explainers,in pictures -\
           [http://www.test.bbc.co.uk/news/business](http://www.stage.bbc.co.uk/news/explainers)\
        [   http://www.test.bbc.co.uk/news/special_reports](http://www.stage.bbc.co.uk/news/special_reports)\
         [  http://www.test.bbc.co.uk/news/in_pictures](http://www.stage.bbc.co.uk/news/in_pictures)\
         [  http://www.test.bbc.co.uk/news/explainers](http://www.stage.bbc.co.uk/news/explainers)
    -   Check all blogs (QBR,the papers etc) are working as expected -  <http://www.test.bbc.co.uk/news/blogs/the_papers?_x_candy_override=https://api.test.bbc.co.uk>
    -   Check correspondent pages(Index and articles) are working as expected -  [http://www.test.bbc.co.uk/news/correspondents/rorycellanjones](http://www.stage.bbc.co.uk/news/correspondents/rorycellanjones) & [http://www.test.bbc.co.uk/news/technology-35863859](http://www.stage.bbc.co.uk/news/technology-35863859)
    -   Check that weather works as expected - [http://www.test.bbc.co.uk/news](http://www.stage.bbc.co.uk/news)
    -   Check local indexes look ok - [http://www.test.bbc.co.uk/news/england/birmingham_and_black_country](http://www.stage.bbc.co.uk/news/england/birmingham_and_black_country)
    -   Disable JS and check that the site is rendered without issues.
    -   Check share tools work as expected

-    AV Page

    -   Check that the video plays properly - [http://www.test.bbc.co.uk/news/world-europe-35881935](http://www.stage.bbc.co.uk/news/world-europe-35881935)
    -   Check that [http://www.test.bbc.co.uk/news/video_and_audio](http://m.stage.bbc.co.uk/news/video_and_audio) is not blank and no 500 errors displayed in the console.
    -   Check that the Related, Most Watched and Top Stories tabs are rendered with data and quick regression around the tabs.
    -   Check that stats are working.
    -   Audio MAP - <http://www.test.bbc.com/persian/tv-and-radio-39252530>
    -   Video MAP - <http://www.test.bbc.com/mundo/noticias/2016/03/160322_video_belgica_bruselas_interior_aeropuerto_zaventem_explosiones_ataques_lv>
    -   OMP Video MAP - <http://www.test.bbc.com/gahuza/35857408>
    -   OMP Video MAP - <http://www.test.bbc.com/japanese/video-35868772>
    -   OMP StoryPage with embedded video - <http://www.test.bbc.com/japanese/35684400>
    -   Live TV - <http://www.test.bbc.com/arabic/tvandradio/2013/05/000000_bbcarabic_livetv> & <http://www.test.bbc.com/persian/tvandradio/2013/08/000001_bbcpersian_livetv>
    -   Live Nitro Radio -  <http://www.test.bbc.com/arabic/bbc_arabic_radio/liveradio>
    -   Nitro Radio Bulletin - <http://www.test.bbc.com/arabic/bbc_arabic_radio/liveradio> (Click a bulletin on the left of the page)
    -   MPS Story Page with with embedded video - [http://www.test.bbc.com/mundo/noticias/2016/03/160313_turquia_explosion_ankara_muertos_ilm](http://www.stage.bbc.com/mundo/noticias/2016/03/160313_turquia_explosion_ankara_muertos_ilm)

    -   Check duration labels render on playable media assets on page

-   Live Event Component

    -   Check that the Live Event component is working as expected (Comments coming through and they are updated based on the latest time) - Live event av avilable on any index when the release is done[ ](http://www.stage.bbc.co.uk/news/live/world-europe-35869266)

    -   Check that the Live Event Component is not blank - <http://www.test.bbc.co.uk/news/live/world-europe-35869266> - if it is blank check this <http://pal.test.bbc.co.uk/news/live/23040381?_x_candy_override=https://api.test.bbc.co.uk>

-    ORB Header and Footer links

    -   <http://www.test.bbc.com/arabic>
    -   Check for localised labels
    -   Link to BBC Id Sign In lands on page - <https://ssl.test.bbc.com/id/ar-SA/signin?ptrt=http%3A%2F%2Fwww.test.bbc.com%2Farabic%2Fsearch%2F%3Fq%3Dtest>
    -   Test interactions with links

-   Search

    -   <http://www.test.bbc.com/arabic/search/?q=test>
    -   Test interactions search box
    -   Test interactions with search results page

-   Topic pages

    -   <http://www.test.bbc.com/gahuza/topics/ba90754a-9033-4e9c-990b-d1139e5070a3>
    -   <http://www.test.bbc.com/gahuza/topics/e68c5b82-50e8-47d8-953c-bf61a2de0a85>

-   RSS Feeds

    -   On [http://www.](http://www.bbc.com/kyrgyz)[test.bbc.com/kyrgyz](http://test.bbc.com/kyrgyz), click through on RSS icon to <http://feeds.bbci.co.uk/kyrgyz/rss.xml>
    -   <https://broker.karanga.test.cloud.bbc.co.uk/persian/rss.xml>
    -   <https://broker.karanga.test.cloud.bbc.co.uk/persian/fullrss.xml>
    -   <http://feeds.bbci.co.uk/japanese/fullrss.xml>
    -   check feeds updates and no encoding errors are displayed

-   Contact Us Form

    -   <http://www.test.bbc.com/urdu/institutional/2011/10/000001_contact_us>
    -   Check for localisation
    -   Successful submission page
    -   Mandatory field form errors

-   New Picture Gallery

    -   <http://www.test.bbc.com/russian/multimedia/2016/03/160330_inpics_nanotecture>
    -   <http://www.test.bbc.com/arabic/multimedia/2016/03/160327_perceptions_beauty_pic_gal>

-   Most Read

    -   <http://www.test.bbc.com/arabic>
    -   <http://www.test.bbc.com/zhongwen/simp/popular/read>
    -   Click through to 'Most Popular' tab on device and navigate to storypage
    -   Tablet and 2nd column views and clickthrough

-   Atlas

    -   <http://www.test.bbc.co.uk/ws/languages>

    -   Check all live sites are listed on this page and check a couple of click throughs to site homepage

-   Sitemaps

    -   <http://www.bbc.com/mundo/sitemap.xml>
    -   [http://www.bbc.com/arabic/sitemap.xml](http://www.bbc.com/mundo/sitemap.xml)
    -   [http://www.bbc.com/russian/sitemap.xml](http://www.bbc.com/mundo/sitemap.xml)
    -   Check these render ok and are not broken

-   Fonts

    -   Check fonts render on WS sites
    -   Load site on Chrome browser
    -   Inspect page
    -   On Application tab, go to Local Storage
    -   Click on <http://www.test.bbc.com/>
    -   Click on bbc.font Key Value and delete it
    -   Disable JS on browser and refresh page
    -   Enable JS on browser and refresh page
    -   Check font-family for bbc.font Key Value

        |Site     |Font           |
        | --------|:-------------------------:|
        | Arabic  | BBCNaseem				      |
        | Bengali | Shonar Bangla	             |
        | Burmese | Padauk                    |
        | Hindi   | mangal
        | Nepali  | mangal
        | Pashto  | BBCNaseem
        | Persian | BBCNaseem
        | Sinhala | Iskoola Pota BBC, SetDeco
        | Tamil   | Latha
        | Urdu    | BBCNaseem

-   CPS Preview

    -   Open CPS test
    -   Go to front page and click on a MAP page
    -   Click on Preview and the page should be rendered without any errors. (Clicking on Preview will open preview in CPS itself)
    -   There is also an option to Preview in Browser which will open preview in a browser, make sure that works too.

Release on Stage
----------------

#### General checks

-   Salvo :

    -   **ACTION** : Run then the [salvo-stage--runner](https://jenkins.news.tools.bbc.co.uk/view/Responsive%20News%20-%20Salvo%20Tests%20-%20STAGE/job/salvo-stage--runner/) job should be run, this job kicks off all of the salvo tests which run against the stage environment.
    -   **VERIFY** : That each of the salvo test jobs have run successfully. They can be seen here: [Salvo Workspace](https://jenkins.news.tools.bbc.co.uk/view/Responsive%20News%20-%20Salvo%20Tests%20-%20STAGE/)
    -   **COMMUNICATE** : Assuming all of the tests pass then a message should be posted on the #release channel on Slack to state that the salvo tests have passed.

-   Linkey :

    -   **ACTION** : The linkey tests should be run by clicking on 'Build Now' against the [Linkey stage job](https://jenkins.bbc.co.uk/job/linkey-stage/)
    -   **VERIFY** : That the job completes successfully
    -   **COMMUNICATE** : Assuming the tests pass then a message should be posted on the #release channel on Slack to state that the linkey tests have passed.

-   Wraith :

    -   **ACTION** : The following Wraith jobs should be started for [News](https://jenkins.news.tools.bbc.co.uk/job/wraith_news_stage/) and [World Service](https://jenkins.news.tools.bbc.co.uk/job/wraith_ws_stage/)
    -   **VERIFY** : Check the screenshots and investigate any differences highlighted

-   Automated Regression Tests :

    -   **ACTION** : The automated regression checks should be started here: [Regression Testing Browserstack](https://jenkins.news.tools.bbc.co.uk/job/regression-testing-browserstack/build?delay=0sec)
    -   **VERIFY** : View the results and ensure all of the test pass. A link to the results can be seen here: [Automated Regression Results](https://www.browserstack.com/automate/builds/b50af56704de855c096efffe4f72c95990622222)

#### Manual Checks

-   General Functionality

    -   Check that the site is rendered without any issues - <http://www.stage.bbc.co.uk/news>
    -   Check that there are no 500 errors.This can be done by opening firebug>console tab - <http://www.stage.bbc.co.uk/news>
    -   Check if there are any JS errors on the page - <http://www.stage.bbc.co.uk/news>
    -   Check adverts are only displayed on the international page - [http://www.stage.bbc.com/news](http://www.stage.bbc.co.uk/news)
    -   Check that weather works as expected - <http://www.stage.bbc.co.uk/news>
    -   Check local indexes look ok - <http://www.stage.bbc.co.uk/news/england/birmingham_and_black_country>
    -   Disable JS and check that the site is rendered without issues.
    -   Check share tools work as expected.

-   AV Page

    -   Check that the video plays properly - <http://www.stage.bbc.co.uk/news/world-europe-35881935>
    -   Check that [http://www.stage.bbc.co.uk/news/video_and_audio](http://m.stage.bbc.co.uk/news/video_and_audio) is not blank and no 500 errors displayed in the console.
    -   Check that the Related,Most Watched and Top Stories tabs are rendered with data and quick regression around the tabs.
    -   Check that stats are working.

-   Live event Component

    -   Check that the Live Event component is working as expected (Comments coming through and they are updated based on the latest time) - Live event  available on any index when the release is done[ ](http://www.stage.bbc.co.uk/news/live/world-europe-35869266)
    -   Check that the Live Event Component is not blank - <http://www.stage.bbc.co.uk/news/live/world-europe-35869266>
    -   <http://www.stage.bbc.com/urdu/world/2016/04/160404_panama_tax_leaks_rh>

-   RSS Feeds
    -   <http://feeds.stage.bbci.co.uk/persian/rss.xml>

-   Sanity Check Sites

    -   [http://www.stage.bbc.co.uk/news](http://www.stage.bbc.com/arabic)
    -   <http://www.stage.bbc.com/arabic>
    -   <http://www.stage.bbc.com/russian>
    -   <http://www.stage.bbc.com/mundo>
    -   Homepage
    -   Indexes and Assets
    -   Audio and Video Playback
    -   Forms

Release on Live
---------------

#### General checks

-   Linkey :

    -   **ACTION** : The linkey tests should be run by clicking on 'Build Now' against the [Linkey live job](https://jenkins.bbc.co.uk/job/linkey-live/)
    -   **VERIFY** : That the job completes successfully
    -   **COMMUNICATE** : Assuming the tests pass then a message should be posted on the #release channel on Slack to state that the linkey tests have passed.

-   Automated Regression Tests :

    -   **ACTION** : The automated regression checks should be started here: [Regression Testing Browserstack](https://jenkins.news.tools.bbc.co.uk/job/regression-testing-browserstack/build?delay=0sec)
    -   **VERIFY** : View the results and ensure all of the test pass. A link to the results can be seen here: [Automated Regression Results](https://www.browserstack.com/automate/builds/b50af56704de855c096efffe4f72c95990622222)

#### Manual Checks

-   Regression on LIVE just requires a quick sanity check across the news pages that are currently live to ensure that nothing has broken.

-   Run sanity checks on device and desktop browsers for playback on Video and Audio files

-   Sanity Check Sites

	- <http://www.bbc.co.uk/news>
   - <http://www.bbc.com/arabic>
   - <http://www.bbc.com/russian>
   - <http://www.bbc.com/mundo>
   -   Homepage
   -   Indexes and Assets
   -   Audio and Video Playback
   -   Forms

-   Check CPS preview for MAPs not retuning 404s

    -   Example urls - <https://preview.api.bbc.co.uk/previewPal/10462520>
    -   <https://preview.api.bbc.co.uk/previewPal/41011888>

-   CPS Preview
    -   Open CPS Live
    -   Go to front page and click on a MAP page
    -   Click on Preview and the page should be rendered without any errors.Clicking on Preview will open preview in CPS itself
    -   There is also an option to Preview in Browser which will open preview in a browser,make sure that works too.


