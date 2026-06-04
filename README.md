# AI Sales Assistant for Lead Qualification & Follow-up

An automated sales lead qualification system built with **n8n**, **Telegram Bot**, **Google Sheets**, and **Email Notifications**.

This workflow helps businesses qualify potential customers automatically through a structured 10-question conversation, calculate a lead score, save qualified leads to Google Sheets, and notify the sales team by email.

---

## Project Overview

Many businesses receive customer messages from different channels but waste time manually checking whether each customer is serious, ready to buy, or just asking general questions.

This project solves that problem by creating an automated sales assistant that:

* Starts a qualification flow when the customer sends `hi`
* Asks 10 fixed lead qualification questions
* Gives each question 3 clear answer options
* Calculates the lead score automatically
* Saves qualified leads to Google Sheets
* Sends an email notification to the sales team
* Sends a professional reply to the customer

---

## How It Works

The customer starts the conversation by sending:

```text
hi
```

The bot then asks 10 questions, one question at a time.

Each question has 3 fixed choices:

```text
1 = Low intent / 0%
2 = Medium intent / 50%
3 = High intent / 100%
```

After the customer answers all 10 questions, the system calculates the final lead score.

---

## Lead Qualification Logic

| Lead Score    | Status                       | Action                                                      |
| ------------- | ---------------------------- | ----------------------------------------------------------- |
| 70% or higher | Qualified Lead               | Save to Google Sheets, notify sales team, reply to customer |
| Less than 70% | Not Qualified / Needs Review | Send a polite reply without showing the score               |

The lead score is used internally by the automation system.
The customer does not see the percentage score.

---

## Workflow Architecture

```text
Telegram Trigger
      ↓
Code Node
      ↓
IF Node
   ├── True: Qualified Lead
   │       ↓
   │   Google Sheets
   │       ↓
   │   Send Email to Sales Team
   │       ↓
   │   Telegram Reply to Customer
   │
   └── False: Not Qualified
           ↓
       Telegram Reply to Customer
```

---

## Features

* Telegram bot lead intake
* Step-by-step qualification conversation
* 10 fixed qualification questions
* 3 fixed choices per question
* Automatic lead scoring
* Qualified lead filtering
* Google Sheets lead documentation
* Email notification for the sales team
* Professional customer replies
* No manual lead checking required

---

## Tools Used

* **n8n** – Workflow automation
* **Telegram Bot** – Customer communication channel
* **Google Sheets** – Lead documentation
* **Email / Gmail** – Sales team notification
* **JavaScript Code Node** – Lead scoring and conversation logic

---

## Google Sheets Columns

The workflow saves qualified leads using the following columns:

```text
Date
Name
Username
Source
Customer Message
Need
Buying Intent
Budget
Timeline
Lead Score
AI Summary
Documentation Sent
```

---

## Customer Journey

1. Customer sends `hi`
2. Bot starts the 10-question qualification flow
3. Customer answers each question with `1`, `2`, or `3`
4. System calculates the lead score
5. If the lead score is 70% or higher:

   * Lead is saved to Google Sheets
   * Sales team receives an email
   * Customer receives a professional confirmation message
6. If the lead score is below 70%:

   * Customer receives a polite message
   * Lead is not sent to the sales team

---

## Example Customer Reply for Qualified Leads

```text
Thank you. Your request has been received successfully.

A member of our sales team will contact you within the next 24 hours to discuss your requirements and the next steps.
```

---

## Example Customer Reply for Non-Qualified Leads

```text
Thank you for your answers.

Our team will review your request and get back to you if your requirements match our service.
```

---

## Setup Instructions

1. Import the workflow JSON file into n8n.
2. Create a Telegram bot using BotFather.
3. Add the Telegram bot credentials inside n8n.
4. Create a Google Sheet for qualified leads.
5. Connect Google Sheets credentials in n8n.
6. Connect Gmail or email credentials.
7. Update the Google Sheets node with your sheet.
8. Update the Email node with your sales email address.
9. Activate the workflow.
10. Send `hi` to the Telegram bot to test the system.

---

## Repository Files

```text
README.md
workflow.json
.gitignore
```

---

## Security Notes

This repository does not include:

* Telegram bot tokens
* API keys
* Google credentials
* Email passwords
* n8n credentials

All credentials must be configured securely inside n8n.

Never upload secrets, tokens, passwords, or private credentials to GitHub.

---

## Use Cases

This workflow can be adapted for:

* Real estate agencies
* Digital marketing agencies
* SaaS companies
* Online course businesses
* Clinics and appointment-based businesses
* Service providers
* E-commerce customer support
* Sales teams that receive many repetitive leads

---

## Why This Project Matters

Sales teams often waste time responding to unqualified leads or manually collecting customer information.

This automation helps businesses:

* Save time
* Respond faster
* Identify serious customers
* Reduce manual work
* Improve sales follow-up
* Keep qualified leads organized

---

## Future Improvements

Possible future upgrades:

* Add WhatsApp integration
* Add Facebook Lead Ads integration
* Add CRM integration such as HubSpot or Salesforce
* Add AI-generated lead summaries
* Add automatic follow-up emails
* Add lead status tracking
* Add dashboard analytics

---

## Project Status

Completed MVP.

The current version includes:

* Telegram qualification flow
* Fixed 10-question scoring system
* Google Sheets documentation
* Email notification
* Customer response automation

---

## Author

Built by **Mohamed Soliman** as an AI automation portfolio project.
