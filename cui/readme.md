# Constrained  User Intent Model

A Constrained User Intent (CUI) model is an abstraction that captures the workflow of end-user clients in a portable, machine-processable, vendor-neutral, UI-agnostic form. 

A CUI model of VA's current clinical client (CPRS) enables migration of VA's current workflow to the new commercial EHR client (Powerchart).  A CUI models are the most understandable by AI and LLM systems, and thus also enable next-generation agentic AI-driven workflows.


```mermaid
stateDiagram-v2
    state OrderWorkflow {
        ViewOrders --> EnterOrder --> SignOrder
    }

    [*] --> OrderWorkflow
    OrderWorkflow --> [*]

```

---

1. Candidate High-Level Abstractions

Abstraction	Scope	Pros	Cons / Limitations

Constrained User Intent (CUI) / Task Ontology	Encodes what the user wants to achieve, independent of screens or RPCs	
• UI-independent
• Maps to backend via intent handlers
• Supports AI-agent-driven UX
• Vendor-neutral	
• Needs detailed ontology of clinical tasks
• May miss low-level UI nuances unless extended


Clinical Task / Activity Model (workflow ontology)	
Focus on tasks, sequences, decision points in care delivery	• Captures clinical reasoning<br>• Can link to FHIR resources<br>• Can drive automation and AI agents	• Not always granular enough for UI reconstruction<br>• Task sequencing can be context-specific
FHIR Workflow / PlanDefinition / ActivityDefinition	HL7 FHIR-based definitions of clinical processes	• Standardized and vendor-neutral<br>• Machine-readable<br>• Supports execution logic	• Designed more for care pathways than individual UI actions<br>• Limited semantic richness for clinician intent
OpenEHR Task/Action/Composition Model	Detailed structured clinical tasks / composition of entries	• Vendor-neutral<br>• Supports clinical semantics	• Adoption outside archetype communities is limited<br>• Less focused on end-user UI workflow
Human-Computer Interaction (HCI) Workflow Model	Screens → Actions → Sequences (abstracted)	• Captures actual UI behavior<br>• Can be reverse-engineered from RPC logs	• Hard to generalize across vendors<br>• Tightly coupled to prior UI unless abstracted



---

2. Recommended Abstraction: CUI + Task Ontology Layer

Definition:
A Constrained User Intent (CUI) ontology represents what the clinician intends to do in a semantic, structured way:

Example:

Intent: “Place a new medication order”

Attributes: patient context, medication type, route, dose, schedule

Outcome: order submitted



Why this works:

1. UI-agnostic – the same intent can be executed via CPRS or Powerchart UI.


2. Backend-agnostic – can map to different RPCs, FHIR endpoints, or database actions.


3. Migration-ready – allows generation of equivalent workflows in new EHR.


4. AI-agent-ready – AI can reason over user intents rather than screen sequences.


5. Composable – multiple CUIs can be linked to model complex workflows.




---

3. Implementation Strategy

1. Extract “As-Is” Workflow

Map CPRS RPC sequences to CUIs rather than screen clicks.

Example: RPC: ORWDXR ORDER_NEW → CUI: CreateMedicationOrder.



2. Define Task Ontology

Define high-level clinical tasks:

Medication ordering

Lab ordering

Note documentation

Imaging request


Include attributes, constraints, preconditions, and outcomes.



3. Abstract Sequencing / Context

Encode possible sequences (pre/post conditions) independent of UI.

Example: Lab order must follow patient selection; note documentation may occur before or after labs.



4. Vendor-Neutral Representation

Options:

OWL / RDF ontology for semantic reasoning.

FHIR PlanDefinition + ActivityDefinition for machine-readable clinical workflow.

BPMN / CMMN for task sequencing (if you need a visual, executable workflow).




5. AI Integration Layer

Map CUIs to AI agents:

Chat-based UX: “I want to order a stat CBC for John Doe” → AI maps to CreateLabOrder(CBC, STAT, John Doe).

Agentic automation: AI triggers appropriate backend calls dynamically.






---

4. Summary Recommendation

High-level abstraction: CUI / Task Ontology

Features:

UI-independent

Backend-independent

Semantic, machine-readable

Supports AI-driven UX


Migration & AI approach:

Map legacy RPC sequences to CUIs

Use ontology to define possible workflows

Generate equivalent workflows in target EHR (Powerchart)

Use AI to interpret CUIs into end-user actions dynamically



Key principle: Model “intent” and “task outcome”, not UI clicks or RPC sequences.


---

If you want, I can draft a concrete example of a CUI + task ontology mapping for CPRS → Powerchart, showing how it can drive both migration and AI-agent UX. This would include a small ontology snippet and example workflow. Do you want me to do that next?



