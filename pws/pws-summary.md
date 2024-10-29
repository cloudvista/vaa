First: an explanation why these responses have an overwhelming IT / technology focus, rather than a clinical informatics / analytics focus.  As the author of this Product Work Statement (PWS), I have had to continuously change it over the past two years to please various committees and review boards to navigate VA's contracting processes.  Originally the PWS was an extension of a prior OIT project to analyze RPC traffic called Vista Adaptive Maintenance (VAM). The VAM project (completed in 2020) demonstrated it was possible to non-invasively capture RPC traffic from VistA systems hosted in the VA Enterprise Cloud (VAEC), and that one could do bulk summary statistics of RPC traffic. VAM however did not do any analysis of the RPC flows (workflow analytics) that this current PWS is concerned with.

In summer 2023 we were allocated funding for workflow analytics from VHA CIDMO. As a VHA funded project, we removed all "IT" associated components of the PWS.  The IT Workgroup (ITW) reviewed the PWS, and made the determination that it was indeed "non-IT" and we could  proceed using VHA funding.
In March 2024 we did market research via open public solicitation and request for information (RFI). A technical review of the RFI responses determined that there was only one viable contractor. However, rather than awarding the contract at that time to this one viable vendor, VA contracting transferred this PWS from VHA contracting to OIT contracting with an associated waiver stating that OIT can peform "IT related" tasks such as informatics and analytics.  The OIT contract vehicle is a pre-selected pool of about 30 prime contractors called T4NG.  We therefore had to transfer the PWS to the T4NG PWS contract format, which is full of IT related policies and procedures.  Again - apology for the convoluted and "noisy" responses that focus on technologies rather than analytics.
# ==============================================================================================



This brief guide is to help you sift through the noise and focus on the informatics and clinical  analytics component.

The Technical Evaluation committee will evaluate only the technical components of the response, which is  section 5.2 and 5.3.  Section 5.1 (project management) is not in scope for our review.  The PWS sections in scope to evaluate are the following:

# 5.2	VISTA CLIENT TRAFFIC CAPTURE AND ANALYSIS (Base Period)	7
5.2.1	CAPTURE OF VISTA CLIENT TRAFFIC	
5.2.2	ANALYSIS OF VISTA CLIENT TRAFFIC
5.2.3	ANALYSIS OF USE OF KEY VISTA CLIENTS
5.2.4	VISTA CLIENT USE IMPROVEMENT REPORT
# 5.3	VISTA CLIENT traffic CAPTURE AND Analysis [OPTION PERIOD 1]
5.3.1	MIGRATED VISTA CLIENT TRAFFIC ANALYSIS
5.3.2	VISTA COMMUNITY CARE CLIENT TRAFFIC ANALYSIS



1.0 	BACKGROUND

To aid maintenance and manageability of VistA, VA has migrated all VistA systems to the VA Enterprise Cloud (VAEC), a federally certified U.S. GovCloud managed by Amazon Web Services (AWS).  By leveraging the built-in traffic logging capabilities of the VAEC-based VistA systems, VHA has the first-ever opportunity to analyze the actual clinical care workflows employed in VA medical centers.  Such analysis would drive improved standards of practice by health care providers. These improvements would be prompted by the actual practice of care and not speculation about how care is being provided.

VA care is currently provided through VistA’s point of care clients (‘VistA Applications”) which communicate with the VistA servers. Taken as a whole, these communications between VistA clients and VistA servers capture the patterns of clinical care activity performed today in VA.  The Vista Application Analytics task order calls for health care data experts to analyze the traffic between VistA clients and three representative VistA servers. The analysis will be provided in a series of precise reports, detailing different aspect of VA care. 

Analysis will include the types and volumes of structured and unstructured information read and written by clearly identified classes of health care professional as well as the range of time spent on different tasks.  On completion, VHA will possess a set of concrete, actionable recommendations, and demonstrations for improving the care provided to Veterans as well as a guide for how to perform such analysis in the future.


3.0 	SCOPE OF WORK
The Contractor shall analyze the traffic exchanged between VistA clients and a representative sample of VAEC-based VistA systems. These exchanges use VA’s proprietary Remote Procedure Call (RPC) protocol. The Contractor shall use the built-in facilities of VAEC to capture this traffic non-invasively (without any need to change or reconfigure the VistA system itself or its clients). From this captured data, the Contractor shall provide detailed analysis of representative traffic, identifying point-of-care applications, user behaviors, patterns of clinical use, and areas of concern. The Contractor shall reduce the production of this analysis to a repeatable process.


# 5.2	VISTA CLIENT TRAFFIC CAPTURE AND ANALYSIS (Base Period)

5.2.1	CAPTURE OF VISTA CLIENT TRAFFIC
The Contractor shall coordinate the use of built-in VAEC facilities to non-invasively log the VistA client traffic (RPC traffic) of VAEC-hosted VistAs for a representative period. As a non-invasive method, it will not require any change, reconfiguration, interfaces, development, patches, or plugins in the VistA system itself or any client communicating with that VistA. 

=> This task requires the vendor to use facilities built into the VA Enterprise Cloud (i.e. features already built in to AWS)  to non-invasively capture RPC traffic.   The vendor needs to explain HOW they will do this, and explain WHY it is non-invasitve.  Restating the task "we will non-invasively capture RPC traffic" without an explanation proving why it is non-invasive is not sufficient. This is a show stopping requirement.  There is no way VA will allow us to touch real, live traffic flows in a production Vista-CPRS environment. That could adversely disrupt patient care.




5.2.2	ANALYSIS OF VISTA CLIENT TRAFFIC
Using the client traffic captured (deliverable 5.2.1A) , the Contractor shall provide Traffic Analysis Reports comprising the complete client traffic for each of the three analyzed VistAs. In addition, the Contractor shall provide a Cross VistA Analysis Report distinguishing cross-VistA from VistA-specific traffic patterns. 

=> This task requires the contractor to provide summary statistics and totals for volumes and varieties of client traffic of three VistAs. The contractor must explain HOW they will do this. 
Note: There is NO correlation to clinical workflows; these are just composite statistics.  


5.2.3	ANALYSIS OF USE OF KEY VISTA CLIENTS
Based on the traffic and client types isolated during the VistA traffic analysis, the Contractor shall produce a detailed Client Traffic Analysis of the operation of three of the most used VistA point-of-care applications ("Clients"). CPRS shall be one of the three; the remaining two shall be chosen after project start based on client usage. All client analyses must be validated and verifiable in a demonstrable way, matching RPC flows to specific client screens and typical tasks. The Contractor shall document the verification and validation of the analysis and provide a Client Traffic Analysis Validation and Verification Report. 

=> This task requires the contractor to match the RPC traffic flows to client screens and tasks.  There will be a unique RPC flow associated with each task (login, logoff, ordering a medication, ordering a lab, writing notes, etc.). There will be hundreds of unique RPC flows - one for each interaction / task.   The contractor must explain HOW they will do this matching of RPC flows to client screens user tasks.  The contractor must also demonstrate that the matching of these RPC flows to specific screens and tasks are complete and correct.


5.2.4	VISTA CLIENT USE IMPROVEMENT REPORT
Based solely on the Client Use Analysis Reports, the Contractor shall provide recommendations to upgrade the use of the top three RPC-using Point-of-Care VistA Clients to deliver better clinical care. 

=> This task requires the contractor to provide recommendations to upgrade CPRS (and two other clients) to deliver better clinical care (more safe, more efficient, etc). These recommendations must come from soley the clinical workflow (RPC flows) analysis of section 5.2.3.
