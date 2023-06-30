---
created: 2023-06-30T14:19:05+02:00
edited: 2023-06-30T14:19:05+02:00
title: Outlook to Google Calendar Sync
---

A scheduled process that exports the calendar from Outlook and imports it into Google Calendar.

## Background

Outlook allows adding a Google account so that a Google calendar can be displayed in the Outlook calendar. However, the inverse does not seem to be possible, i.e. Google calendar does not allow adding a Microsoft account for adding an Outlook calendar.

There exist third-party services such as [SyncGene](https://www.syncgene.com/) that make this possible. However, access of such services to Outlook or Google Calendar may be blocked by company policies if work accounts are used (as is the case with Post which blocks access to Outlook by third-party apps like SyncGene).

The only workaround to have Outlook calendars in Google Calendar thus seems to be to export the current calendar snapshot from Outlook (which should be possible as an `.ics` file) and import it into Google Calendar. This action could be performed at a scheduled intervall, e.g. every day.

## Open questions

- How to export the calendar from Outlook without accessing some form of Outlook API itself (which may be blocked by company policies)?
- How to import a calendar to Google Calendar in an automated way?
