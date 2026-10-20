# Customer Support Codebasics AI Agent — Learner Experience Email Support

An AI-powered, no-code customer support agent built with **Zapier AI Agents** to help the Codebasics Learner Experience Team handle learner email inquiries efficiently.

The agent searches official bootcamp brochures, drafts responses when the available evidence is sufficiently strong, and escalates unanswered questions to a human team member through WhatsApp.

## Project Overview

**Objective:** Reduce repetitive support work while ensuring responses remain grounded in official documentation.

**Platform:** Zapier AI Agents

**Integrations:**
- Gmail — Detect incoming emails and create reply drafts
- Google Drive — Provide bootcamp brochures as knowledge sources
- WhatsApp Notifications — Alert the support team when manual attention is needed

**Knowledge Sources:**
- `DS_Bootcamp_brochure_pdf.pdf`
- `DA_Bootcamp_brochure_pdf.pdf`

## Workflow Architecture

```text
Incoming Email (Gmail)
          |
          v
   Determine Intent
          |
          v
 Search Official Brochures
    (Google Drive)
          |
          v
 Evaluate Answer & Assign
 Confidence Score (0–10)
          |
          v
     Decision Point
       /       \
 Score >= 7   Score < 7
     |            |
     v            v
 Create Gmail   Notify Team
 Draft Reply    via WhatsApp
     |            |
     v            v
 Human Review   Manual Handling
```

## How It Works

### 1. Email Intent Detection
The agent analyzes incoming email content to determine whether the message contains a learner or customer question.

### 2. Knowledge Retrieval
The agent searches the Data Science and Data Analytics bootcamp brochures stored in Google Drive.

**Grounding rule:** Answers must be explicitly supported by the available documents. The agent must not invent details, make assumptions, or guess when information is missing.

### 3. Response Generation
When a relevant answer is found, the agent prepares a professional email draft following Codebasics communication guidelines:
- Warm, humble, learner-first, and professional tone
- Simple language and concise paragraphs
- Direct answers to the learner's question
- Consistent email signature and contact details

### 4. Confidence-Based Routing

| Confidence Score | Decision | Action |
|---|---|---|
| 9–10 | Strong evidence | Create Gmail draft |
| 7–8 | Good evidence | Create Gmail draft |
| 6 | Manual review required | WhatsApp escalation |
| 0–5 | Insufficient evidence | WhatsApp escalation |

The operational threshold is **7/10**.

### 5. Human-in-the-Loop Review
- **High confidence:** A reply draft is created in Gmail for human review.
- **Low confidence:** The agent sends a WhatsApp notification containing the required manual-attention message.
- **No automatic sending:** Customer-facing emails are not sent automatically.

## Demonstration & Test Results

### Test Case 1: Refund Policy Inquiry

**Question:** What is the refund policy for the DS and AI Bootcamp?

- Knowledge retrieval: Relevant refund information found in the brochures
- Confidence score: **9/10**
- Action: Gmail reply draft created successfully
- Outcome: A human can review the response before sending

  <img width="1572" height="757" alt="Automation" src="https://github.com/user-attachments/assets/8a5418c7-a50f-4f13-aa57-51d238edaf8d" />


### Test Case 2: Data Engineering Bootcamp Launch Date

**Question:** When will the Data Engineering Bootcamp launch?

- Knowledge retrieval: No explicit launch date found in the available brochures
- Confidence score: **4/10**
- Action: WhatsApp notification sent successfully after an initial action failure
- Outcome: The inquiry was flagged for manual handling rather than receiving an unsupported answer

  <img width="557" height="182" alt="Enquiry" src="https://github.com/user-attachments/assets/ea14a4fa-314d-4cc4-8e73-9d819d2bb3dc" />
  <img width="400" height="780" alt="Work Alert Generated" src="https://github.com/user-attachments/assets/0217c738-ee7c-4125-98d5-54ef37d3ab07" />


## Key Features

- No-code AI agent development
- Document-grounded question answering
- Confidence-based decision routing
- Automated Gmail draft creation
- WhatsApp escalation for unanswered questions
- Human-in-the-loop review
- Reduced risk of unsupported customer-facing answers

## Technology Stack

- Zapier AI Agents
- Gmail
- Google Drive
- WhatsApp Notifications
- Large Language Models (LLMs)
- Retrieval-augmented, document-grounded response generation

*Note: The workflow uses Zapier's built-in agent and knowledge-source capabilities. It does not implement a custom RAG pipeline or custom-trained language model.*

## Limitations & Future Improvements

- The agent's confidence score is an LLM-generated assessment, not a calibrated probability of correctness.
- Answer quality depends on the accuracy and completeness of the source documents.
- WhatsApp integration failures require monitoring and retry handling.
- Future improvements could include broader knowledge coverage, structured evaluation across more test cases, and escalation logging.

## Project Status

**Demonstration completed:** Both high-confidence drafting and low-confidence human escalation were tested successfully.
<img width="1405" height="866" alt="Agents Dashboard" src="https://github.com/user-attachments/assets/21edb179-c8b4-43f3-acdf-301efe27702a" />
<img width="1917" height="862" alt="Zapier Dashboard" src="https://github.com/user-attachments/assets/525e3795-44bc-4546-b7f2-d02dcc745a9b" />
<img width="912" height="522" alt="Tools Connected" src="https://github.com/user-attachments/assets/bf313506-9057-4240-9424-40c299f5e2db" />
<img width="935" height="762" alt="Instruction Prompt" src="https://github.com/user-attachments/assets/94f04168-75ce-46ae-bd89-a5bfd5097f11" />


## Disclaimer

This project demonstrates an AI-assisted customer support workflow using Codebasics-related brochure content. It is a portfolio project and is not an official Codebasics product.

