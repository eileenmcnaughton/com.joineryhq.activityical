# CiviCRM Activity iCalendar Feed

## Overview

Several people have expressed interest in getting their CiviCRM assigned activities into their Google Calendar or similar calendaring applications. This extension fills that purpose by providing a feed of each user's assigned activities in iCalendar format, ready to be subscribed to with Google Calendar and/or Outlook.


## Key Features

* General description: This module provides an iCalendar feed for each CiviCRM contact containing the contact's upcoming (future) assigned activities, suitable for subscription via Google Calendar, Microsoft Outlook, and/or similar software.
* Activities are represented as VEVENT objects, matching applicable properties (DTSTART, DTEND based on duration, etc.) where possible and appending names of any other assignees to the DESCRIPTION property.
* Feed can include activities of any type, including client-defined activity types.
* Feed includes activities with a status of "Scheduled" or any client-defined activity status.
* To conserve server resources, feeds are cached at a site-wide configurable interval.
* A contact's feed shows all activities having that contact assigned, even if other contacts are also assigned.
* Users with sufficient permissions can easily determine the correct URL for their contact's activities feed by viewing the URL in CiviCRM. Administrative users can easily retrieve the feed URL for any contact.
* URL includes a persistent random hash to limit other parties' attempts at guessing the URL and viewing the contact's feed; this hash can be re-generated by the user (if sufficiently permissioned) or by an administrator in case, for example, the URL becomes known to the wrong people.

## Installation and Configuration

Follow the standard CiviCRM extension installation procedure.

Once installed, the configuration page is available by navigating to Administer -> System Settings -> Activity iCalendar Feed.

Notable configuration options include these:

* __Activity iCalendar Feed Group:__ Not all contacts will have a feed. Taking a conservative approach, this extension provides feeds only for contacts who are current members of the CiviCRM group selected in this configuration option. You may wish to create a dedicated group named "Activity iCal Feed" for this purpose.


## Feed URL for Each Contact

Note: Not all contacts will have a feed. See _Installation and Configuration: Activity iCalendar Feed Group_, above.

For each contact having a feed, a unique URL is defined to access their feed. This URL includes a random hash as a barrier against unauthorized persons guessing the URL and accessing the user's feed.

Other than validating the random hash, the URL makes no checks for authentication before presenting the activity feed for the requested user. A user may regenerate a new URL with a new random hash if she feels her feed URL has become known by people who should not have it.

### Feed Details page
For each contact, a summary of feed information is displayed on the contact's Feed Details page. This page includes the feed URL, some explanatory help text, and a button to regenerate the feed URL with a new random hash.

The Feed Details page is accessible as follows:

#### For the current user's contact:
With the right configuration, a link to information about the current user's feed is displayed at the top of the CiviCRM Contact Dashboard. To enable this display, navigate to Administer > Customize Data and Screens > Display Preferences, find the section labeled "Contact Dashboard", and ensure that the option "Assigned Activities" is enabled.

With this done, a user who clicks on "My Contact Dashboard" when logged into CiviCRM will see, at the top of the Contact Dashboard, a message stating, "Assigned activities are accessible as an iCalendar feed," and a link labeled "Feed details..." pointing to the contact's Feed Details page -- assuming the contact has a feed.

#### For any other contact:
Users with the "administer CiviCRM" permission can access the Feed Details page for any contact having a feed. This is most easily accessed under the "Activities" tab of the contact record. At the top of this page is a label, "iCalendar", followed by two links: "Feed", which is a direct link to the feed URL; and "Details", which is a link to the Feed Details page for this contact.

## FAQs
1. __Why am I getting the error, "The given contact does not have an activities iCalendar feed." for some contacts?__
Not all contacts will have a feed. See _Installation and Configuration: Activity iCalendar Feed Group_, above.
2. __Why isn't my feed updating in Google Calendar?__
In Google Calendar, the expected behavior is that linked iCalendar feeds may not not refreshed for several hours. The Google Calendar documentation at https://support.google.com/calendar/answer/37100?hl=en&ref_topic=1672445 says, "It might take up to 12 hours for changes to show in your Google Calendar." Unfortunately, even though the extension is doing its job and always providing a feed with the latest information, it's up to the feed consumer (in this case, Google Calendar) to decide what they want to do with that information and how often they want to refresh it. You can verify that the feed is working properly by acccessing the feed URL directly in your browser.


## Help and Improvements

Please help me improve this extension by using the extension issue queue to report any troubles and to make requests for feature improvements. The issue queue is here: https://github.com/twomice/com.joineryhq.activityical/issues

Issues submitted to the issue queue will be addressed as I have time and interest. Please contact me at allen@joineryhq.com to request paid support.
