
## VistA Application Analytics

Vist Applicaton Analytics (VAA) provides comprehensive cloud-based capture and analytics of all interactions, transactions, and workflows of all VistA end-user applications, enabling data-driven improvement of efficiency, safety, and workflows across the VA healthcare system.

![](img/vaa-intro1.png)

![vaa-implementation](img/vam.svg)


![vaa-cloud](img/vaa-analyses.svg)


| analysis | storage | technique | summary |
|---------|----------|-----------|---------|
| Simple |  S3 | direct RPC queries | foundation metrics|
| Filtered | DynamoDB | RPC extraction scripts | RPC name, type, attributes |
| Sequence | RedshiftDB | RPC sequence reduction | longest common sequence (LCS) identification |
| Workflow | github | VDL reduction | download -> parse, isolate, index -> flowchart (mermaid) |
| Correlation | github | sequence comparison to workflow | Task Set identification |



#### Work Statement
```text
5.2	VISTA CLIENT TRAFFIC CAPTURE AND ANALYSIS (Base Period)
5.2.1	CAPTURE OF VISTA CLIENT TRAFFIC	
5.2.2	ANALYSIS OF VISTA CLIENT TRAFFIC
5.2.3	ANALYSIS OF USE OF KEY VISTA CLIENTS
5.2.4	VISTA CLIENT USE IMPROVEMENT REPORT

5.3	VISTA CLIENT traffic CAPTURE AND Analysis [Option Period)
5.3.1	MIGRATED VISTA CLIENT TRAFFIC ANALYSIS
5.3.2	VISTA COMMUNITY CARE CLIENT TRAFFIC ANALYSIS
```


#### Schedule
```mermaid
gantt
    dateFormat  YY-MM-DD
    title       VistA App Analytics
 
    section 5.2.1
    Completed task            :done,    task1, 2024-09-06,2024-09-08
    Active task               :active,  task2, 2024-09-09, 3d
    Future task               :         task3, after task2, 5d
    Future task2              :         task4, after task3, 5d

    section 5.2.2
    Completed task in the critical line :crit, done, 2024-09-06,24h
    Implement parser and jison          :crit, done, after task1, 2d
    Create tests for parser             :crit, active, 3d
    Future task in critical line        :crit, 5d
    Create tests for renderer           :2d
    Add to mermaid                      :until isadded
    Functionality added                 :milestone, isadded, 2024-09-25, 0d
    
    section 5.2.3
    Completed task in the critical line :crit, done, 2024-09-06,24h
    Implement parser and jison          :crit, done, after des1, 2d
    Create tests for parser             :crit, active, 3d
    Future task in critical line        :crit, 5d
    Create tests for renderer           :2d
    Add to mermaid                      :until isadded
    Functionality added                 :milestone, isadded, 2024-09-25, 0d

    section 5.2.4
    Describe gantt syntax               :after doc1, 3d
    Add gantt diagram to demo page      :20h
    Add another diagram to demo page    :48h

    section Documentation
    Describe gantt syntax               :active, a1, after des1, 3d
    Add gantt diagram to demo page      :after a1  , 20h
    Add another diagram to demo page    :doc1, after a1  , 48h

```


### 5.2.1 CAPTURE OF VISTA CLIENT TRAFFIC

The Contractor shall coordinate the use of built-in VAEC facilities to non-invasively log the VistA client traffic (RPC traffic) of VAEC-hosted VistAs for a representative period. As a non-invasive method, it will not require any change, reconfiguration, interfaces, development, patches, or plugins in the VistA system itself or any client communicating with that VistA. 

The Contractor shall coordinate the logging of all client traffic of three VAEC-based production VA VistAs (“Analyzed VistAs”). At least one of the VistAs should support a large integrated medical facility.  
   
The Contractor shall:  
a)	In collaboration with the Government, identity three VistAs and obtain permission from their managers to capture their RPC traffic  
b)	Coordinate the configuration of the RPC Traffic capture to log all RPC traffic for these three VistAs.  
c)	Monitor and ensure traffic logging of each of the three identified VistAs for at least one month and the storage of all captured data in VAEC for analysis.  
d)	Develop and provide a VistA Traffic Logging Standard Operating Procedure to document the processes and procedures used to log required traffic from any VistA, including permissions required from VistA owners and VAEC maintainers

