🏡 Real Estate CRM Automation – Salesforce


📌 Overview

A custom-built Salesforce CRM solution for managing real estate sales lifecycle with automated business logic using Apex triggers and validation rules.



📸 System Screenshots

Opportunity Closed Won
Property Auto Updated
Commission Created
Validation Rule
Site Visit Task Automation


🔹 Objects Used

Custom Objects
Property__c
Commission__c
Site_Visit__c
Standard Objects
Opportunity
Task


🔹 Key Automations Implemented

1️⃣ Opportunity → Closed Won Automation


When Opportunity stage changes to Closed Won:
Property status automatically updates to Sold
2% commission record is auto-generated
Ensures no duplicate commission creation


2️⃣ Site Visit Automation

When a Site Visit is created:
Automatically creates follow-up Task
Updates Opportunity stage to Negotiation/Review
Prevents visit scheduling if property is already sold


3️⃣ Validation Rule

Blocks site visit creation if Property Status = Sold
Maintains business data integrity


🔹 Technologies Used

Apex Triggers
SOQL
DML Operations
Validation Rules
Lightning Record Pages
Custom Object Relationships


🔹 Business Impact

Eliminates manual status updates
Automates commission calculations
Prevents invalid sales operations
Streamlines real estate deal lifecycle