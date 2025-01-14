# lead-data-eng-exercise

Take-home Exercise for the Lead Data Engineer technical interview

## Objectives

This exercise will test your ability to work with real-world data problems, design an API for data delivery, and analyze and communicate findings. It emphasizes data transformation, troubleshooting, and thoughtful problem-solving.

## Part 1: Data Analysis

You are provided with a SQLite database containing a `project_status_history` table that tracks the status of research projects over time. The table includes:

- `project_id`
- `status`
- `timestamp`

**Tasks:**

1. Use SQL or Python (Pandas) to:
    - Calculate the time spent by each project in each status.
    - Identify projects that exceeded 30 days in any single status.
2. Write a brief summary of your findings and any potential implications for project management. Include charts, figures, and other data visualizations. Can be a interactive dashboard or static report.h

## Part 2: Data Delivery

You are provided with a SQLite database containing several tables related to research personnel and funding:

- `personnel`: Employee information, including department and role.
- `funding_projects`: Project details, including funding amounts and assigned personnel.
- `departments`: Metadata about university departments.
- Data quality issues include:
    - Personnel assignments with missing department IDs.
    - Projects with duplicate entries for funding amounts.

**Tasks:**

1. Design and create a Python API to serve the following data:
    - Total funding per department, summarized over the past year.
    - A list of projects with their assigned personnel, filling in missing department names where possible.
    - Any projects with duplicate funding entries flagged for review.
2. Consider edge cases like:
    - Departments without funding.
    - Personnel without assignments.
3. Document your API endpoints and explain how the data is processed before delivery.

## Part 3: Communication & Collaboration

Completed live with the RAIS team
After reviewing Part 1 and Part 2, we provide the candidate with additional requirements and ask them to walk through how they would update the design or implementation.

This will test their ability to communicate and collaborate with us. We aren't asking them to complete the task, just walk us through their approach.
