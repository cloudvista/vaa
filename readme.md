![](img/intro.png)

### Summary
By leveraging the traffic streaming capability of cloud-based VistA, VHA has the first-ever opportunity to comprehensively analyze the actual workflows of all clinical staff at VA medical centers.  Such analysis would drive improved standards of practice by health care providers. These improvements would be prompted by the actual practice of care and not speculation about how care is being provided.

* VAA is about workflow, analyzed by categorizing and sequencing the RPC traffic it leads to.
* Knowing VA'a actual, current workflows is key for better operations and migration to new systems.
* Not all workflows or screens are equal - what is most used? What quick orders or note templates truly matter? … all this information is in the traffic of the Vista Clients.




### Introduction
Each day across VA clinical staff use a suite of VistA point-of-care applications (CPRS and 40+ others) to create and process over 50 million documents, orders, labs, images, and transactions for veteran care. All VistA Applications process their transactions on VistA via remote procedure calls. In aggregate, these remote procedure calls (RPCs) between VistA Applications and VistA describe all clinical care transactions and workflows performed at VHA medical centers.

<p align="center">
    <img src="https://github.com/cloudvista/vaa/blob/main/img/workflow-overview.svg" width="700">
</p>

### Background
To provide a modern platform for veteran healthcare delivery, VA has migrated all VistA systems from their many unique, legacy, decentralized environments across the country to a single, centralized, commercially-supported cloud platform managed by Amazon Web Services (AWS).  

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
Workflow analysis is comprised of several sequential levels of analysis, each of which builds on the prior:
1. Bulk Analysis: All RPC traffic of a VistA is quality controlled; All RPCs are identified, parsed, and classified by type, use, and client
2. Sequence Analysis: The longest common sequence of RPCs are identified, and correlated to specific transactions
3. Screen Analysis: The client screens are identified and correlated to specific types of actions or transactions
4. Document Analysis:  Workflows as documented in the official client user manuals is identified and broken down to specific actions and transactions
5. Workflow Correlation Analysis: The actual workflow (Sequence Analysis), the actual screens (Screen Analysis), and the documented workflows (Document Analysis) are correlated to validate and verify completeness and correctness of workflow analysis.


<p align="center">
    <img src="https://github.com/cloudvista/vaa/blob/main/img/workflow-correlation.svg" width="700">
</p>


## Schedule

__Year 1: Foundational Workflow Analysis__  
1. Capture of all VistA client traffic  
2. Statistical Analysis of all traffic
   1. Bulk Analysis
3. Semantic analysis of all traffic
   1. Screen Analysis
   2. Document Analysis
   3. Sequence Analysis
   4. Workflow Correlation Analysis
4. VistA client use improvement report

__Year 2: Key Client Workflow Analyses__  
1. Transition site workflow analysis (VistA client traffic at an EHRM site)  
2. Community Care workflow analysis (VistA client traffic for Community Care)


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
