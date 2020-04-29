## Sales Rep Story at BigCo, Inc.

### Purpose
We track Sales Rep information at BigCo, Inc.


### Data
Data tracked for SalesReps includes name (first, middle, last), unique salesrep id, commission percentage, email (work, alternate), phonenumber (work, mobile), smsNumber. We also track the date/time the record was created and each date/time it is modified.

### Actions
Typical actions are creating, updating, and deleting (when a SalesRep is deleted, all data must be retained for reporting purposes). SalesReps can edit their name and contact info only. The Sales Supervisor can edit all fields except salesrep id and the tracking dates. List filters include name, email, and commission percentage.

### Rules
Sales Reps are assigned one or more accounts to manage. Reps make regular contact with accounts (via email, phone, in-person visits). They can set account spending limits and discount rates. Each time a SalesRep makes an account contact, that must be added to the system.  Sales Reps get a percentage of all purchases made by their accounts. The percentage they get varies and is set by the sales supervisor.

### Processes
The following special lists/reports that run on demand are:
 * Commission Report (rep name, id, percentage, and computed commision for the month)
 * Account Report (rep name, id, associated accounts)
 * Customer Report (rep name, id, associated customers and accounts).
   
