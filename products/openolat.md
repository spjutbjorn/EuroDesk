# OpenOlat

**Category:** Learning Management System (LMS)
**Type:** Self-hosted or managed
**Jurisdiction:** Switzerland (adequacy-approved)
**Website:** [openolat.com](https://www.openolat.com)

## What It Is

OpenOlat is an open-source learning management system for online courses, training programs, assessments, classrooms, and blended learning. It is a strong fit for universities, training providers, and internal L&D teams that need a European LMS with the option to self-host.

## Hosting Options

| Option | Description |
|---|---|
| **Self-hosted** | Run OpenOlat on your own EU or Swiss-hosted infrastructure |
| **Managed by OpenOlat partner** | Use a hosted deployment from an EU or Swiss operator |

## Good Fit For

- Universities and higher education
- Internal corporate training
- Certification programs and assessments
- Course portals and learner administration

## Self-Hosted Setup

### Requirements
- Linux server
- Java runtime
- Tomcat
- PostgreSQL or MariaDB

### Install

```bash
wget https://www.openolat.com/releases/openolat-latest.war
sudo mv openolat-latest.war /var/lib/tomcat10/webapps/openolat.war
sudo systemctl restart tomcat10
```

### Database

```bash
sudo -u postgres createuser openolat
sudo -u postgres createdb openolat
```

## Key Features

- Course and curriculum management
- Quizzes, assessments, and grading
- Groups, classrooms, and collaboration spaces
- Roles and permissions for learners and staff
- Self-hosted and managed deployment options

## Compliance Notes

- Prefer EU- or Swiss-hosted deployment for learner and assessment data.
- Integrate with SSO to centralize account lifecycle and access control.
- Define retention policies for course records, exams, and uploaded learner content.

## Trade-offs

- More structured and education-focused than lightweight webinar platforms
- Requires application administration and upgrade planning if self-hosted
- Best results come from aligning course design and user provisioning

## EuroDesk Verdict

OpenOlat fills a clear gap for education, universities, and internal training teams that need a sovereign European LMS instead of relying on US education platforms.
