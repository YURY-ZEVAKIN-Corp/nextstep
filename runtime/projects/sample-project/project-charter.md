# Project Charter

## Metadata

- Project Key: `SAMPLE`
- Project Name: `TaskFlow — Collaborative Task Management App`
- Owner: `Product Manager`
- Status: `Active`
- Start Date: `2026-06-01`
- Target Outcome: `MVP with user authentication, task CRUD, and real-time board`
- Sprint Cadence: `Biweekly`
- Sprint Length: `2 weeks`

## Purpose

Build a lightweight, real-time collaborative task management application that allows small teams to create, assign, and track tasks across a shared board. TaskFlow targets teams that find existing tools (Jira, Trello) too heavy for their workflow.

## Success Measures

- Measure 1: Users can sign up, log in, and manage their profile within 2 sprints
- Measure 2: Core task CRUD operations are functional with real-time board updates
- Measure 3: Application achieves 99% uptime during beta with <500ms API response times

## Scope

- User authentication (email/password, JWT-based sessions)
- Task CRUD with assignee, status, priority, due date
- Real-time collaborative board (WebSocket-based)
- RESTful API with Express + PostgreSQL
- React (Vite) frontend with responsive design
- Docker-based local development and CI/CD via GitHub Actions

## Out of Scope

- Mobile native apps (PWA only)
- Offline mode
- Third-party integrations (Slack, GitHub)
- SSO / OAuth providers
- Advanced reporting and analytics

## Key Stakeholders

- Product Manager — backlog prioritisation and value validation
- Solution Architect — technology decisions and system design
- Tech Lead — implementation oversight and code quality
- QA Engineer — test planning and release validation
- DevOps Engineer — CI/CD pipeline and infrastructure

## Dependencies

- Docker and Docker Compose for local development environment
- GitHub Actions for CI/CD pipeline
- Node.js 20+ and PostgreSQL 16+ availability
- Team familiarity with React, Express, and relational databases

## Risks

- Risk 1: Team unfamiliarity with WebSocket-based real-time sync — Mitigation: Spike in sprint 1, pair programming
- Risk 2: JWT secret management in CI/CD — Mitigation: Use GitHub Secrets + environment variable injection
- Risk 3: Scope creep on MVP features — Mitigation: Strict backlog triage via Product Manager

## Technology Governance

- Technology stack file: `technology-stack.md`
- Initial stack decisions required: React/Vite, Express.js, PostgreSQL, JWT auth, Docker, GitHub Actions
