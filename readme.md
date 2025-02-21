![](img/intro.png)

### Introduction
Each day across VA clinical staff use a suite of point-of-care applications ("VistA Applications") to create and process 50+ million documents, orders, labs, images, and transactions for veteran care. All VistA Applications process their transactions on VistA via remote procedure calls. In aggregate, these remote procedure calls (RPCs) between VistA Applications and VistA describe all clinical care transactions and workflows performed at VHA medical centers.

<p align="center">
    <img src="https://github.com/cloudvista/vaa/blob/main/img/workflow-overview.svg" width="700">
</p>

### Background
To provide a modern centralized platform for veteran healthcare delivery, VA has migrated all VistA systems from their many unique, legacy, decentralized environments across the country to a single, centralized, commercially-supported cloud platform managed by Amazon Web Services (AWS).  

This centralized cloud platform for VistA provides over two hundred new features, capabilities, and improvements for VistA that can be used to improve the quality, efficiency, and access of VA care for veterans. (See: [AWS Overview](https://docs.aws.amazon.com/whitepapers/latest/aws-overview/introduction.html))  

<p align="center">
    <img src="https://github.com/cloudvista/vaa/blob/main/img/vista-to-vaec.svg" width="700">
</p>

By leveraging the traffic streaming capability of cloud-based VistA, VHA has the first-ever opportunity to comprehensively analyze the actual workflows of all clinical staff at VA medical centers.  Such analysis would drive improved standards of practice by health care providers. These improvements would be prompted by the actual practice of care and not speculation about how care is being provided.

### Overview of Analysis
The Vista Application Analytics project will capture and analyze all end-user traffic between all VistA clients (VistA Applications) and cloud-based VistA.  This analysis will provide precise reports detailing different aspect of VA care. Analysis will include the types and volumes of structured and unstructured information read and written by clearly identified types of healthcare providers and the range of time spent on different tasks. On completion, VHA will possess a set of concrete, actionable recommendations;  demonstrations for improving  veteran care workflows and efficiency; and a comprehensie guide to perform such analyses in the future.

#### Workflow Capture
All VistA client workflows (RPC traffic flows) of cloud-based VistA are streamed to cloud storage using the built-in traffic mirroring service in the AWS Cloud.

<p align="center">
    <img src="https://github.com/cloudvista/vaa/blob/main/img/vaa-capture.svg" width="700">
</p>


#### Workflow Analysis


<p align="center">
    <img src="https://github.com/cloudvista/vaa/blob/main/img/workflow-correlation.svg" width="700">
</p>


## Schedule

__Year 1__  
1. Capture of VistA client traffic  
2. Analysis of all VistA client traffic for three VistAs  
3. Analysis of Key VistA clients  
4. VistA client use improvement report

__Year 2__  
1. Transition VistA client traffic analysis (VistA client traffic at EHRM sites)  
2. Community Care client traffic analysis (VistA client traffic for Community Care clients)


```mermaid
gantt
    dateFormat  YY-MM-DD
    title       VistA App Analytics
 
    section Traffic Capture
    Completed task            :done,    task1, 2024-09-06,2024-09-08
    Active task               :active,  task2, 2024-09-09, 30d
    Future task               :         task3, after task2, 50d
    Future task2              :         task4, after task3, 50d

    section Traffic Analytics
    Completed task in the critical line :crit, done, 2024-09-06,24h
    Implement parser and json          :crit, done, after task1, 20d
    Create tests for parser             :crit, active, 30d
    Future task in critical line        :crit, 50d
    Create tests for renderer           :20d
    Add to mermaid                      :until isadded
    Functionality added                 :milestone, isadded, 2024-09-25, 0d
    
    section Client Analytics
    Completed task in the critical line :crit, done, 2024-09-06,24h
    Implement parser and json          :crit, done, after des1, 2d
    Create tests for parser             :crit, active, 3d
    Future task in critical line        :crit, 5d
    Create tests for renderer           :2d
    Add to mermaid                      :until isadded
    Functionality added                 :milestone, isadded, 2024-09-25, 0d


    section Client Improvement
    Describe gantt syntax               :active, a1, after des1, 3d
    Add gantt diagram to demo page      :after a1  , 20h
    Add another diagram to demo page    :doc1, after a1  , 48h

```

### References
[VHA Workforce Dashboard 2023](https://www.va.gov/EMPLOYEE/docs/workforce/VA-Workforce-Dashboard-Issue-03.pdf)

