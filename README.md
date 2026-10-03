# RepoPilot

### From unfamiliar repository to actionable contribution.

RepoPilot is an open-source AI-powered developer tool that helps first-time contributors understand unfamiliar GitHub repositories and move from repository discovery to a concrete, actionable contribution.

Powered by **Gemma**, RepoPilot uses open-weight AI to analyze repository context, identify where contributors can start, and transform natural-language problems into repository-aware issue drafts.

Rather than treating repository analysis and issue generation as separate features, RepoPilot connects them into a single contributor workflow:

**Understand the repository → Identify where to start → Find a contribution opportunity → Describe a problem → Generate a repository-aware issue**

---

## ✨ What is RepoPilot?

Starting with an unfamiliar open-source repository can be difficult.

A contributor may need to understand:

* What the project does
* How the repository is structured
* Which technologies are being used
* Which files and modules matter
* Where a beginner should start
* What contribution could be suitable
* How to describe a discovered problem clearly

RepoPilot combines **repository understanding and contribution guidance** into one workflow.

The contributor provides a public GitHub repository URL. RepoPilot retrieves relevant repository context through the GitHub REST API and uses **Gemma** to turn that context into structured, contributor-focused guidance.

The same repository context is then carried into the issue workflow, allowing Gemma to generate an issue that is grounded in the repository rather than based only on the user's description.

---

## 🧭 Core Workflow

```text
                    GitHub Repository
                           │
                           ▼
                  Repository Analysis
                           │
                           ▼
                    Repository Context
                           │
                           ▼
                     Gemma Analysis
                           │
             ┌─────────────┴─────────────┐
             ▼                           ▼
      Understand Project          Find Where to Start
             │                           │
             └─────────────┬─────────────┘
                           ▼
                 Suggested Contribution
                           │
                           ▼
                   Describe a Problem
                           │
                           ▼
              Repository + Problem Context
                           │
                           ▼
                     Gemma Analysis
                           │
                           ▼
                Structured Issue Draft
                           │
                           ▼
                  Review & Contribute
```

The result is a guided contribution workflow rather than a generic AI chatbot.

---

# 🤖 Powered by Gemma

**Gemma is at the core of RepoPilot.**

RepoPilot uses **Gemma**, Google's family of open-weight AI models, through the Gemini API.

Gemma is used for the two central intelligence workflows in the application:

### 1. Repository Understanding

Gemma receives structured repository context, including information such as:

* Repository metadata
* README content
* Programming languages
* File and folder structure
* Relevant repository information

It analyzes this context to produce:

* Project overview
* Project summary
* Technology stack
* Important files
* Where to start
* Suggested contribution
* Beginner-friendly task
* Uncertainties

### 2. Repository-Aware Issue Generation

When a contributor describes a problem, RepoPilot does not send only the user's text to the model.

Instead, Gemma receives:

```text
User's Problem Description
          +
Repository Context
          +
Relevant Repository Information
          ↓
        Gemma
          ↓
Structured Issue
```

This allows RepoPilot to produce an issue draft that is connected to the repository being explored.

For example:

**User input:**

> Login button freezes when signing in from Chrome on Android.

Gemma can use the repository context to generate:

* A structured title
* Problem summary
* Reproduction steps
* Expected behavior
* Actual behavior
* Relevant repository areas
* Possible cause
* Missing information
* Suggested labels
* Acceptance criteria

---

## 🔍 Why Gemma Matters

AI is not a decorative feature in RepoPilot.

The AI component directly drives the core product workflow:

```text
Repository Context
       ↓
     Gemma
       ↓
Repository Understanding
       ↓
Contribution Guidance
       ↓
User Problem
       +
Repository Context
       ↓
     Gemma
       ↓
Repository-Aware Issue
```

Without the AI analysis, RepoPilot would not provide its central contributor guidance or repository-aware issue generation.

This makes **Gemma an integral part of the product architecture**, rather than an additional chatbot layer.

---

# 🧩 Key Features

## Repository Analysis

Provide a public GitHub repository URL and RepoPilot generates a contributor-focused overview using repository context and Gemma.

