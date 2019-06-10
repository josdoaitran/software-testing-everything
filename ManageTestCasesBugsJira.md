# MANAGE TEST CASES AND BUGS USING JIRA

## Modification in JIRA

Modifications are required to use existing flow of JIRA as a Test Case  management with the help of a JIRA administrator. Below are the steps to modify the existing JIRA workflow:

+ Create/Add new Issue type
+ Create/Add new Status
+ JIRA default workflow
+ Test case work flow after modification
+ Status in Test case workflow

Here are additional detail explaining each of the steps below:

### 1. How to create issue type?

Add a new issue type in existing flow and name it “Test case.” This should be a top-level (standard) task (for this go to Administration > Issues > Issues Types and use  Add Issue Type option).

### 2. How to create status?

Add new status (for this go to Administration > Status > Status Types and use Add Status Type option)

### 3. JIRA default workflow

JIRA workflow is the set of status and transitions through which an issue goes during its lifecycle

![alt text](https://www.3pillarglobal.com/wp-content/uploads/2014/11/xJIRA-KP-1.jpg.pagespeed.ic.lJ8-hVD-h2.webp)

### 4. Test case work flow after modification

After modification with the help of JIRA administrator below is the Test case workflow with different status:

_Test case work flow_

![alt text](https://www.3pillarglobal.com/wp-content/uploads/2014/11/xJIRA-KP-2.jpg.pagespeed.ic.dyufgJHFp8.webp)

_Status in Test case workflow:_

TC awaiting review: Default status when a Test Case is created and awaiting for Review from the QA lead.

TC Template: An approved TC that has not yet been scheduled yet.

TC-Ready to Run: TC that has been scheduled.

In Progress: TC that has been in-progress state

TC-Failed: After execution when TC fail status update to TC-Failed

TC-Passed: After execution when TC Pass status update to TC-Passed

TC-Invalid: A test that has become obsolete or cannot be run

Closed: This is the final status of the TC

### 5. About JIRA CLI

One of the major challenge was how to import the TCs in JIRA because designing test cases one by one in JIRA was time consuming. A tool was needed by which I can upload the TC in JIRA from file (.csv, Excel, etc.). Finally, I found Add-on JIRA CLI (free tool ~Till version 2.6.0) to import the Test case’s from .csv

### 6.How to import Test case using JIRA CLI?

- Download jira-cli (Lasted version) from [this link](https://marketplace.atlassian.com/apps/6398/jira-command-line-interface-cli/version-history)
- Save the Test cases file with name import.xls and convert into .csv format then copy import.Csv file under downloaded folder (jira-cli-2.6.0) .csv format given below

![](https://www.3pillarglobal.com/wp-content/uploads/2014/11/xJIRA-21.jpg.pagespeed.ic.efbEKthSZr.webp)

~In above import.csv file Description column consist  merge data of (Prerequisites, Steps, and Expected Results)

- Under downloaded folder (jira-cli-2.6.0) there is a file with name import.properties

- Map column name for which we want to import the data in the properties file

field.Type = Type

field.Component = Components

field.Project = Project

field.Objective = Summary

field.Description = Description

File (~import.properties file format as seen above)

- Run the following single line command in command prompt
```
c://Jira-cli-3.8.0>jira.bat –server <URL of JIRA> -user kailash.pathak – password “xxxxxxx” –action runFromCsv –file import.csv –propertyFile import. Properties –common “–project SSPQA”               — continue
```

(~Here “SSPQA” Is Project Key)

-Test case data is imported in JIRA against the particular components successfully
