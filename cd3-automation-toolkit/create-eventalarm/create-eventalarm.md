# Create OCI Event Rule, Alarm and Notifications

## Introduction

Oracle Cloud Infrastructure services emit Events, which are structured messages that indicate changes in resources. 

The Notifications service lets you know when something happens with your resources in Oracle Cloud Infrastructure. 

Using Alarms and Event Rules, you can get human-readable messages through email and text messages (SMS).

Some examples of how you might use Events and Notifications: 

- Send a Notification to a DevOps team when a database backup completes.
- Convert files of one format to another when files are uploaded to an Object Storage bucket.

Estimated Time: 10 minutes

### Objectives

The objectives of this lab are:

- Add OCI Event Rule, Alarm and Notifications details in Excel spreadsheet.
- Execute the setUpOCI.py script to generate Terraform files.
- Execute Terraform commands from the respective service folder.

### Prerequisites
Please follow the previous lab till the last step. Once you are able to provision OCI service, you are all set to continue with this lab.

## Task 1: Add OCI Event Rule, Alarm and Notifications in Excel Spreadsheet

1. Copy *CD3-CIS-ManagementServices-template.xlsx* from below path to locally on your system.

    ```
    /cd3user/oci_tools/cd3_automation_toolkit/example
    ```

2. Open *CD3-CIS-ManagementServices-template.xlsx* and update *Events, Alarms, Notifications* tabs based on your requirements and save it. You could use CIS standard pre-filled data in spreadsheet.

    _e.g._ ![Event Rule](images/event_rule.jpg)

    ![Notifications](images/notifications.jpg)

    ![Alarms](images/alarms.jpg)

## Task 2: Deploy OCI Event Rule, Alarm and Notifications

1. Place *CD3-CIS-ManagementServices-template.xlsx* Excel sheet at any location inside your container. 

2. Open ```<prefix>_setUpOCI.properties``` under below path:

    ```/cd3user/tenancies/<prefix>/<prefix>_setUpOCI.properties```

3. Under ```cd3file``` parameter, add the path of the input Excel sheet.

    ```
    e.g. cd3file=/cd3user/tenancies/usr1_livelab/CD3-CIS-ManagementServices-template.xlsx
    ```

    In the same file, make sure ```workflow_type``` parameter is set to ```create_resources```.

2. *Execute* the setUpOCI Script from below path:

    ```
    cd /cd3user/oci_tools/cd3_automation_toolkit/
    python setUpOCI.py /cd3user/tenancies/<prefix>/<prefix>_setUpOCI.properties
    ```

3. Select *option 11* for ```Management services``` from Menu and *options 1,2,3* from submenu for *Notifications, Events and Alarms*.

4. Once the execution is *successful*, ```<prefix>_events.auto.tfvars``` file will be generated under below folder in the region selected.

    ```
    /cd3user/tenancies/<prefix>/terraform_files/<region_dir>/<managementservices>
    ```

5. Navigate to the above path and *execute* the terraform commands:

    ```
    terraform init
    terraform plan
    ```

Wait for a bit until the plan succeeds and plan logs are available under _Logs_. Take a look to familiarize yourself with the log format. Scroll down until you see the line `Plan: X to add, 0 to change, 0 to destroy`.

6. Once satisfied by the plan logs, put it to action by starting the *Apply* process.

    ```
    terraform apply
    ```

## Task 3: Inspect Created Objects

After apply is successful, Go to *OCI console* under compartment which was selected for deployment and review the resources created. 

Ask yourself how these resources will make your environment more healthy.

You may now __proceed to the next lab__.

## Acknowledgements

- __Author__ - Dipesh Rathod
- __Contributors__ - Murali N V, Suruchi Singla, Lasya Vadavalli
- __Last Updated By/Date__ - Dipesh Rathod, May 2023
