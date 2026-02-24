🏗 System Architecture – Real Estate CRM Automation
1️⃣ Overview

This project implements a real estate sales lifecycle automation system in Salesforce using Apex triggers, custom objects, and validation rules.

The architecture follows:

Event-driven automation (Apex triggers)

Relational data modeling (Lookup relationships)

Business rule enforcement (Validation Rules)

Bulk-safe design pattern

2️⃣ Data Model
Standard Objects

Opportunity

Task

Custom Objects

Property__c

Commission__c

Site_Visit__c

3️⃣ Object Relationships

Opportunity → Lookup → Property

Commission → Lookup → Opportunity

Site Visit → Lookup → Opportunity

Site Visit → Lookup → Property

Task → Related To → Opportunity

This relational model ensures data consistency and supports automation across objects.

4️⃣ Automation Layer
A. Opportunity Trigger (After Update)

Triggered when Opportunity Stage changes to Closed Won.

Actions:

Updates related Property Status to Sold

Calculates Commission (2% of Property Price)

Creates Commission record

Design Notes:

Uses Trigger.oldMap to detect stage change

Uses bulk-safe collections (Set, Map, List)

Avoids SOQL inside loops

B. Site Visit Trigger (On Insert)

Triggered when a new Site Visit record is created.

Actions:

Creates follow-up Task

Updates Opportunity stage to “Negotiation/Review”

Enforces validation (property cannot be sold)

5️⃣ Validation Layer

Validation Rule prevents scheduling a Site Visit for properties where:

Property Status = Sold

This ensures business data integrity and prevents invalid operations.

6️⃣ Design Principles Used

Bulk-safe Apex design

Separation of concerns

Cross-object automation

Defensive programming

Governor limit awareness

7️⃣ Automation Flow Summary
Opportunity Closed Won Flow

Stage changes to Closed Won

Property fetched via lookup

Property status updated to Sold

Commission calculated (Price × 2%)

Commission record inserted

Site Visit Flow

Site Visit created

Check Property status

If Sold → Block

If Available → Create Task

Update Opportunity Stage