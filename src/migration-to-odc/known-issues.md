---
summary: Current technical issues and recommendations in the migration of the OutSystems O11 apps to ODC, with recommendations how to address the issues where possible. 
locale: en-us
guid: 84c331ff-513c-4e1f-ae7c-df9dfaac44f1
app_type: traditional web apps, mobile apps, reactive web apps
platform-version: o11
figma:
---

# Known issues

This page outlines the current technical limitations related to the migration on the OutSystems 11 apps to ODC. OutSystems development teams are actively working on addressing the issues.

## Data is truncated for attributes larger than 100 MB

A validation process checks the size of each binary data attribute in the database. If an attribute exceeds the maximum allowed size of 100 MB, the data is truncated in the migration process. This mechanism is in place to unblock the migration process, but it requires careful data preparation before migration to a production environment.

### Impact

The truncation of attributes leads to data loss.

### How to fix

When **migrating to a production environment**, ensure that the attributes in your OutSystems 11 apps are smaller than 100 MB.

## Forbidden access to LifeTime

This error shows in logs and means the service account cannot reach LifeTime to fetch data. You define this service account in the ODC Portal, during the setup of the Migration Assessment Tool.

### Impact

You can't initiate the migration because ODC cannot connect to O11 LifeTime.

### How to fix

Reset the service account for the Assessment Tool.

1. Go to LifeTime Access and access the page `https://<LifeTime_server>/lifetime/troubleshoot.aspx`. 
1. In the **Effective Permission Status** section, find the **AssessmentTool**(`service_account_name`).
1. Select the button **Clean up** in the same line.