The analysis includes:

* Project overview
* One-line project summary
* Technology stack
* Important files and directories
* Areas worth exploring
* Suggested starting point
* Suggested contribution
* Beginner-friendly task
* Uncertainties and unavailable information

---

## 🎯 Contribution Guidance

RepoPilot goes beyond explaining what a repository contains.

Gemma analyzes the available repository context to identify a potential starting point for a new contributor.

A contribution recommendation includes:

**Suggested contribution**

> Improve mobile login error handling

**Difficulty**

> Beginner

**Relevant area**

```text
src/components/LoginButton.jsx
```

The contributor can then move directly into the issue workflow.

---

## 🐛 Repository-Aware Issue Generation

Contributors can describe a problem naturally.

For example:

> Login button freezes when signing in from Chrome on Android.

RepoPilot combines the problem description with repository context before sending the request to Gemma.

The resulting issue draft can contain:

* Title
* Summary
* Steps to reproduce
* Expected behavior
* Actual behavior
* Relevant repository files
* Possible cause
* Missing information
* Suggested labels
* Acceptance criteria

The generated issue is **copy-ready**, but the contributor remains responsible for reviewing it before submitting it to GitHub.

---

## 🧭 Contribution Path

RepoPilot represents the contributor journey as a clear progression:

```text
Understand Repository
        ↓
Explore Important Area
        ↓
Suggested Beginner Task
        ↓
Create Repository-Aware Issue
        ↓
Ready to Contribute
```

This is the central product experience.

RepoPilot is not intended to be another repository chatbot. It is designed to help a contributor answer:

> **"I found this project. I understand it now. What should I do next?"**

---

# 🏗️ Architecture

```text
┌──────────────────────┐
│         User         │
└──────────┬───────────┘
           │
           ▼
┌──────────────────────┐
│    React + Vite      │
│      Frontend        │
└──────────┬───────────┘
           │
           ▼
┌──────────────────────┐
│   Node.js + Express  │
│       Backend        │
└───────┬────────┬─────┘
        │        │
        ▼        ▼
┌────────────┐ ┌────────────────┐
│ GitHub API │ │  Gemini API    │
│            │ │   + Gemma      │
└──────┬─────┘ └───────┬────────┘
       │               │
       └───────┬───────┘
               ▼
      ┌──────────────────┐
      │ Repository       │
      │ Context          │
      └────────┬─────────┘
               │
               ▼
      ┌──────────────────┐
      │      Gemma       │
      │                  │
      │ Analyze context  │
      │ Generate output  │
      └────────┬─────────┘
               │
               ▼
      ┌──────────────────┐
      │ Structured JSON  │
      └────────┬─────────┘
               │
               ▼
      ┌──────────────────┐
      │    RepoPilot     │
      │        UI        │
      └──────────────────┘
```

---

# 🛠️ Technology Stack

| Layer                  | Technology      |
| ---------------------- | --------------- |
| Frontend               | React           |
| Build Tool             | Vite            |
| Backend                | Node.js         |
| API Framework          | Express         |
| Repository Integration | GitHub REST API |
| AI Model               | **Gemma**       |
| AI Platform            | Gemini API      |
| Package Manager        | npm             |
| Version Control        | Git / GitHub    |
| License                | MIT             |

---

# 🔌 API Design

The frontend communicates with focused backend endpoints and expects structured JSON responses.

## `POST /api/explain`

Analyzes a GitHub repository using repository context and Gemma.

### Request

```json
{
  "repoUrl": "https://github.com/owner/repository"
}
```

### Response

```json
{
  "project_name": "",
  "one_line_summary": "",
  "what_it_does": "",
  "tech_stack": [],
  "key_files": [],
  "where_to_start": "",
  "suggested_contribution": {
    "title": "",
    "description": "",
    "difficulty": ""
  },
  "uncertainties": []
}
```

---

## `POST /api/issue`

Generates a repository-aware issue using Gemma.

### Request

```json
{
  "repoUrl": "https://github.com/owner/repository",
  "bugDescription": "Login button freezes on mobile.",
  "repositoryContext": {}
}
```

