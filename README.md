# AI-Powered Event Triage Pipeline

🚀 A cloud-native, AI-powered event triage pipeline built with **GitHub Actions** and **Hugging Face Inference API**.

This project demonstrates how incoming events can be automatically classified using a transformer-based AI model (**DistilBERT**) and then routed with a confidence score — without any manual triage.

Although this demo uses **GitHub Issues** as the event source, the same pattern applies directly to real enterprise systems such as:

- **Dynamics 365 support cases**
- **SAP IDOCs**
- **Azure Service Bus messages**
- **integration failures**
- **operational alerts**
- **incident/event queues**

---

## 📌 Overview

In many enterprise systems, incoming events are still routed manually or through brittle keyword-based rules.

This project shows how to introduce a lightweight AI classification layer into the event-processing flow:

> **Incoming event → AI classification → routing/comment/output**

The result is a simple but powerful architecture pattern for intelligent triage and automation.

---

## 🧠 What This Project Does

Whenever a new GitHub issue is created:

1. A **GitHub Actions workflow** is triggered
2. The issue title is sent to a **Hugging Face transformer model**
3. The model performs **sentiment classification**
4. The workflow extracts:
   - **label** (`POSITIVE` / `NEGATIVE`)
   - **confidence score**
5. The workflow posts an automated triage comment on the issue

### Example Output

- 🔴 **Sentiment:** NEGATIVE | **Confidence:** 99.2%
- 🟢 **Sentiment:** POSITIVE | **Confidence:** 99.8%

---

## 🏗️ Architecture

```text
GitHub Issue Opened
        ↓
GitHub Actions Workflow Triggered
        ↓
Hugging Face Inference API (DistilBERT)
        ↓
Sentiment Classification Result
        ↓
Automated Triage Comment Posted Back to GitHub