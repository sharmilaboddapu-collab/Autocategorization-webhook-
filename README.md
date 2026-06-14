# Autocategorization-webhook-
Project Title
Auto Categorization Webhook

Business Problem
Manual ticket tagging is slow and inconsistent.
In organizations, customer support and IT helpdesk teams receive hundreds of tickets daily. Agents manually assign categories and priorities based on their understanding.
Problems with manual tagging:
Time-consuming process
Inconsistent categorization
Incorrect ticket routing
Delayed issue resolution
Poor reporting and analytics
An automated AI-driven solution is needed to improve speed, consistency, and accuracy.

Project Objective
Develop a FastAPI webhook that automatically classifies incoming support tickets using an LLM.
The system should:
Receive ticket JSON
Analyze ticket content
Predict category
Predict subcategory
Assign priority
Return structured JSON output
Store prediction logs

Expected POC Output
Input Ticket
{ “ticket_id”:“INC101”, “subject”:“Unable to login”, “description”:“Password reset link is not working” }
Output
{ “ticket_id”:“INC101”, “category”:“Access Management”, “subcategory”:“Password Reset”, “priority”:“High”, “confidence”:“0.95” }

AI Capability Demonstrated
Mandatory Capability Selected
Agent Loop
The application follows an AI Agent workflow:
Receive Ticket ↓ Load Examples ↓ Analyze Input ↓ Send Prompt to LLM ↓ Validate Response ↓ Generate Output ↓ Store Logs
The system automatically decides the next action at every stage.

Few-Shot Classification
Historical examples are loaded from samples.json.
Example:
Input: “Forgot password and unable to login”
Output:
Category: Access Management
Subcategory: Password Reset
Priority: High
These examples guide the LLM in making accurate predictions.

Structured Output
The AI returns data in fixed JSON format.
{ “category”:““,”subcategory”:““,”priority”:““,”confidence”:“” }
This ensures consistency and easy integration with other systems.

Technology Stack
Category
Technology
Source Control
GitHub
Programming Language
Python
API Framework
FastAPI
AI Model
Ollama / Gemini / Groq
Database
SQLite
Data Source
JSON
Logging
Python Logging
Testing
Pytest
Collaboration
Discord
Version Control
GitHub

System Architecture
Client Application |
v +———————-+ | FastAPI Webhook | +———-+———–+ | v +———————-+ | Few-Shot Examples | | samples.json | +———-+———–+ | v +———————-+ | LLM Processing | +———-+———–+ | v +———————-+ | JSON Validation | +———-+———–+ | v +———————-+ | Logging System | +———-+———–+ | v +———————-+ | JSON Response | +———————-+

Project Workflow
Step 1: Receive ticket JSON request.
Step 2: Load few-shot examples from samples.json.
Step 3: Construct prompt using ticket details.
Step 4: Send prompt to AI model.
Step 5: Generate classification.
Step 6: Validate structured JSON.
Step 7: Log prediction results.
Step 8: Return enriched JSON response.

API Endpoint
POST /classify
Request
{ “ticket_id”:“INC001”, “subject”:“VPN not connecting”, “description”:“Unable to access VPN” }
Response
{ “ticket_id”:“INC001”, “category”:“Network”, “subcategory”:“VPN”, “priority”:“Medium”, “confidence”:“0.92” }

Sample Data
samples.json
[ { “text”:“Unable to reset password”, “category”:“Access Management”, “subcategory”:“Password Reset”, “priority”:“High” }, { “text”:“VPN connection failed”, “category”:“Network”, “subcategory”:“VPN”, “priority”:“Medium” }, { “text”:“Laptop battery issue”, “category”:“Hardware”, “subcategory”:“Battery”, “priority”:“Low” }]

Folder Structure
auto-categorization-webhook/
│
├── app.py
├── requirements.txt
├── README.md
├── prompts.md
├── ai_usage_note.md
├── samples.json
│
├── data/
│ └── sample_input.json
│
├── outputs/
│ └── sample_output.json
│
├── logs/
│ └── predictions.log
│
├── tests/
│ └── test_basic.py
│
└── src/
├── classifier.py
├── llm_helper.py
└── utils.py

Prompt Documentation
Example Prompt
You are a support ticket classification assistant.
Analyze the ticket below.
Ticket: {subject} {description}
Classify into:
Category
Subcategory
Priority
Return JSON only.
Use these examples:
{few_shot_examples}
Output Format:
{ “category”:““,”subcategory”:““,”priority”:““,”confidence”:“” }

AI Usage Note
What AI Helped With
Ticket classification
Prompt generation
JSON output generation
Code suggestions
Testing ideas
What AI Got Wrong
Sometimes predicted incorrect priorities.
Sometimes generated extra text outside JSON.
Best Prompt Used
Classify support tickets into category, subcategory, and priority using the provided examples. Return JSON only.

Test Cases
Test Case 1
Input:
Password reset issue
Expected Output:
Category = Access Management
Subcategory = Password Reset
Priority = High
Status = Pass

Test Case 2
Input:
VPN connection failed
Expected Output:
Category = Network
Subcategory = VPN
Priority = Medium
Status = Pass

Assumptions
Ticket data is in English.
LLM API is available.
Categories are predefined.
Input JSON is valid.

Limitations
Accuracy depends on examples.
Ambiguous tickets may reduce prediction quality.
New issue types require additional examples.
Internet connection required for cloud LLMs.

Future Enhancements
Auto Ticket Routing
Multi-Language Support
Dashboard Analytics
Human Feedback Loop
ServiceNow Integration
Jira Integration

Deliverables Included
✔ Public GitHub Repository
✔ README Documentation
✔ Demo Video (5–7 Minutes)
✔ AI Usage Note
✔ Sample Data Folder
✔ Test Cases
✔ Team Member Resumes (PDF)
✔ Source Code
✔ Prompt Documentation

Conclusion
The Auto Categorization Webhook is an AI-powered FastAPI solution that automatically classifies support tickets using Few-Shot Learning and Structured Output Generation. The prototype demonstrates AI Agent workflow capabilities, improves ticket management efficiency, and reduces manual effort through intelligent automation.