Deliverables:  
A.  VistA Traffic Logging Standard Operating  Procedure  

=> This task requires the vendor to use facilities built into the VA Enterprise Cloud (i.e. features already built in to AWS)  to non-invasively capture RPC traffic. 



### 5.2.2	ANALYSIS OF VISTA CLIENT TRAFFIC

Using the client traffic captured (deliverable 5.2.1A) , the Contractor shall provide Traffic Analysis Reports comprising the complete client traffic for each of the three analyzed VistAs. In addition, the Contractor shall provide a Cross VistA Analysis Report distinguishing cross-VistA from VistA-specific traffic patterns. All four reports (i.e. 3 Traffic Analysis Reports and 1 Cross VistA Analysis Report) shall be composed in GitHub compatible markdown with embedded graphics where appropriate. The Contractor shall store all four reports as markdown in the VA Enterprise GitHub. 

Traffic Analysis Report for each VistA shall characterize:  
a)	User volume  
b)	Client types and volume of use  
c)	Connection volumes, frequency, and duration  
d)	Types of user authentication/security and relative use  
e)	Machine from end Users  
f)	RPC usage frequency and execution times  
g)	RPC groupings – representing transactions  
h)	RPCs specific to a VistA from cross-VistA RPCs  

DELIVERABLES:  
A.	Traffic Analysis Reports for three production VistAs  
B.	Cross VistA Traffic Analysis Report


=> This task requires the contractor to provide summary statistics and totals for volumes and varieties of client traffic of three VistAs.




### 5.2.3	ANALYSIS OF USE OF KEY VISTA CLIENTS

Based on the traffic and client types isolated during the VistA traffic analysis, the Contractor shall produce a detailed Client Traffic Analysis of the operation of three of the most used VistA point-of-care applications ("Clients"). CPRS shall be one of the three; the remaining two shall be chosen after project start based on client usage. All three reports shall be composed in GitHub compatible markdown with embedded graphics where appropriate.  The Contractor shall store the three reports in a git in the VA Enterprise GitHub.   All client analyses must be validated and verifiable in a demonstrable way, matching RPC flows to specific client screens and typical tasks. The Contractor shall document the verification and validation of the analysis and provide a Client Traffic Analysis Validation and Verification Report. 

The per Client Traffic Analysis shall include:  
a)	User volumes and types. User types shall capture clinical care specialties and roles.  
b)	Connection volume and duration, tying frequency of client use to user types  
c)	Types of user authentication/security and relative use  
d)	Patient volumes  
e)	Enumeration of all RPCs used by a client and their relative use  
f)	Distinction of clinical from non-clinical RPCs  
g)	Distinction of RPCs that change (write) from those that read the clinical record  
h)	Distinction of slow running, high overhead and variable overhead RPCs  
i)	Clinical care task sets, represented as groups of RPCs used in tandem  
j)	Match task sets with the use of one or more specific client screens  
k)	Task sets employed by different user types  
l)	Isolate performance issues with patterns of use that slow care  
m)	Verification and validation that the analysis accurately captures care provision  

Deliverables:  
A.	Three (3)  VistA Client Use Analysis Reports  
B.	Client Analysis Validation and Verification Report


=> This task requires the contractor to match the RPC traffic flows to client screens and tasks.  There will be a unique RPC flow associated with each task (login, logoff, ordering a medication, ordering a lab, writing notes, etc.). There will be hundreds of unique RPC flows - one for each interaction / task.   The contractor must explain HOW they will do this matching of RPC flows to client screens user tasks.  The contractor must also demonstrate that the matching of these RPC flows to specific screens and tasks are complete and correct.



### 5.2.4	VISTA CLIENT USE IMPROVEMENT REPORT

Based solely   on the Client Use Analysis Reports, the Contractor shall provide recommendations to upgrade the use of the top three RPC-using Point-of-Care VistA Clients to deliver better clinical care. These recommendations shall be documented in Client Use Improvement Reports for each Client in Microsoft Word and a supporting PowerPoint presentation. 

Deliverables:  
A.	Client Use Improvement Reports  


=> This task requires the contractor to provide recommendations to upgrade CPRS (and two other clients) to deliver better clinical care (more safe, more efficient, etc). These recommendations must come from soley the clinical workflow (RPC flows) analysis of section 5.2.3.
