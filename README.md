# ManufacturingOps
Copilot Cowork Demo Assets for Manufacturing

Manufacturing Operations 

Copilot Cowork Plugin 

Setup & Replication Guide — v1.0 

 

Overview 

This guide walks you through setting up the Manufacturing Operations Copilot Cowork plugin, including the SharePoint document library, demo grounding documents, and the plugin package itself. The plugin provides 7 manufacturing-specific skills that leverage Work IQ to pull data from SharePoint and across Microsoft 365. 

Target audience: Copilot SEs, solution architects, and demo engineers who want to replicate the manufacturing ops demo environment. 

Prerequisites 

Microsoft 365 tenant with Copilot Cowork access (Frontier preview program) 

Admin access to M365 Admin Center (enrolled in Frontier) 

A SharePoint site for hosting grounding documents 

The ManufacturingOps.zip plugin package 

The 7 demo documents from the demo-docs/ folder 

Ability to modify the skills files and repackage them for Copilot Cowork
(Vibe works quite well for this)

 

Step 1: Set Up the SharePoint Document Library 

Create a SharePoint site and folder structure to host the manufacturing operations demo documents. 

1.1 Create or Choose a SharePoint Site 

Navigate to your SharePoint admin center or an existing team site 

For this demo, we use: https://myorg.sharepoint.com/sites/ContosoMotors 

If creating new, use a Team Site with the name matching your demo customer (e.g., Contoso Motors) 

1.2 Create the Manufacturing Ops Folder 

In the site, go to Shared Documents (the default document library) 

Create a new folder called "Manufacturing Ops" 

The final path should be: Shared Documents > Manufacturing Ops 

Full URL: https://<tenant>.sharepoint.com/sites/<SiteName>/Shared Documents/Manufacturing Ops 

1.3 Upload the Demo Documents 

Upload all 7 demo documents from the demo-docs/ folder into the Manufacturing Ops folder: 

Document 

Maps to Skill 

Daily-Production-Report-Eastside-20260519.docx 

status-report 

Capacity-Plan-EV-Motor-Housing-Q3-2026.docx 

capacity-plan 

SOP-MFG-042-CNC-Lathe-Changeover.docx 

process-doc 

Shift-Handoff-2nd-to-3rd-20260519.docx 

runbook 

ECR-2026-087-Steel-to-Aluminum-Bracket.docx 

change-request 

Risk-Assessment-Paint-Line-May-2026.docx 

risk-assessment 

ISO-9001-Audit-Readiness-Eastside-July-2026.docx 

compliance-tracking 

 

Important: Wait a few minutes after uploading for SharePoint indexing to complete before testing the skills. Work IQ needs the documents to be indexed to discover them. 

 

Step 2: Update the SharePoint URL in Skills 

If you are using a different SharePoint site than the default Contoso Motors demo environment, you must update the SharePoint URL in each skill. 

2.1 Files to Update 

Each of the 7 SKILL.md files contains a Data Sources section with the SharePoint URL. The files are located at: 

skills/status-report/SKILL.md 

skills/capacity-plan/SKILL.md 

skills/process-doc/SKILL.md 

skills/runbook/SKILL.md 

skills/change-request/SKILL.md 

skills/risk-assessment/SKILL.md 

skills/compliance-tracking/SKILL.md 

2.2 What to Change 

In each SKILL.md file, find the Data Sources section and replace the SharePoint URL: 

Find: https://m365x38311559.sharepoint.com/sites/ContosoMotors/Shared Documents/Manufacturing Ops 

Replace with: https://<your-tenant>.sharepoint.com/sites/<YourSite>/Shared Documents/Manufacturing Ops 

2.3 Rebuild the Plugin Package 

After editing the SKILL.md files, re-create the ZIP package: 

PowerShell: Compress-Archive -Path manifest.json, color.png, outline.png, skills -DestinationPath ManufacturingOps.zip -Force 

 

Step 3: How the Skills + Work IQ Integration Works 

Each skill is designed to leverage Work IQ for grounding against real data in your M365 environment. No connectors or MCP servers are required for v1. 

Skill Activation Flow 

User asks a manufacturing-related question in Copilot Cowork 

Cowork matches the request to one of the 7 skills based on the description trigger phrases in the SKILL.md frontmatter 

