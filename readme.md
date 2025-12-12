

<p align="center">
    <img src="https://github.com/cloudvista/vaa/blob/main/img/intro.png" width="600">
</p>


### Summary
VA Application Analytics (VAA) is a first-ever analysis of VA's actual clinical workflows. VAA's cloud-based traffic streaming approach to capturing workflow is a proven, deterministic, data-driven approach. It is not notional or speculative, or based on manual human observation. VAA comprehensively captures all traffic of all users and usage of clinical end-user applications across entire VA medical centers. VAA identifies, catalogs, and sequences all interactions - every click, menu, template,  dialogue, reminder, order, and transaction - down to the millisecond.

* VA clinical workflows incorporate over 30 years of accumulated institutional knowlege, governance, and congressional mandates, which are operationalized within thousands of VA- and veteran-specific care workflows. All of these care workflows are captured.
* Veteran care workflows are unique to the VA and must be preserved to meet the needs of veterans.  Capturing VA's clinical workflows enables VA to seamlessly migrate to modernized commercial EHR systems and technologies - while preserving veteran-centric care.
* Comprehensive analysis VA's workflows also improves use of VA's current care applications - improving clinical efficiency, expanding access to care, and reducing costs.
* The most used VA care application is CPRS, which supports over 115 million veteran care encounters annually. At this scale, workflow analysis which saves just one minute per veteran care encounter translates to 2 million hours of additional care for veterans - expanding access to care at no additional cost.

### Introduction
Each day in VA clinical staff use a suite of VistA client applications (the most important of which is CPRS) to create and process over 50 million documents, orders, labs, images, and transactions for veteran care. Each week VA staff use CPRS over 4.4 million hours -  more than all other application usage in VA *combined*.

<p align="center">
    <img src="https://github.com/cloudvista/vaa/blob/main/img/plot-va-app-use-nationwide.png" width="500">
</p>


All Vista client applications process their transactions on VistA via remote procedure calls (RPCs). In aggregate, these RPCs between VistA Applications and VistA describe all clinical care transactions and workflows performed at VA medical centers.
<p align="center">
    <img src="https://github.com/cloudvista/vaa/blob/main/img/workflow-overview.svg" width="700">
</p>



### Background
To provide a modern platform for veteran healthcare delivery, VA has migrated all VistA systems from their many decentralized on-premises environments across the country to a single, centralized, commercially-supported cloud platform managed by Amazon Web Services (AWS).  

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
Workflow analysis is comprised of sequential levels of increasingly nuanced analysis, each of which builds on the other:  

A. __Metrics Analysis (Statistical Analysis)__: Raw unprocessed RPC traffic is quality controlled for completeness and correctness. RPCs are identified by volume, type, use, and client

B. __Workflow Correlation Analysis (Semantic Analysis)__: Correlate the RPC sequences to each client screen and the associated user interactions (i.e. what the doctor sees and does on the screen is correlated to the RPC sequences that this generates).  This correlation is built on four parallel analyses:  
1. __Usage Analysis__: Variety of specific RPCs used by specific VistA clients (Example: 850+ distinct RPCs used by CPRS)  
2. __Sequence Analysis__: Identify the longest common sequence of RPCs behind each transaction (Eample: RPC sequence for updating an allergy)
3. __Screen Analysis__: Identify the client screens specific to each workflow (Example: screens the user sees when updating an allergy)
4. __Document Analysis__:  Identify the user documentation specific to each workflow (Example: user guide for updating an allergy)

<p align="center">
    <img src="https://github.com/cloudvista/vaa/blob/main/img/workflow-correlation.svg" width="700">
</p>


## Schedule

__Year 1: Foundational Workflow Analysis__  
1. Capture of all VistA client traffic  
2. Metrics Analysis
3. Workflow Correlation Analysis  
  i. Usage Analysis  
  ii. Sequence Analysis  
  iii. Screen Analysis  
  iv. Document Analysis
4. VistA client use improvement report - based on *actual* workflow



__Year 2: Key Client Workflow Analyses__  
1. Transition workflow analysis (VistA client traffic at an EHRM site)  
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