```mermaid
flowchart TD
    %% Start node
    Start([Start])
    
    %% Patient selection
    SP[Select Patient]
    CheckPatient{Patient exists?}
    CheckEncounter{Active encounter?}
    
    %% End node
    End([End])
    
    %% Start flow
    Start --> SP
    SP --> CheckPatient
    CheckPatient -- No --> End
    CheckPatient -- Yes --> CheckEncounter
    CheckEncounter -- No --> ScheduleFU
    CheckEncounter -- Yes --> Intent{UserIntent?}
    
    %% CreateMedicationOrder
    subgraph CreateMedicationOrder["Create Medication Order"]
        Med1[Search Medication]
        Med2[Specify Dose/Schedule]
        Med3[Check Allergies]
        Med4[Confirm Order]
        MedOutcome[Order Submitted]
        Med1 --> Med2 --> Med3 --> Med4 --> MedOutcome
    end
    
    %% DiscontinueMedication
    subgraph DiscontinueMedication["Discontinue Medication"]
        Dis1[Retrieve Active Medications]
        Dis2[Choose Medication]
        Dis3[Confirm Discontinuation]
        DisOutcome[Medication Discontinued]
        Dis1 --> Dis2 --> Dis3 --> DisOutcome
    end
    
    %% OrderRefill
    subgraph RefillMed["Order Refill"]
        Refill1[Retrieve Active Medications]
        Refill2[Identify Refill]
        Refill3[Confirm Refill]
        RefillOutcome[Refill Processed]
        Refill1 --> Refill2 --> Refill3 --> RefillOutcome
    end
    
    %% CreateLabOrder
    subgraph CreateLabOrder["Create Lab Order"]
        Lab1[Search Lab Test]
        Lab2[Specify Priority/Specimen]
        Lab3[Confirm Order]
        LabOutcome[Lab Order Submitted]
        Lab1 --> Lab2 --> Lab3 --> LabOutcome
    end
    
    %% SignLabResult
    subgraph SignLabResult["Sign Lab Result"]
        SL1[Select Lab]
        SL2[Review Result]
        SL3[Verify Abnormalities]
        SL4[Sign Result]
        SL4 --> SLOutcome[Lab Result Signed]
    end
    
    %% CreateImagingOrder
    subgraph CreateImagingOrder["Create Imaging Order"]
        Img1[Select Modality]
        Img2[Specify Body Part/Protocol]
        Img3[Set Priority]
        Img4[Confirm Order]
        ImgOutcome[Imaging Order Submitted]
        Img1 --> Img2 --> Img3 --> Img4 --> ImgOutcome
    end
    
    %% DocumentProgressNote
    subgraph DocumentProgressNote["Document Progress Note"]
        Prog1[Choose Note Template]
        Prog2[Enter Text]
        Prog3[Attach Observations]
        Prog4[Sign Note]
        ProgOutcome[Progress Note Signed]
        Prog1 --> Prog2 --> Prog3 --> Prog4 --> ProgOutcome
    end
    
    %% DocumentProcedure
    subgraph DocumentProcedure["Document Procedure"]
        Proc1[Choose Procedure Template]
        Proc2[Enter Details/Outcomes]
        Proc3[Sign Procedure]
        ProcOutcome[Procedure Documented]
        Proc1 --> Proc2 --> Proc3 --> ProcOutcome
    end
    
    %% RequestConsult
    subgraph RequestConsult["Request Consult"]
        Con1[Choose Consult Type]
        Con2[Specify Reason/Details]
        Con3[Submit Consult]
        ConOutcome[Consult Request Submitted]
        Con1 --> Con2 --> Con3 --> ConOutcome
    end
    
    %% ScheduleFollowUp
    subgraph ScheduleFollowUp["Schedule Follow-Up"]
        FU1[Choose Follow-Up Type]
        FU2[Specify Date/Time]
        FU3[Confirm]
        FUOutcome[Follow-Up Scheduled]
        FU1 --> FU2 --> FU3 --> FUOutcome
    end
    
    %% EnterAllergy
    subgraph EnterAllergy["Enter Allergy"]
        All1[Enter Allergen/Reaction]
        All2[Set Severity]
        All3[Save]
        AllOutcome[Allergy Documented]
        All1 --> All2 --> All3 --> AllOutcome
    end
    
    %% ReviewMedications
    subgraph ReviewMedications["Review Medications"]
        RM1[Retrieve Active Medications]
        RM2[Review Allergies/Interactions]
        RM3[Document Findings]
        RMOutcome[Medications Reviewed]
        RM1 --> RM2 --> RM3 --> RMOutcome
    end
    
    %% ReviewVitals
    subgraph ReviewVitals["Review Vitals"]
        RV1[Retrieve Vitals]
        RV2[Compare to Thresholds]
        RV3[Document Findings]
        RVOutcome[Vitals Reviewed]
        RV1 --> RV2 --> RV3 --> RVOutcome
    end
    
    %% ViewClinicalSummary
    subgraph ViewClinicalSummary["View Clinical Summary"]
        VS1[Retrieve Summary Sections]
        VS2[Review/Filter]
        VSOutcome[Summary Reviewed]
        VS1 --> VS2 --> VSOutcome
    end
    
    %% GeneratePatientReport
    subgraph GeneratePatientReport["Generate Patient Report"]
        GR1[Choose Report Type]
        GR2[Filter Dates/Sections]
        GR3[Generate]
        GR4[Export]
        GROutcome[Report Generated]
        GR1 --> GR2 --> GR3 --> GR4 --> GROutcome
    end
    
    %% Intent mapping to subgraphs
    Intent --> CreateMedicationOrder
    Intent --> DiscontinueMedication
    Intent --> RefillMed
    Intent --> CreateLabOrder
    Intent --> SignLabResult
    Intent --> CreateImagingOrder
    Intent --> DocumentProgressNote
    Intent --> DocumentProcedure
    Intent --> RequestConsult
    Intent --> ScheduleFollowUp
    Intent --> EnterAllergy
    Intent --> ReviewMedications
    Intent --> ReviewVitals
    Intent --> ViewClinicalSummary
    Intent --> GeneratePatientReport
    
    %% Connect subgraph outcomes back to End
    MedOutcome --> End
    DisOutcome --> End
    RefillOutcome --> End
    LabOutcome --> End
    SLOutcome --> End
    ImgOutcome --> End
    ProgOutcome --> End
    ProcOutcome --> End
    ConOutcome --> End
    FUOutcome --> End
    AllOutcome --> End
    RMOutcome --> End
    RVOutcome --> End
    VSOutcome --> End
    GROutcome --> End
```