The skill instructs Cowork to use Work IQ to search the SharePoint Manufacturing Ops library for relevant documents 

Cowork uses the retrieved data to generate a grounded, data-informed response following the skill's output format 

Work IQ Data Sources per Skill 

Skill 

SharePoint Docs 

M365 Signals 

status-report 

Production reports, shift summaries 

Emails/Teams for production alerts, shift updates 

capacity-plan 

Capacity plans, output data 

Emails for demand changes, customer orders 

process-doc 

Existing SOPs, work instructions 

ECRs that may affect the process 

runbook 

Shift handoffs, quality holds 

Teams/email for active alerts, equipment issues 

change-request 

Prior ECRs, impact assessments 

Emails for customer/supplier requirements 

risk-assessment 

Risk registers, production data 

Emails/Teams for incidents, supplier issues 

compliance-tracking 

Audit checklists, CAPA logs 

Calendar for audit dates, email for auditor comms 

 

Step 4: Verify with Sample Prompts 

After uploading the plugin and documents, test each skill with these sample prompts in Copilot Cowork: 

status-report 

"Generate a daily production status report for Line 3 and Line 5, 2nd shift. We ran 1,200 units against a target of 1,400, had two unplanned downtime events, and one near-miss safety incident." 

capacity-plan 

"We need to increase output from 5,000 to 7,200 units/week on our assembly line. Analyze whether our current 2-shift operation with 12 operators can handle it, or if we need a 3rd shift." 

process-doc 

"Create an SOP for our CNC lathe changeover process. It involves tool swaps, fixture alignment, first-piece inspection, and requires safety glasses and cut-resistant gloves." 

runbook 

"Build a shift handoff runbook for tonight's 2nd-to-3rd shift transition. Line 1 is running normal, Line 2 has a quality hold on lot B-4417, and we're waiting on a bearing replacement for the conveyor on Line 3." 

change-request 

"Draft an engineering change request to switch from a steel bracket to aluminum on part #MC-2290. The driver is a 15% weight reduction per customer request. We need to assess tooling, quality, and PPAP impact." 

risk-assessment 

"Conduct a risk assessment for our paint line. We've had 3 unplanned stops this month, our spray nozzle supplier is single-source, and two operators are the only ones trained on the booth controls." 

compliance-tracking 

"We have an ISO 9001 surveillance audit in 6 weeks. Help me build a readiness checklist focused on clauses 8 (Operations) and 10 (Improvement) — those were our weak areas last time." 

 

Appendix A: Plugin Package Structure 

The ManufacturingOps.zip file contains the following structure: 

File / Path 

Purpose 

manifest.json 

M365 Unified App Manifest (devPreview schema) with agentSkills references 

color.png 

192x192 full-color app icon 

outline.png 

32x32 white-on-transparent outline icon 

skills/status-report/SKILL.md 

Daily production review skill 

skills/capacity-plan/SKILL.md 

Capacity planning & constraint analysis skill 

skills/process-doc/SKILL.md 

SOP / standard work / work instructions skill 

skills/runbook/SKILL.md 

Shift handoff & line-down response skill 

skills/change-request/SKILL.md 

Engineering change request skill 

skills/risk-assessment/SKILL.md 

Risk assessment & triage skill 

skills/compliance-tracking/SKILL.md 

Regulatory compliance & audit prep skill 

Appendix B: SKILL.md Format Reference 

Each skill follows the Agent Skills open standard. The SKILL.md file has two parts: 

YAML frontmatter (between --- delimiters): name, description, metadata 

Markdown body: Data Sources, Workflow, Output Format, and reference material 

 

Required frontmatter fields: 

name — kebab-case, must match the folder name exactly 

description — include trigger phrases for when the skill should activate 

 

Key section in each skill: Data Sources 

This section tells Cowork to use Work IQ to search your SharePoint library and cross-reference M365 signals. This is what grounds the skill against real data rather than generating from nothing. 

Appendix C: v2 Roadmap 

The following enhancements are planned for v2: 

Add connectors for MES/ERP system data (SAP, Oracle, Plex, etc.) 

Add reference materials in references/ subdirectories per skill for deep-dive manufacturing standards 

Custom branded icons 

Additional skills: inventory management, preventive maintenance scheduling, supplier scorecard 

Evaluate whether MCP server connectors are needed vs. Work IQ for SharePoint data access 
