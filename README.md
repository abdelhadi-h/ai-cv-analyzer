# 🤖 AI CV Analyzer

> AI-powered CV analysis and job matching workflow built with n8n and OpenAI.

AI CV Analyzer is an automation workflow designed to evaluate resumes against a specific job description.

The workflow downloads a CV from a provided URL, extracts the text from the PDF, sends the resume and job requirements to an OpenAI model, and returns a structured candidate evaluation.

---

## 🚀 Overview

The workflow automates an initial CV screening process.

Instead of manually reading every resume, the workflow can:

```text
CV URL
  ↓
Download PDF
  ↓
Extract CV Text
  ↓
AI Analysis
  ↓
Candidate Evaluation
  ↓
Structured JSON
✨ Features
📄 PDF Resume Processing

The workflow downloads a resume from a provided file URL and processes it as a PDF.

The extracted document text is then passed to the AI analysis step.

🤖 AI Candidate Analysis

The workflow uses:

OpenAI GPT-4o-mini

to analyze a candidate's resume against a predefined job description.

The AI prompt evaluates:

Candidate experience
Technical skills
Job requirements
Overall suitability
Strengths
Potential concerns
📊 Candidate Evaluation

The AI returns structured evaluation data containing:

Percentage

A suitability percentage representing how well the candidate matches the role.

Summary

A short summary of the candidate's experience, personality, strengths, and concerns.

Reasons for Suitability

Specific reasons why the candidate matches the position.

Reasons for Unsuitability

Specific reasons why the candidate may not match the position.

🧠 Output Structure

Example:

{
  "percentage": 80,
  "summary": "Candidate has strong software engineering experience and relevant AI development skills.",
  "reasons-suit": [
    {
      "name": "Relevant Experience",
      "text": "Candidate has experience aligned with the software engineering requirements."
    }
  ],
  "reasons-notsuit": [
    {
      "name": "Experience Gap",
      "text": "Candidate may not meet the required years of professional experience."
    }
  ]
}

The exact output depends on the submitted CV and job description.

🔧 Workflow Architecture
┌────────────────────────────┐
│     Manual Trigger         │
│    Test Workflow           │
└──────────────┬─────────────┘
               │
               ▼
┌────────────────────────────┐
│      Set Variables         │
│                            │
│ • CV URL                   │
│ • Job Description          │
│ • AI Prompt                │
│ • JSON Schema              │
└──────────────┬─────────────┘
               │
               ▼
┌────────────────────────────┐
│       Download File        │
│       HTTP Request         │
└──────────────┬─────────────┘
               │
               ▼
┌────────────────────────────┐
│    Extract Document PDF    │
│       PDF → Text           │
└──────────────┬─────────────┘
               │
               ▼
┌────────────────────────────┐
│    OpenAI CV Analysis      │
│       GPT-4o-mini          │
└──────────────┬─────────────┘
               │
               ▼
┌────────────────────────────┐
│        Parsed JSON         │
│   Structured Evaluation    │
└────────────────────────────┘
🛠️ Technology Stack
Technology	Purpose
n8n	Workflow automation
OpenAI	AI-powered CV analysis
GPT-4o-mini	Resume evaluation
HTTP Request	Download CV files
PDF Extraction	Extract resume text
JSON Schema	Structured AI output
📋 Workflow Inputs

The current workflow defines:

CV File URL
file_url
Job Description
job_description
AI Prompt
prompt
Output Schema
json_schema
💼 Example Job

The workflow currently includes a Software Engineer job description covering areas such as:

Software engineering
Machine learning
NLP
LangChain
LangGraph
Cloud platforms
Docker
Kubernetes
CI/CD
Product development

The job description can be replaced with another role.

🔄 How It Works
1. Provide a CV

A PDF resume URL is provided to the workflow.

2. Provide a Job Description

The system receives the requirements for the position.

3. Download the CV

The HTTP Request node downloads the PDF.

4. Extract the Resume

The PDF extraction node converts the document into text.

5. Analyze the Candidate

The extracted resume is sent to OpenAI together with the job description and evaluation instructions.

6. Validate the Result

The AI response is returned using a predefined JSON schema.

7. Parse the Evaluation

The final node converts the response into structured JSON data.

📌 Current Workflow

The workflow currently contains:

When clicking ‘Test workflow’
        ↓
Set Variables
        ↓
Download File
        ↓
Extract Document PDF
        ↓
OpenAI - Analyze CV
        ↓
Parsed JSON
🧪 Example Input
{
  "file_url": "https://example.com/resume.pdf",
  "job_description": "Software Engineer with experience in cloud, AI, and production systems."
}
📤 Example Output
{
  "percentage": 70,
  "summary": "Candidate has relevant technical experience but does not fully meet all requirements.",
  "reasons-suit": [
    {
      "name": "Technical Skills",
      "text": "Candidate has experience with technologies relevant to the position."
    }
  ],
  "reasons-notsuit": [
    {
      "name": "Experience",
      "text": "Candidate may not meet the required professional experience."
    }
  ]
}
🔐 Security

Never expose API credentials in a public repository.

Do not commit:

OpenAI API keys
Private CVs
Personal candidate information
Private file URLs
Internal company information
Production credentials

Use n8n credential management for authentication.

⚠️ Privacy

CVs contain personal information.

Before using this workflow with real candidates, ensure that your implementation follows the applicable privacy and data-protection requirements for your organization and region.

For public demonstrations, use fictional or anonymized candidate data.

📁 Project Structure
ai-cv-analyzer/
│
├── README.md
│
├── .gitignore
│
└── workflows/
    └── ai-cv-analyzer.json
🔧 Installation
1. Install n8n

You can run n8n locally or use a hosted n8n instance.

Official documentation:

https://docs.n8n.io/

2. Import the Workflow

Import:

workflows/ai-cv-analyzer.json

into n8n.

3. Configure OpenAI

Connect your OpenAI credentials in n8n.

4. Configure Variables

Update:

CV URL
Job description
Prompt
JSON schema
5. Run the Workflow

Use the manual trigger to test the workflow.

🎯 Use Cases

This workflow can be used as a foundation for:

AI CV screening
Recruitment automation
Candidate matching
HR automation
Recruitment agencies
Technical hiring
Resume analysis
Job application screening
🏢 Recruitment Automation

The workflow can become part of a larger recruitment system:

Candidate
    ↓
Application Form
    ↓
CV Upload
    ↓
AI CV Analyzer
    ↓
Candidate Evaluation
    ↓
Recruiter Dashboard
    ↓
Interview
🔮 Roadmap
Phase 1 — CV Analysis
 PDF CV extraction
 Job description analysis
 OpenAI integration
 Structured JSON output
 Candidate suitability percentage
 Strength analysis
 Concern analysis
Phase 2 — Recruitment Automation
 Application form
 Candidate database
 Automated email
 HR notifications
 Candidate pipeline
Phase 3 — AI Recruitment Platform
 Multiple job descriptions
 Job-specific candidate matching
 Candidate search
 Recruiter dashboard
 Interview automation
 Candidate scoring
 Recruitment analytics
🧠 Future Architecture
                    Candidates
                         │
                         ▼
                  Application Form
                         │
                         ▼
                    CV Upload
                         │
                         ▼
                  AI CV Analyzer
                         │
              ┌──────────┴──────────┐
              ▼                     ▼
        Candidate Score       AI Summary
              │                     │
              └──────────┬──────────┘
                         ▼
                  Candidate Database
                         │
                         ▼
                  Recruiter Dashboard
                         │
                         ▼
                      Interview
📈 Why Automation?

The goal is to remove repetitive steps from the initial screening process.

Traditional process:

Open CV
   ↓
Read CV
   ↓
Compare with Job
   ↓
Write Notes
   ↓
Evaluate Candidate

Automated process:

Upload CV
   ↓
AI Analysis
   ↓
Structured Evaluation

This allows recruiters to receive consistent, structured information during the initial screening stage.

📚 What This Project Demonstrates

This project demonstrates practical integration of:

AI
Workflow automation
Document processing
Resume analysis
API integration
Structured AI outputs
JSON schemas
Recruitment automation
📌 Project Status

Status: MVP / Proof of Concept

Current workflow:

PDF
 ↓
Text Extraction
 ↓
OpenAI
 ↓
Candidate Evaluation
 ↓
JSON
👨‍💻 Author
Abdelhadi Habibi

Computer Science student and builder focused on:

Artificial Intelligence
Automation
SaaS
Business Systems
HR Automation
Workflow Automation
📄 License

This project is currently provided for educational, demonstration, development, and experimentation purposes.

A formal open-source license can be added in a future release.

⭐ Project Vision

Turn resumes into structured hiring intelligence.

CV
 ↓
AI
 ↓
Analysis
 ↓
Structured Data
 ↓
Recruitment Decision Support

Built with:

n8n + OpenAI + AI Automation
