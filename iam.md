# AWS Organization

* Manage multiple AWS accounts easily  
* Consolidate billing and manage resources across different accounts, using just a single payment method
* Pricing benefits due to aggrevated usage as it combines all accounts
* Can share reserved instances and savings plan discounts across accounts
* IAM Center can be integrated into the corporate directory for centralized authentication
* Main Account is the management/primary one, and others are named member accounts

### Structure

Root Organisation Unit is the main account, within this you can have additional OU's for Developmet, Production, HR etc. 
These can be nested 

### Advantages

1) Tagging standards for billing purposes
2) Enable CloudTrail for all accounts but combine into a single S3
3) Establish cross account roles for administration purposes
4) Can define Service Control Policies (SCP) - see below

# Service Control Policy (SCP)

* IAM Policy
* Apply to specific accounts or OU's
* Help to enforce policies across the organization and control features accessible to other accounts
* Can ensure the resources are accessible and used appropriately
* They apply to all member accounts but not the management account 