### Response

```json
{
  "title": "",
  "summary": "",
  "steps_to_reproduce": [],
  "expected_behavior": "",
  "actual_behavior": "",
  "possible_cause": "",
  "relevant_files": [],
  "suggested_labels": [],
  "missing_information": [],
  "acceptance_criteria": []
}
```

---

# 🛡️ Responsible AI Design

RepoPilot is designed to distinguish between **repository-supported information** and **AI-generated inference**.

### No unsupported repository claims

If information cannot be determined from the available repository context, RepoPilot should explicitly communicate:

> **Not available from the provided repository context.**

### Hypotheses are clearly labeled

Potential causes generated by Gemma should not be presented as confirmed facts.

The interface identifies them as:

> **AI hypothesis — verify before reporting**

This encourages contributors to review generated information before using it in a public issue.

---

# 📦 Project Scope

RepoPilot is intentionally designed as a focused hackathon MVP.

### Included

* Public GitHub repository analysis
* Repository metadata and context retrieval
* Gemma-powered repository understanding
* Contributor starting-point guidance
* Suggested contribution direction
* Gemma-powered issue generation
* Structured issue preview
* Missing-information detection
* Copy-ready issue output
* Contribution Path

### Out of Scope

The MVP does not include:

* User authentication
* GitHub OAuth
* Persistent user accounts
* Database infrastructure
* Vector databases
* Complex RAG pipelines
* Autonomous coding
* Automatic code modification
* Automatic GitHub issue creation
* Payments
* Social features

The focus is on demonstrating the core contributor workflow clearly and reliably.

---

# 🚀 Getting Started

## Prerequisites

* Node.js
* npm
* Git
* Gemini API key

## Clone

```bash
git clone <repository-url>
cd RepoPilot
```

## Install Dependencies

```bash
npm install
```

## Configure Environment Variables

Create a `.env` file:

```env
GEMINI_API_KEY=your_api_key_here
```

Never commit API keys or other secrets to the repository.

## Run Locally

```bash
npm run dev
```

Refer to the available npm scripts for the frontend and backend development commands.

---

# 📁 Project Structure

```text
RepoPilot/
├── client/
│   └── src/
│       ├── components/
│       ├── pages/
│       ├── services/
│       └── data/
│
├── server/
│   ├── routes/
│   ├── services/
│   └── index.js
│
├── .env.example
├── package.json
├── LICENSE
└── README.md
```

Frontend components, API services, and development mock data should remain separated to keep the application easy to maintain and connect to the backend.

---

# 💡 Why RepoPilot?

The challenge for a first-time contributor is rarely just:

> **"What does this repository do?"**

The more important question is:

> **"I understand the project. What can I actually contribute?"**

RepoPilot is designed around this transition.

By combining **GitHub repository context + Gemma-powered analysis + contribution guidance + repository-aware issue generation**, RepoPilot helps turn an unfamiliar codebase into a clearer path toward contribution.

---

# 🏆 Hacktoberfest Hack Day 2026

RepoPilot is being developed for:

**Hacktoberfest Hack Day 2026 — Hyderabad**

**React Hyderabad × MLH × DEV**

### Challenge

**Best Open-Source AI Project**

RepoPilot uses **Gemma**, an open-weight AI model, as a central component of its application workflow.

Gemma powers repository understanding, contribution guidance, and repository-aware issue generation.

---

# 📜 License

RepoPilot is released under the **MIT License**.

See [`LICENSE`](LICENSE) for the complete license text.

---

# 👥 Team

Built by a team Triple-Spark for Hacktoberfest Hack Day 2026.
Built by:
1. Safura Nishat
2. Nazia Sultana
3. Aditi Jaiswal

---

# 🤝 Contributing

Contributions and feedback are welcome.

If you discover a bug, have a feature suggestion, or would like to improve RepoPilot, open an issue or submit a pull request.

Please review the project's contribution guidelines before submitting changes, if available.

---

<p align="center">
  <strong>RepoPilot</strong><br>
  From unfamiliar repository to actionable contribution.
</p>
