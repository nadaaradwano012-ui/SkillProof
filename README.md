# SkillProof 

> **Know your skills. Identify the gaps. Build your internship readiness.**

SkillProof is a frontend-first internship skill gap matching web application developed by the **SkillProof Team** as part of the **DEPI React Front-End track**.

The platform helps university students organize their skills and supporting work, compare their skills with internship requirements, identify skill gaps, follow a learning roadmap, and track internship applications. It also provides restricted views for recruiters and company administrators to review applications and manage the hiring process.

## Table of Contents

- [Project Overview](#project-overview)
- [Problem Statement](#problem-statement)
- [Project Objectives](#project-objectives)
- [User Roles](#user-roles)
- [Core User Journey](#core-user-journey)
- [MVP Scope](#mvp-scope)
- [Excluded from the First MVP](#excluded-from-the-first-mvp)
- [Skill Matching Logic](#skill-matching-logic)
- [Application and Roadmap Statuses](#application-and-roadmap-statuses)
- [Confirmed Technology](#confirmed-technology)
- [Current Project Status](#current-project-status)
- [Team and Responsibilities](#team-and-responsibilities)
- [Official Milestones](#official-milestones)
- [Project Documentation](#project-documentation)
- [Proposed Project Structure](#proposed-project-structure)
- [Development Workflow](#development-workflow)
- [Quality Rules](#quality-rules)
- [Running the Project](#running-the-project)
- [Known Limitations](#known-limitations)
- [Instructor and Program](#instructor-and-program)
- [License](#license)

## Project Overview

SkillProof is a web-based platform that compares the skills listed in a student's profile with the required skills of an internship.

The system returns:

- Matched required skills.
- Missing required skills.
- An explainable Skill Coverage score.
- Learning roadmap actions based on identified gaps.
- Application status information.

SkillProof does not claim that a student has mastered a skill, guarantee internship acceptance, or make automatic hiring decisions.

## Problem Statement

Students may find it difficult to determine how well their current skills match an internship opportunity. Skills, projects, certificates, and supporting links may also be distributed across different places without a clear view of the student's readiness.

Companies and recruiters need an organized view of relevant applicant information, but access must remain limited to appropriate data and actions.

SkillProof addresses this problem by providing a clear, rule-based skill comparison and a connected workflow for students, recruiters, and companies.

## Project Objectives

- Help students build and maintain an organized skill profile.
- Compare student skills with internship-required skills using clear rules.
- Identify matched and missing required skills.
- Calculate a transparent Skill Coverage score.
- Convert missing skills into manageable learning roadmap items.
- Allow students to track internship applications.
- Allow recruiters to review applications and update hiring stages.
- Allow company administrators to manage internships and recruiters.
- Deliver a readable and maintainable React frontend that the team can explain and extend.

## User Roles

### Student

A student can:

- Create and edit a profile.
- Add, edit, search, and remove skills.
- Add projects, certificates, and supporting links.
- Browse internship opportunities.
- View internship details and required skills.
- Run the Skill Gap Matcher.
- View matched and missing skills.
- View the Skill Coverage calculation.
- Add missing skills to a learning roadmap.
- Update roadmap progress.
- Add or submit internship applications.
- Track application status.

### Recruiter

A recruiter can:

- View authorized company internships.
- View applicants for permitted internships.
- Review relevant candidate information.
- View Skill Coverage as supporting information.
- Review projects and supporting evidence shared with an application.
- Add private internal notes.
- Update application status.

A recruiter cannot edit student profile data or use Skill Coverage as an automatic hiring decision.

### Company Admin

A company administrator can:

- Manage the company profile.
- Create, edit, save, publish, and close internships.
- Define required and preferred skills.
- View company applicants and hiring stages.
- Invite and manage recruiters.
- Deactivate recruiters while preserving existing application history.

## Core User Journey

1. A student creates a profile.
2. The student adds current skills, projects, certificates, and supporting links.
3. A company creates an internship and defines its required skills.
4. The student selects the internship and runs the Skill Gap Matcher.
5. SkillProof normalizes and compares the skill lists.
6. The system displays matched skills, missing skills, and Skill Coverage.
7. The student adds relevant missing skills to the learning roadmap.
8. The student applies for or logs an internship application.
9. A recruiter reviews the application and updates its status.
10. The company administrator monitors internships, recruiters, applicants, and hiring stages.

## MVP Scope

The first MVP includes:

- Public landing page.
- Student and company registration interfaces.
- Recruiter invitation acceptance interface.
- Frontend role-based sign-in flow.
- Student, Recruiter, and Company Admin workspaces.
- Student profile management.
- Skills management with duplicate validation.
- Projects, certificates, and supporting evidence.
- Internship browsing and details.
- Internship creation and management.
- Required and preferred skill entry.
- Skill matching with Matched and Missing results.
- Explainable Skill Coverage calculation.
- Learning roadmap and progress tracking.
- Application tracking.
- Recruiter applicant review.
- Recruiter hiring pipeline.
- Company recruiter management.
- Loading, empty, validation, success, error, and confirmation states where relevant.

## Excluded from the First MVP

The following features are not part of the first MVP:

- Assessments or knowledge tests.
- AI-based CV extraction.
- AI-based job-description extraction.
- Automatic evidence or code verification.
- University SSO or transcript integration.
- Candidate ranking.
- Employer acceptance thresholds.
- Automatic hiring or rejection decisions.
- Advanced company analytics.
- Direct messaging.
- Production backend guarantees.
- Production database guarantees.
- Real authentication guarantees.

These features may only be considered later after the main workflow is complete and the team approves the required scope, prerequisites, and integration cost.

## Skill Matching Logic

### Inputs

- Student skills.
- Internship-required skills.

### Process

1. Validate the inputs.
2. Remove surrounding whitespace from skill names.
3. Compare skill names without case differences.
4. Remove normalized duplicates.
5. Search for every required skill in the student's skills.
6. Classify each required skill as Matched or Missing.
7. Calculate Skill Coverage when at least one required skill exists.
8. Return the result independently from the React user interface.

### Formula

```text
Skill Coverage = (Matched Required Skills / Total Required Skills) x 100
```

### Example

```text
Required Skills: HTML, CSS, JavaScript, React, Git
Student Skills:  HTML, CSS, JavaScript, Git

Matched Skills:  HTML, CSS, JavaScript, Git
Missing Skills:  React

Skill Coverage:  (4 / 5) x 100 = 80%
```

If no required skills are provided, the system returns no score instead of dividing by zero or displaying a misleading `0%`.

> Skill Coverage measures required-skill coverage only. It does not guarantee internship acceptance or prove skill mastery.

### Important Separation of Data

The following information must remain separate:

- Skills listed by the student.
- Self-reported proficiency.
- Assessment results, if implemented in a future version.
- Submitted evidence.
- Reviewed evidence.

Projects, certificates, and supporting links do not automatically change the current Skill Coverage score.

## Application and Roadmap Statuses

### Application Statuses

- Applied
- Under Review
- Interview
- Accepted
- Rejected

A student should not create more than one active application for the same internship.

Closing an internship prevents new applications but does not delete existing applications or their history.

### Roadmap Statuses

- Not Started
- In Progress
- Completed

Roadmap completion is calculated using completed items only:

```text
Roadmap Completion = (Completed Items / Total Roadmap Items) x 100
```

## Confirmed Technology

- **Frontend:** React
- **Programming Language:** JavaScript
- **Styling:** CSS
- **Version Control:** Git and GitHub
- **Development Tool:** Visual Studio Code

The following decisions are not finalized:

- Routing library.
- Shared state approach.
- Backend and API implementation.
- Database.
- Real authentication and authorization.
- Persistent storage.
- Automated testing framework.
- Deployment platform.

The team will use the simplest suitable solution after the relevant concepts and current repository structure are reviewed.

## Current Project Status

SkillProof is currently in the planning and requirements stage.

The first frontend version may use clearly labeled mock data and mock role access. Mock data must not be presented as permanent database storage, and frontend route hiding must not be described as real authorization.

The current repository may not yet contain the final React project structure, dependencies, or run scripts. This README must be updated as implementation decisions are confirmed.

## Team and Responsibilities

### 1. Nada Adnan Radwan

**Role:** Team Lead - Core Logic and Integration

Responsibilities:

- Project coordination.
- GitHub workflow and pull-request coordination.
- Shared frontend structure.
- Mock role access and integration.
- Shared data shapes and mock data coordination.
- Matching contract and integration.
- Repository integration and conflict coordination.
- README and final documentation compilation.

### 2. Reham Ali Ashour

**Role:** Student Profile, Skills, and Evidence

Responsibilities:

- Student Profile.
- Skills CRUD operations.
- Duplicate-skill validation.
- Projects and certificates.
- Supporting evidence links.
- Profile visibility settings.
- Related forms, validation, and UI states.

### 3. Alaa Ali Mohamed

**Role:** Skill Matching and Analysis

Responsibilities:

- Skill Gap Matcher interface.
- Matched and Missing analysis rules.
- Skill Coverage explanation.
- Matching edge cases.
- Matching test cases.
- Transfer of missing skills to the learning roadmap.

### 4. Habiba Ehab Anwar

**Role:** Learning Roadmap and Application Tracking

Responsibilities:

- Learning Roadmap.
- Priority and progress states.
- Custom roadmap items.
- Application Tracker.
- Student application details.
- Basic interview information and related states.

### 5. Sara Ahmed Mohamed

**Role:** Company and Recruiter Experience

Responsibilities:

- Company Profile.
- Internship management.
- Required and preferred skill entry.
- Recruiter Dashboard.
- Applicant views.
- Hiring pipeline.
- Recruiter invitation and deactivation flows.

### Shared Responsibilities

All team members contribute to:

- Responsive design.
- Accessibility.
- Loading, empty, validation, success, and error states.
- Manual testing.
- Pull-request review.
- Integration support.
- Documentation of owned features.
- Final presentation preparation.

## Official Milestones

- **16 October 2026:** Planning, literature review, and requirements.
- **6 November 2026:** System analysis and design.
- **30 November 2026:** Implementation and working application.
- **4 December 2026:** Final testing, reports, and presentation.

Detailed internal work dates are proposed team targets and may be adjusted without changing the official milestones.

## Project Documentation

The planned repository documentation includes:

```text
docs/
├── SkillProof_Project_Planning_and_Management.pdf
└── SkillProof_Requirements_Gathering.pdf
```

The documents cover:

- Project proposal and scope.
- Project plan and proposed internal timeline.
- Team responsibilities.
- Risk assessment and mitigation.
- Proposed KPIs.
- Stakeholder analysis.
- User stories.
- Use cases.
- Functional requirements.
- Non-functional requirements.
- Business rules.
- Matching acceptance cases.

## Proposed Project Structure

The following structure is a proposal for the React implementation. It is not a claim about the repository's current contents.

```text
SkillProof/
├── public/
├── src/
│   ├── components/
│   ├── pages/
│   │   ├── public/
│   │   ├── student/
│   │   ├── recruiter/
│   │   └── company/
│   ├── data/
│   ├── logic/
│   ├── styles/
│   ├── App.jsx
│   └── main.jsx
├── docs/
├── README.md
└── package.json
```

The structure must be updated after the React project is initialized and the team confirms the routing and shared-state approach.

## Development Workflow

1. Create a focused feature branch.
2. Implement one clear task.
3. Verify the feature manually.
4. Check the browser console for errors.
5. Open a pull request with a clear description.
6. Add screenshots for interface changes.
7. Add practical verification steps.
8. Request review for shared or integration-sensitive changes.
9. Resolve conflicts with the affected feature owner.
10. Merge only when the agreed core flow remains functional.

Example branch names:

```text
feature/student-profile
feature/student-skills
feature/skill-matcher
feature/learning-roadmap
feature/application-tracker
feature/company-internships
feature/recruiter-applicants
fix/duplicate-skill-validation
```

Example commit messages:

```text
feat: add student skill form
feat: calculate matched and missing skills
fix: prevent duplicate normalized skill names
style: improve mobile internship cards
docs: update MVP scope in README
```

## Quality Rules

- Do not hard-code displayed Skill Coverage results.
- Do not divide by zero when required skills are empty.
- Normalize skill casing and surrounding whitespace.
- Do not count normalized duplicates more than once.
- Keep matching logic independent from React UI components.
- Keep evidence separate from the current score.
- Do not automatically add a roadmap skill to the student's current skills.
- Do not allow multiple active applications for the same student and internship.
- Do not delete existing applications when an internship is closed.
- Confirm destructive actions before completing them.
- Include relevant loading, empty, validation, success, and error states.
- Preserve entered form values after recoverable errors when possible.
- Do not claim that tests pass unless they were actually run.
- Do not describe mock data as permanent storage.
- Do not describe frontend role views as secure authorization.
- Keep documentation aligned with the real implementation and its limitations.

## Running the Project

The exact setup commands cannot be confirmed until the React project is initialized and `package.json` is available.

After setup is confirmed, this section should include the real commands used by the repository, for example:

```bash
npm install
npm run dev
```

The example commands above must not be treated as verified repository commands until they have been tested successfully with the actual project files.

## Known Limitations

- Backend services are not confirmed.
- Persistent database storage is not confirmed.
- Real authentication is not confirmed.
- Frontend role views do not provide real access control by themselves.
- Mock data may be used during initial frontend development.
- Assessments are excluded from the first MVP.
- Evidence is not automatically verified.
- Skill Coverage does not measure mastery or guarantee acceptance.
- AI features are optional future enhancements and are not dependencies of the core workflow.

## Instructor and Program

- **Program:** DEPI
- **Track:** React Front-End
- **Instructor:** Mohamed Amr
- **Team:** SkillProof 
- **Repository:** <https://github.com/nadaaradwano012-ui/SkillProof.git>

## License

No license has been confirmed yet.
