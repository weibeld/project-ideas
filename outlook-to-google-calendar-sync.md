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
  - From ChatGPT:
    > Yes, it is possible to automate the export of an Outlook calendar as a .ics file without using a third-party tool, by creating a Windows Task Scheduler task. Here are the steps:
    >
    > 1. Open Outlook and select the calendar you want to export.
    > 1. Click on the "File" tab in the top left corner.
    > 1. Click on "Open & Export" and select "Import/Export".
    > 1. In the Import and Export Wizard, select "Export to a file" and click "Next".
    > 1. Select "iCalendar (.ics)" as the file type and click "Next".
    > 1. Choose the calendar you want to export and select the location where you want to save the .ics file.
    > 1. Enter a name for the exported file and click "Finish".
    > 1. Open the Windows Task Scheduler by searching for "Task Scheduler" in the Start menu.
    > 1. Click on "Create Task" in the right-hand pane.
    > 1. Give the task a name and description, and select the frequency and time of day you want the task to run.
    > 1. In the "Actions" tab, click on "New" and select "Start a program".
    > 1. Browse to the location of the Outlook executable file (Outlook.exe) and enter the following command line arguments: /select outlook:calendar /c ipm.appointment /c ipm.task /c ipm.stickynote /c ipm.contact /recycle /q
    > 1. In the "Conditions" and "Settings" tabs, configure the task to run according to your preferences.
    > 1. Click "OK" to save the task.
    > 
    > The Windows Task Scheduler will now automatically export the selected calendar as a .ics file at the specified interval. Note that this method requires some technical knowledge and may require some setup time.
  - ChatGPT about the Windows Task Scheduler syntax:
    > The command line arguments "/select outlook:calendar /c ipm.appointment /c ipm.task /c ipm.stickynote /c ipm.contact /recycle /q" are used to start Outlook and select the specified folder or item types. Here is a brief explanation of each argument:
    > 
    > - "/select outlook:calendar" - This argument selects the Calendar folder in Outlook.
    > - "/c ipm.appointment" - This argument selects the Appointments item type in the selected folder.
    > - "/c ipm.task" - This argument selects the Tasks item type in the selected folder.
    > - "/c ipm.stickynote" - This argument selects the Notes item type in the selected folder.
    > - "/c ipm.contact" - This argument selects the Contacts item type in the selected folder.
    > - "/recycle" - This argument instructs Outlook to start a new instance if there is already an instance running.
    > - "/q" - This argument starts Outlook in "quiet" mode, which means that no splash screen or error messages are displayed.
    > 
    > The command line arguments are used in conjunction with the Windows Task Scheduler to automate the export of an Outlook calendar as a .ics file. While there is no official Microsoft documentation for these arguments, they are widely used by developers and IT professionals for automating Outlook tasks.
  - Resources (also partly from ChatGPT):
    - https://support.microsoft.com/en-us/office/command-line-switches-for-microsoft-office-products-079164cd-4ef5-4178-b235-441737deb3a6
    - https://www.lifewire.com/back-up-copy-auto-complete-list-outlook-1173775
    - https://www.howto-outlook.com/howto/commandlineswitches.htm


- How to import a calendar to Google Calendar in an automated way?
  - From ChatGPT:
      > Unfortunately, there is no built-in feature in Google Calendar to automate the process of importing a .ics file. However, there are some workarounds that you can use to achieve a similar result:
      > 1. Use a script: You can create a script using Google Apps Script that automatically imports a .ics file from a specific location at regular intervals. To do this, you would need to have some coding knowledge and follow the instructions available in the Google Apps Script documentation.
      > 2. Use a third-party integration platform: There are some integration platforms such as Zapier and Integromat that allow you to automate the process of importing a .ics file to Google Calendar. These platforms offer pre-built integrations that you can use to set up an automated workflow. For example, you can set up a workflow that triggers when a new .ics file is added to a specific folder in Google Drive, and automatically imports the events to your Google Calendar.
      > 3. Use a custom program: You can develop a custom program or application that automates the process of importing a .ics file to Google Calendar. However, this would require programming skills and access to the Google Calendar API.
      > While these options require more technical knowledge and may require some setup time, they offer a more automated solution for importing .ics files to Google Calendar.
  - Resources:
    - https://www.google.com/script/start/
