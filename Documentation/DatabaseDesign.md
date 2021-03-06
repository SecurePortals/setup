## Database Design

> So far, this is what our database design looks like:

![Image](https://github.com/SecurePortals/SecPort-Setup/blob/master/Documentation/PNG/ERD5.2.png)

> So let's break down each of these tables and what kind of data will be in each of them. 

### LOGGING

> The LOGGING table will hold the log results of all of our back-end Scripts and Web Services. Everytime a Script (ex: The database Integrity Checks) or a Web Service (ex: Veryfying usernames/passwords), there is a log output that is produced to help us keep track on how the run went. Hopefully, everytime one of these processes is run, it's all green lights and everything runs the way it's supposed to. If this is the case, then we would INSERT one row into the LOGGING table which would have a 'T' value for LOGGING.SUCCESS (T is for True), a value like "Run Successful" for LOGGING.MESSAGE, and then maybe the name of the script/web service for LOGGING.SCRIPT_NAME. But if one of our processes were to fail, then we would see an 'F'for LOGGING.SUCCESS, and a more descriptive message like, "Duplicate in the PROPERTY for PROPERTY_ID = 101" for LOGGING.MESSAGE, and so on. 

### DATA_INTG_RSLTS

> The DATA_INTG_RSLTS table is similar to the LOGGING table, except it is only updated when one of our Database Integrity Check Scripts fails. If one of our DB Integrity Check scripts fail, a message is written to LOGGING as well as DATA_INTG_RSLTS, and we'll include a reference to LOGGING from DATA_INTG_RSLTS so we can follow the message. 

### OWNER, MANAGER, TENTANT

> These three 'user' tables are going to have the data that our users will provide to us. 

### MESSAGES (MAY BE REPLACED BY NOTES)

> The MESSAGES table will hold messages that OWNERs or MANAGERs can send to their TENTANTs. If an owner creates a message, it will go to all their PROPERTY they own; if a MANAGER creates a message, it will go to all their PROPERTY they manage.

### PROPERTY

> The PROPERTY table holds all the data for each of the properties that belong to our OWNERs. BUSINESS RULES: When an OWNER's contract has ended, all properties should be deleted. 

### DOCUMENT

> The DOCUMENT table holds links to all legal documentation, like Lease Agreements. 

### LOGIN

> The LOGIN table holds username/password data and the last time the password was updated. BUSINESS RULES: Password should be updated every six months. Emaail reminders should be sent out reminding users to change their passwords.

### PAYMENTS (TO BE REPLACED BY CREDITS TABLE)

> The PAYMENTS table holds records of all the payments made to SecurePortals. BUSINESS RULES: When payment is made, the associated charge should be dismissed.

### CHARGES

> The CHARGES table holds records of all open charges to tentants. BUSINESS RULES: Closed charges should be deleted.

### TRNS_HIST (TO BE REPLACED BY TRANSACTIONS)

> To Remain Empty.

### SESSION

> The SESSION table will be used to keep track of user's and their login sessions when using our web app. 

### UNIT

> The UNIT table holds the apartment number, or unit number that a LEASE belongs to. MANY-TO-ONE relationshpi with PROPERTY.

### REQUESTS

> The REQUESTS table holds all the maintenance requests that have been created by TENTANTs. BUSINESS RULES: Remind Manager (or Owner if no Manager) every week from the time a Maintenance Request has been made until the Manager (or Owner) has marked the request as complete

### NOTES

> The NOTES table may replace the MESSAGES table, because of overlapping scope. NOTES will allow Tenants to share comments/notes with other tenants that share the same lease, Managers with other managers of the same property/owner/all tenants of their property, and Owners with everyone.

### LEASE

> The LEASE table will hold all the data that keeps track of what the monthly payments are, parking costs, misc costs (like if utilities, electricity are included), and start/end of each lease. 

### EMPLOYEE

> The EMPLOYEE table will house the information for each of the EMPLOYEES in that work for SecurePortals. 

### ADMIN

> The ADMIN table will allow the creation of administrator priviledged users to see and access the DB from the web application. 
