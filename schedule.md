# VAA Schedule

# 5.2	VISTA CLIENT TRAFFIC CAPTURE AND ANALYSIS (Base Period)	7
5.2.1	CAPTURE OF VISTA CLIENT TRAFFIC	
5.2.2	ANALYSIS OF VISTA CLIENT TRAFFIC
5.2.3	ANALYSIS OF USE OF KEY VISTA CLIENTS
5.2.4	VISTA CLIENT USE IMPROVEMENT REPORT
# 5.3	VISTA CLIENT traffic CAPTURE AND Analysis [OPTION PERIOD 1]
5.3.1	MIGRATED VISTA CLIENT TRAFFIC ANALYSIS
5.3.2	VISTA COMMUNITY CARE CLIENT TRAFFIC ANALYSIS




# 5.1.3	TECHNICAL KICKOFF MEETING
A technical kickoff meeting shall be held within 10 days after TO award.  The Contractor shall coordinate the date, time, and location (can be virtual) with the Contracting Officer (CO), as the Post-Award Conference Chairperson, the VA PM, as the Co-Chairperson, the Contract Specialist (CS), and the COR.  

The Contractor shall provide a draft agenda to the CO and VA PM at least five (5) calendar days prior to the meeting.  Upon Government approval of a final agenda, the Contractor shall distribute to all meeting attendees.  During the kickoff-meeting, the Contractor shall present, for review and approval by the Government, the details of the intended approach, work plan, and project schedule for each effort via a Microsoft PowerPoint presentation.  At the conclusion of the meeting, the Contractor shall update the presentation with a final slide entitled “Summary Report” which shall include notes on any major issues, agreements, or disagreements discussed during the kickoff meeting and the following statement “As the Post-Award Conference Chairperson, I have reviewed the entirety of this presentation and assert that it is an accurate representation and summary of the discussions held during the Technical Kickoff Meeting for the VistA Application Analytics effort.”  The Contractor shall compile the PowerPoint into a Microsoft Word document and submit the final Microsoft Word document to the CO for review and signature within three (3) calendar days after the meeting.  

The Contractor shall also work with the CS, the Government’s designated note taker, to prepare and distribute the meeting minutes of the kickoff meeting to the CO, COR and all attendees within three (3) calendar days after the meeting.  The Contractor shall obtain concurrence from the CS on the content of the meeting minutes prior to distribution of the document.



# 5.2.1	CAPTURE OF VISTA CLIENT TRAFFIC

The Contractor shall coordinate the use of built-in VAEC facilities to non-invasively log the VistA client traffic (RPC traffic) of VAEC-hosted VistAs for a representative period. As a non-invasive method, it will not require any change, reconfiguration, interfaces, development, patches, or plugins in the VistA system itself or any client communicating with that VistA. 

The Contractor shall coordinate the logging of all client traffic of three VAEC-based production VA VistAs (“Analyzed VistAs”). At least one of the VistAs should support a large integrated medical facility.
  
The Contractor shall:
a)	In collaboration with the Government, identity three VistAs and obtain permission from their managers to capture their RPC traffic. 
b)	Coordinate the configuration of the RPC Traffic capture to log all RPC traffic for these three VistAs.  
c)	Monitor and ensure traffic logging of each of the three identified VistAs for at least one month and the storage of all captured data in VAEC for analysis.
d)	Develop and provide a VistA Traffic Logging Standard Operating Procedure to document the processes and procedures used to log required traffic from any VistA, including permissions required from VistA owners and VAEC maintainers

Deliverables:
A.	    VistA Traffic Logging Standard Operating  Procedure 





# 5.2.2	ANALYSIS OF VISTA CLIENT TRAFFIC

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




# 5.2.3	ANALYSIS OF USE OF KEY VISTA CLIENTS

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




# 5.2.4	VISTA CLIENT USE IMPROVEMENT REPORT

Based solely   on the Client Use Analysis Reports, the Contractor shall provide recommendations to upgrade the use of the top three RPC-using Point-of-Care VistA Clients to deliver better clinical care. These recommendations shall be documented in Client Use Improvement Reports for each Client in Microsoft Word and a supporting PowerPoint presentation. 

Deliverables:  
A.	Client Use Improvement Reports



=> This task requires the contractor to provide recommendations to upgrade CPRS (and two other clients) to deliver better clinical care (more safe, more efficient, etc). These recommendations must come from soley the clinical workflow (RPC flows) analysis of section 5.2.3.
