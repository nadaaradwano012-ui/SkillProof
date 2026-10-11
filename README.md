SkillProof

Know your skills. Identify the gaps. Build your internship readiness.

> Project status: In development / planned implementation  
> Project type: Internship Skill Gap Matcher  
> Learning context: Digital Egypt Pioneers Initiative (DEPI) student project

SkillProof is a proposed web platform that helps students compare their current skills with the requirements of a specific internship. It identifies matched and missing skills, highlights areas that may need improvement, and turns the results into practical next steps.

> Important: This README describes the intended project scope. Features, APIs, setup commands, and integrations should only be marked as complete after they have been implemented and tested in the repository.

Table of Contents

- [Overview](#overview)
- [Problem Statement](#problem-statement)
- [Proposed Solution](#proposed-solution)
- [Target Users](#target-users)
- [Core Features](#core-features)
- [How Skill Matching Works](#how-skill-matching-works)
- [Readiness Score](#readiness-score)
- [Proposed Technology Stack](#proposed-technology-stack)
- [Proposed Architecture](#proposed-architecture)
- [Project Structure](#project-structure)
- [Getting Started](#getting-started)
- [Configuration](#configuration)
- [API Design](#api-design)
- [Testing Strategy](#testing-strategy)
- [Git and Contribution Workflow](#git-and-contribution-workflow)
- [Privacy and Responsible Use](#privacy-and-responsible-use)
- [Project Scope and Limitations](#project-scope-and-limitations)
- [Team](#team)
- [License](#license)

Overview

Students can find it difficult to determine whether they meet the requirements of an internship and what they should learn next. SkillProof is designed to make this process more transparent by connecting a student's skills and supporting evidence to the requirements of a selected internship.

The platform focuses on understandable results and practical improvement. Rather than showing only a percentage, it explains which required skills match, which are missing, and which may need further development or assessment.

Problem Statement

Students may be interested in an internship but still have questions such as:

- Which of the internship's required skills do I already have?
- Which skills are missing or need improvement?
- What should I prioritize to improve my readiness?
- How can I demonstrate my skills through projects, certificates, or assessments?
- How can I keep track of internship applications and their statuses?

 Proposed Solution

SkillProof brings these activities into one workflow:

1. Create a student profile and list current skills.
2. Add projects, certificates, or other supporting evidence.
3. Enter an internship and review its required skills.
4. Compare the student's skills with the internship requirements.
5. Review matched skills, skill gaps, and an indicative readiness score.
6. Follow a personalized roadmap with practical next steps.
7. Track internship applications and review progress over time.

Target Users

- **Students:** Manage their profiles and skills, analyze internship requirements, add evidence, assess skill gaps, follow a learning roadmap, and track applications.
- **Recruiters:** Review relevant applicant skills, evidence, and matching summaries through a basic recruiter dashboard, subject to appropriate access controls.

 Core Features

The following describes the planned scope, not a claim that every feature is already implemented.

 1. Student Profile and Skills Management

- Create and update a student profile.
- Add, edit, and remove skills.
- Record a self-reported proficiency level, such as Beginner, Intermediate, or Advanced.
- Add projects, certificates, and supporting links.
- Associate evidence with relevant skills.

 2. Internship Requirements Input

- Enter internship details and required skills manually.
- Paste a job description and review the skills identified from it, if text extraction is implemented.
- Optionally store a link to the original internship listing.
- Allow students to review and edit the requirements before running an analysis.

Manual entry must remain available. A URL should not be assumed to be readable by the application, and text extraction must not be described as AI-powered unless a real AI integration exists.

 3. Skill Matching Engine

- Compare student skills against an internship's required skills.
- Categorize requirements as **Matched**, **Missing**, **Needs Improvement**, or **Needs Assessment**, when the available information supports those categories.
- Handle capitalization and unnecessary whitespace consistently.
- Present the reasoning behind the matching results.

 4. Skill Gap Analysis and Readiness Score

- Summarize the total number of required skills and the number of matched skills.
- Display missing and underdeveloped skills separately.
- Calculate an indicative readiness score.
- Prioritize skill gaps using a documented and understandable rule.

 5. Skill Assessment and Verification

- Provide short quizzes or basic tasks for selected skills.
- Store assessment results separately from self-reported proficiency.
- Use assessment results in the analysis only according to explicit rules.
- Distinguish evidence that has been submitted from evidence that has actually been reviewed.

 6. Personalized Learning Roadmap

- Generate next steps based on identified gaps.
- Show the reason a skill was flagged and its priority.
- Suggest practical learning activities or mini-projects where appropriate.
- Let students track roadmap progress, for example Not Started, In Progress, and Completed.
- Refresh recommendations when relevant profile or analysis data changes.

 7. Projects, Certificates, and Evidence

- Add project descriptions and links, including GitHub repositories.
- Add certificate information and supporting links.
- Associate evidence with one or more skills.
- Clearly display evidence status without claiming automatic verification where no verification process exists.

 8. Internship Application Tracking

- Save internships the student is interested in.
- Track an application's status, date, notes, and source link when available.
- Filter or review applications by status.
- Keep application status separate from the skill readiness score.

Suggested statuses include Interested, Preparing, Applied, Interview, Accepted, Rejected, and Withdrawn.

 9. Basic Recruiter Dashboard

- Review internship requirements and relevant applicant profiles.
- View skills, matching summaries, assessment results when available, and supporting evidence.
- Explain why skills were classified as matched or missing.
- Restrict access to student information according to the application's agreed authorization rules.

 Optional Enhancements

These are not required for the initial minimum viable product (MVP):

- AI-assisted CV skill extraction, with user review before saving.
- Analysis of application feedback to suggest potential skill improvements.
- AI-powered mock interviews.

Optional AI functionality must not delay the core matching workflow. Any external AI integration should document its provider, configuration, privacy implications, and fallback behavior.

 How Skill Matching Works

The matching engine is the core business-logic component of SkillProof. It should be implemented separately from the UI so it can be tested and reused.

At a high level, the engine should:

1. Validate the provided student skills and internship requirements.
2. Normalize skill names for comparison, including capitalization and surrounding whitespace.
3. Search for each required skill in the student's skill list.
4. Apply the project's explicit classification rules.
5. Return separate result groups for matched, missing, underdeveloped, and assessment-needed skills, where applicable.
6. Calculate the readiness score and prioritize actionable gaps.

The initial algorithm can use arrays, objects, loops, conditions, searching, and functions. A straightforward nested-loop implementation is acceptable for the MVP and is easy to explain and test.

 Example

**Internship requirements:** HTML, CSS, JavaScript, React, Git  
**Student skills:** HTML, CSS, JavaScript, Git

Possible result:

- **Matched:** HTML, CSS, JavaScript, Git
- **Missing:** React
- **Needs Improvement:** Only skills for which the available information shows that a defined requirement is not met
- **Needs Assessment:** Only skills for which further evaluation is genuinely needed

The example is illustrative. The application should calculate results from actual input rather than hardcoding them.

 Keep Skill Statuses Separate

These are different questions and should not be combined into a single status:

- **Skill match:** Does the student's skill satisfy the internship requirement according to the configured rule?
- **Proficiency:** What level has the student reported or demonstrated?
- **Assessment:** Has the student completed an assessment, and what was its result?
- **Evidence:** Has supporting evidence been added, and has it actually been reviewed?

A skill name appearing in the student's profile does not, by itself, prove competence or verify evidence.

 Readiness Score

For the initial MVP, the proposed score is:

`Readiness Score = (Matched Required Skills / Total Required Skills) × 100`

For example, if four out of five required skills are matched, the score is 80%.

Implementation requirements:

- Recalculate the score from current analysis data.
- Handle an empty requirements list safely; do not divide by zero or show a misleading result.
- Document what counts as a matched requirement.
- Clearly label the score as an **indicative skill-coverage measure**, not a guarantee of being accepted or a complete measure of professional competence.

If the team later chooses a weighted score, the weights and calculation must be documented and understandable.

 Proposed Technology Stack

The exact implementation choices should be confirmed by the team and project supervisor before they are treated as final.

| Area | Proposed technology / approach |
|---|---|
| Frontend | React and TypeScript |
| UI | HTML and CSS; responsive reusable components |
| Backend | Node.js and Express |
| Communication | REST API |
| Data storage | Database technology to be selected and documented |
| Version control | Git and GitHub |
| Testing | Tests for matching logic, API behavior, and key user flows; tools to be confirmed |
| AI features | Optional; external provider and configuration to be decided only if needed |

Do not commit API keys, passwords, database credentials, or other secrets to the repository. Never expose private service keys in client-side code.

 Proposed Architecture

The application is intended to separate interface, business logic, and data access:

- **Frontend:** Collects user input and presents profiles, analysis results, roadmaps, and application data.
- **Backend:** Validates requests, applies business rules, and exposes API endpoints.
- **Matching service:** Handles skill normalization, searching, classification, score calculation, and gap prioritization.
- **Data layer:** Stores and retrieves profiles, skills, internships, evidence, assessments, analyses, and applications once the database decision is finalized.

The matching logic should remain testable independently of React components or the database. Until a database is selected and configured, any mock or in-memory data should be clearly treated as temporary development data rather than permanent storage.

 Project Structure

SkillProof/
├── client/
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   ├── layouts/
│   │   ├── services/
│   │   ├── hooks/
│   │   ├── types/
│   │   ├── utils/
│   │   └── styles/
│   └── package.json
├── server/
│   ├── src/
│   │   ├── routes/
│   │   ├── controllers/
│   │   ├── services/
│   │   ├── models/
│   │   ├── middleware/
│   │   └── utils/
│   └── package.json
├── docs/
│   ├── requirements.md
│   ├── architecture.md
│   ├── data-model.md
│   ├── api-documentation.md
│   ├── testing-plan.md
│   └── decisions.md
├── .env.example
├── .gitignore
└── README.md

## Getting Started

> **Setup status:** The exact installation and run commands must be verified against the project's actual `package.json` scripts before this section is treated as final.

### Prerequisites

- Git
- Node.js and npm
- A code editor, such as Visual Studio Code
- The selected database, if required by the implemented version

Check your installation:

```bash
node --version
npm --version
git --version
```

### Clone the Repository

Replace `<REPOSITORY_URL>` with the repository's actual URL:

```bash
git clone <REPOSITORY_URL>
cd SkillProof
```

### Install Dependencies

After the frontend and backend applications have been created, install dependencies in each project folder:

```bash
cd client
npm install
```

In a separate terminal:

```bash
cd server
npm install
```

### Run the Application

The following is a typical development setup, assuming the relevant `dev` scripts exist in each `package.json`:

```bash
# Terminal 1 — frontend
cd client
npm run dev
```

```bash
# Terminal 2 — backend
cd server
npm run dev
```

Use the actual scripts and ports defined by the project. If these scripts have not been configured, add and test them before publishing final setup instructions.

## Configuration

Configuration depends on the final backend, database, and optional integrations. If environment variables are needed:

1. Create a local `.env` file in the appropriate project directory.
2. Add `.env` to `.gitignore`.
3. Provide an `.env.example` containing variable names and safe placeholder values only.
4. Document where each value is used and whether it is required.

Possible examples, depending on the implementation:

```dotenv
PORT=5000
DATABASE_URL=replace_with_local_database_connection
AI_API_KEY=configure_only_if_an_ai_integration_is_enabled
```

These are illustrative names, not confirmed configuration requirements. Never use real credentials in documentation or commit them to GitHub.

## API Design

The backend is planned to expose REST endpoints. The examples below are **proposed routes**, not confirmed or implemented API contracts. Update this section as endpoints are built and tested.

| Method | Example route | Purpose |
|---|---|---|
| `GET` | `/api/students/:id` | Retrieve a student profile |
| `PUT` | `/api/students/:id` | Update a student profile |
| `GET` | `/api/students/:id/skills` | Retrieve a student's skills |
| `POST` | `/api/students/:id/skills` | Add a skill |
| `PUT` | `/api/skills/:id` | Update a skill |
| `DELETE` | `/api/skills/:id` | Remove a skill |
| `POST` | `/api/internships` | Create an internship record |
| `PUT` | `/api/internships/:id` | Update internship details |
| `POST` | `/api/match` | Run a matching analysis |
| `GET` | `/api/analyses/:id` | Retrieve a saved analysis |
| `POST` | `/api/evidence` | Add supporting evidence |
| `POST` | `/api/assessments` | Submit or create an assessment, depending on the final design |
| `GET` | `/api/students/:id/roadmap` | Retrieve roadmap items |
| `PUT` | `/api/roadmap/items/:id` | Update roadmap progress |
| `GET` | `/api/applications` | Retrieve application records |
| `POST` | `/api/applications` | Add an application record |
| `PUT` | `/api/applications/:id` | Update an application record |

For each implemented endpoint, document its method, purpose, input schema, example response, validation rules, possible errors, and access requirements. Do not describe planned endpoints as functional until they have been implemented and tested.

## Testing Strategy

Testing should cover the matching engine first, followed by the main API and user workflows.

### Matching Logic

Test at least the following cases:

- All required skills are present.
- Some or all required skills are missing.
- The student has an empty skills list.
- The internship has no required skills.
- Skill names differ only in capitalization or surrounding whitespace.
- Duplicate skill names are present.
- A skill is listed but does not meet an explicitly defined proficiency requirement.
- Evidence is absent or has not been reviewed.
- The readiness score is recalculated when input changes.

### Application Workflows

Test profile updates, internship creation, analysis display, roadmap progress updates, evidence management, assessment results, and application status changes as these features are implemented.

### API and UI

Test valid and invalid requests, missing records, appropriate error responses, form validation, empty states, loading states, and responsive layouts. Run the tests and record the actual results; do not claim that tests passed unless they were run.

## Git and Contribution Workflow

GitHub is part of the development process. Use the repository to track code, tasks, reviews, and documentation.

Recommended practices:

1. Keep `main` stable and suitable for demonstration.
2. Create a feature branch for a focused task, such as `feature/skill-matching`.
3. Make small, meaningful commits.
4. Open a Pull Request (PR) explaining what changed, why it changed, and how it was tested.
5. Review a teammate's changes before merging when practical.
6. Update documentation when behavior, setup, or API contracts change.

Example workflow:

```bash
git switch main
git pull origin main
git switch -c feature/skill-matching
```

After implementation and testing:

```bash
git add .
git commit -m "feat: implement skill matching"
git push -u origin feature/skill-matching
```

Example commit messages:

- `feat: add student skill form`
- `feat: calculate readiness score`
- `fix: handle empty internship requirements`
- `test: add matching logic test cases`
- `docs: update API documentation`

Never commit `.env` files, credentials, private tokens, or unnecessary generated files. Use a suitable `.gitignore` file.

## Privacy and Responsible Use

SkillProof should handle student information and professional evidence carefully:

- Collect only information needed by the platform.
- Restrict access to private records according to the implemented authorization rules.
- Do not expose credentials or private data in repository files, logs, or error messages.
- Make clear when information is self-reported versus assessed or reviewed.
- Do not mark evidence as verified without an actual review process.
- Explain the readiness score and its limitations.
- If an external AI service is introduced, document what data is sent and allow users to review AI-generated suggestions before saving them.

Authentication, detailed role permissions, and the database choice require a confirmed implementation decision before production use.

## Project Scope and Limitations

- SkillProof is intended to support skill development and internship preparation; it cannot guarantee an interview, internship, or job offer.
- The readiness score is an indicative measure of skill coverage, not a full measure of a person's ability.
- Self-reported skills may not accurately reflect a student's proficiency.
- Evidence is not automatically verified merely because a link or certificate is submitted.
- Job description parsing, CV analysis, feedback analysis, and AI mock interviews are optional enhancements unless explicitly approved and implemented.
- Database technology, authentication, deployment, and the final user-interface language remain decisions to be documented by the team.
- A feature should be marked complete only after its behavior has been implemented and tested.

## Team

Add confirmed team details here:

- **Team name:** To be added
- **Team members and roles:** To be added
- **Supervisor or mentor:** To be added if required

## License

A license has not yet been selected. Add a license file and update this section once the team has agreed on the terms for sharing and reuse.
