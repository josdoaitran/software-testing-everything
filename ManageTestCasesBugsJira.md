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

### 7. Process for Test case creation and allocation in JIRA

Below are the steps for test case creation and allocation in JIRA:

Test Case creation steps:

- Create a new project with the help of JIRA administrator.
- Create sprint Task, sub task for QA e.g. Design Test case and Execute Test case of particular module 
- Create Components against the Project with the help of JIRA administrator
- Create Test Case In Excel
- Convert TC in .csv file with giving name as import.csv (its mandatory csv with this  name) for to import in JIRA. csv file format attached above
- Upload .csv into JIRA using JIRA CLI using the (above mentioned steps)

Create Test Case in excel sheet in the format which is acceptable by JIRA CLI (see below for example)
![](https://www.3pillarglobal.com/wp-content/uploads/2014/11/xJIRA-211.jpg.pagespeed.ic.iXpu-z0K8u.webp)

Test Case Allocation steps :

We can allocate Test Cases for execution using bulk change functionality. During the bulk change we can assign the user name to the Test Cases.

First search the TCs then assign user name in bulk by clicking on Assign to me link see below screen shot for more detail
![](https://www.3pillarglobal.com/wp-content/uploads/2014/11/xJIRA-KP-3.jpg.pagespeed.ic.lzOAfML8tf.webp)
![](https://www.3pillarglobal.com/wp-content/uploads/2014/11/xJIRA-KP-4.jpg.pagespeed.ic.Aa2q3SseZQ.webp)

### Test Case Execution

Once the TCs are allocated next step is to execute the Test Cases in JIRA with updating their status with Pass, Fail etc.

### Prerequisites:

- We are executing TC in three browsers (Chrome, IE, and FireFox)
- We are executing each of TC in two cycles (Cycle 1, Cycle 2)

After uploading and allocating the test cases next step is to execute the test cases. Follow these steps to execute it:

- Bring all Test cases we want to execute in “IN PROGRESS” state using Bulk change functionality
- Execute TCs one by one

### In case of Test case FAIL

- In case of a FAIL a New Transition comments screen (See screen shot below) open
- Enter actual result.
- Enter Sprint<Sprint Number>-Cycle< Test Cycle No. >-<Browser Name> <Fail>

E.g. Sprint26-Cycle1-IE-Fail as Comment

- Click on the Fail button
- Particular test case is Fail
- Report bug for Fail Test Case
Link Fail Test Case with Bug Number (*Explain in next point*)

### Linking of Fail Test case with Bug ID

To link the test case with Bug ID Open Particular Failed TC and Click on “Link” from menu following screen open to link the Test Case with Bug ID after clicking on link button Fail TC link with the Bug ID

![](https://www.3pillarglobal.com/wp-content/uploads/2014/11/xJIRA-KP-5.jpg.pagespeed.ic.U1IfQhp0ir.webp)

![](https://www.3pillarglobal.com/wp-content/uploads/2014/11/xJIRA-KP-6.jpg.pagespeed.ic.U_vqSw_03v.webp)
### In case of Test case PASS

If Test Case Pass in first time or in second cycle in that case update the comments with Pass status and with respective Cycle Below the screenshot when TC pass in second cycle

![](https://www.3pillarglobal.com/wp-content/uploads/2014/11/xJIRA-KP-7.jpg.pagespeed.ic.A81KRYpTsh.webp)

*Note:*

Entered above comments help us to pull out the report.
![](https://www.3pillarglobal.com/wp-content/uploads/2014/11/xJIRA-KP-8.jpg.pagespeed.ic.hKfxFOR_Dg.webp)

### In case of Test case INVALID

In case of invalid test case that has become obsolete or cannot be run. We will update the status as shown below:
![](https://www.3pillarglobal.com/wp-content/uploads/2014/11/xJIRA-KP-9.jpg.pagespeed.ic.hKfxFOR_Dg.webp)

*Note:*

Same transition screen open to enter comments in case of other status (Closed, TC-Template, TC-Ready to Run etc.)

## Report in JIRA of Test Cases

We can generate execution report using different criteria (We can use the entered comments during execution of TC as search criteria).

### Search Criteria:

### Sprint Wise Report
