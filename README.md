# Weekly Reporting Flow 

- Technical Security Team - Weekley Report Creation and publication and notification bot

PowerAutomate flow for Team Weekly Report automation


### Process Setup

Trigger: The flow is scheduled to run every Monday at 9:00 AM GMT.

Calculate Dates:

It calculates the date for the next Friday.
It extracts the year, month, and day from that date to format it for the report name and folder structure.
Create Folder:

A new folder is created in SharePoint under a specified path for the weekly report, using the formatted year and month.
Get Template Content:

The flow retrieves a PowerPoint template from SharePoint that will be used for the report.
Create Report File:

A new PowerPoint file is created in the newly created folder, using the content from the template and naming it according to the calculated date and report name.
Create Sharing Link:

A sharing link for the newly created report file is generated, allowing others to access it.
Notify Team Members:

The flow prepares a list of team members' email addresses and generates mention tokens for each member.
It sends a message to a specified Teams channel, notifying the team about the published report and including the sharing link.
Reminders:

The flow sets up reminders for the team:
A reminder is sent on Wednesday about the upcoming report.
A final reminder is sent on Friday before the meeting, encouraging team members to update their sections of the report.
Termination:

The flow concludes successfully after sending the final reminder.


### Formulas



|__Name__|__Variable__|__Formula__|
|--------|------------|------------|
|Get the next Fridays date  | nextFriday |`@addDays(utcNow(),sub(5,dayOfWeek(utcNow())))`|
|Extract the year | YearOnly | `concat(formatDateTime(outputs('nextFriday'),'yyyy'))`|
|Month and Year (e.g. July 25, Feburary 2025) |monthAndYear | `concat(formatDateTime(outputs('getFridayDate'), 'MMM yyyy'))`|
|abbreviation month and Year (e.g. Jul 2025, Feb 2025) | shortMonthAndYear | `@concat(formatDateTime(outputs('getFridayDate'), 'MMM yyyy`|  
|Day Month and Year (e.g. 07-02-2025 | dayMonthYear | `concat(formatDateTime(outputs('fridayInWeek'),'dd-MM-yyyy'))`|
|Report Name - Part of name | reportName |`string('Technical Security Team - Weekly Report')`|
|Add timestamp to protect overwrite (now time) | reportName |`@formatDateTime(utcNow(),'HH:MM')`|
|Now date | fomattedNowdate  |`formatDateTime(utcNow(), 'dd-MM-yyyy')`|



|__Name__|__Variable__|__Formula__|
|--------|------------|------------|
|Create sharepoint file or folder | createFolder | - |
|Site Address*| SharePoint site address |https://easyjet.sharepoint.com/sites/SecurityOperations|
|Folder path*| Path  |/SecOps Team Reporting/2. Weekly/1. Technical Security Weekly Report/{outputs('YearOnly')}/{outputs('shortMonthAndYear')}/|
|Get Template Content*|  Site Address* |https://easyjet.sharepoint.com/sites/SecurityOperations|
|File Identifier*|  Template location |/Shared Documents/SecOps Team Reporting/1. Report Templates/1. Technical Security Team/2. Weekly Technical Security Team Report/TEMPLATE.pptx|
|Wait Until | Random delay after start time|```{
  "type": "Recurrence",
  "recurrence": {
    "interval": 1,
    "frequency": "Minute",
    "timeZone": "GMT Standard Time",
    "startTime": "2025-02-11T22:15:00Z"
  }
}``` |














| First Header  | Second Header |
| ------------- | ------------- |
| Content Cell  | Content Cell  |
| Content Cell  | Content Cell  |



