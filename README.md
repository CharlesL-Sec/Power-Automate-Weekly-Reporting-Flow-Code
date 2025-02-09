# Weekly Reporting Flow 

- Technical Security Team - Weekley Report Creation and publication and notification bot

PowerAutomate flow for Team Weekly Report automation


### Process Setup

The PowerAutoMate script will: 
- Make a copy of the working template in the 1. Technical Security Weekly Report { YYYY} {MMM YY}/ directory.
- Create this copy using the serial date of the next Friday e.g. 20250132 – Technical Security Team Weekly.
-Create a sharelink for the new weekly report copy.
- Post a message to the reporting Teams channel containing the new sharelink


This process  requires the following setup
-	PowerPoint Weekly Reporting Template
-	Once the required PowerPoint template has been created, the file should be stored in the following SharePoint folder -  https://easyjet.sharepoint.com/:p:/r/sites/SecurityOperations/Shared%20Documents/SecOps%20Team%20Reporting/1.%20Report%20Templates/1.%20Technical%20Security%20Team/2.%20Weekly%20Technical%20Security%20Team%20Report/ 

This boilerplate should be stored with a logically serialised and versioned filename.
A working copy should be made named TEMPLATE.pptx 
___This will reduce the risk that the script can wipe out the original template due to an error__

### PowerAutoMate Flow Process.
The PowerAutoMate script will: 
- Make a copy of the working template in the 1. Technical Security Weekly Report { YYYY} {MMM YY}/ directory.
- Create this copy using the serial date of the following Friday, e.g. 20250132 – Technical Security Team Weekly.
-Create a sharelink for the new weekly report copy.
- Post a message to the reporting Teams channel containing the new sharelink
	



### Formulas



|__Name__|__Variable__|__Formula__|
|--------|------------|------------|
|Get the next Fridays date  | nextFriday |`@addDays(utcNow(),sub(5,dayOfWeek(utcNow())))`|
|Extract the year | YearOnly | `concat(formatDateTime(outputs('nextFriday'),'yyyy'))`|
|Month and Year (e.g. July 25, Feburary 2025) |monthAndYear | `concat(formatDateTime(outputs('nextFriday'),'Y'))`|
|Abreviation month and Year (e.g. Jul 2025, Feb 2025) | shortMonthAndYear | `concat(formatDateTime(outputs('nextFriday'),'Y'))`|  
|Day Month and Year (e.g. 07-02-2025 | dayMonthYear | `concat(formatDateTime(outputs('fridayInWeek'),'dd-MM-yyyy'))`|
|Report Name - Part of name | reportName |`st0ring('Technical Security Team - Weekly Report')`|
|Add timestamp to protect overwrite (now time | reportName |`formatDateTime(utcNow(), 'HH:mm')`|



|__Name__|__Variable__|__Formula__|
|--------|------------|------------|
|Create sharepoint file or folder | createFolder | - |
|Site Address*| SharePoint site address |https://easyjet.sharepoint.com/sites/SecurityOperations|
|Folder path*| Path  |/SecOps Team Reporting/2. Weekly/1. Technical Security Weekly Report/{outputs('YearOnly')}/{outputs('shortMonthAndYear')}/|
|Get Template Content*|  Site Address* |https://easyjet.sharepoint.com/sites/SecurityOperations|
|File Identifier*|  Template location |/Shared Documents/SecOps Team Reporting/1. Report Templates/1. Technical Security Team/2. Weekly Technical Security Team Report/TEMPLATE.pptx|















| First Header  | Second Header |
| ------------- | ------------- |
| Content Cell  | Content Cell  |
| Content Cell  | Content Cell  |



