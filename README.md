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
|Get the next Fridays date  | fridayInWeek |`@addDays(utcNow(),sub(5,dayOfWeek(utcNow())))`|
|Extract the year | YearOnly | `concat(formatDateTime(outputs('fridayInWeek'),'yyyy'))`|


| First Header  | Second Header |
| ------------- | ------------- |
| Content Cell  | Content Cell  |
| Content Cell  | Content Cell  |



