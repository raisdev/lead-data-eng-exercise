# RAIS Lead Data Engineer Technical Exercise

## About

This exercise will test your ability to work with real-world data problems. It emphasizes data engineering and backend web development skills.

Your goal is to design and build an ETL and API for a "Personnel Dashboard" for Project Managers. The dashboard will list the personnel assigned to each project that the user manages. Each personnel record will include additional metadata about the employee, like current earnings and position title.

## Instructions

Complete the task described below using Python. You are welcome to use any tools, frameworks, or packages of your choice. You can also use Docker and SQL.

To evaluate your submission, we should be able to run your ETL and make HTTP requests against your API. We will review your submission for correctness, quality, and performance.

A write-up of your solution (ex: `README.md`) should be included with your submission. The write-up should include instructions for setting up, running, and testing the submission. The write-up should also highlight the engineering decisions you made throughout the exercise.

To submit, please package your source code into a `.zip` and send to the contact that forwarded you to this exercise. Please do not post your submissions online (ex: Github, Social Media, etc.). There is no time limit for this exercise, but we expect it to take a few hours.

## Setup

Download the SQLite database at the following address:
- https://cornell.box.com/s/x70lullie3vi7vbyfrzrankl2wsbwnau

The provided SQLite database should contain two tables:
- `CUR_LABOR_EXP`:  All current labor expenses 
- `LM_EARNINGS`: Last Month's employee earnings

Note: "Current" and "Last Month" are relative to February, 2025

## Task

Using the provided SQLite database, build an ETL and API for the Personnel Dashboard. The ETL and API should be well documented, performant, and consider edge cases. Please review all requirements below.

### Part I - ETL

- The ETL should build a table of personnel records using the source data provided.
- Any operations or transformations applied to the source data should be reproducible (i.e. given a new source database like the one provided, the ETL should recreate the data).

### Part II - API

The API endpoints should:
- Return a JSON payload
- Require a custom header `x-user-id`.
	- This is the id of user (ie the Project Manager) making the request.
	- The API should always respect the provided `x-user-id`
	- For example, if `x-user-id` is `abc123`, only the personnel that user `abc123` manages should be included in the API response.
	- `x-user-id` header will serve as both user authentication and authorization 
- Return a personnel record by the personnel record id
- Return a list of personnel records by project id
- Return a list of personnel record by employee netid
- Return a list of all personnel records across all projects

Each personnel record should have the following keys:
- `record_id` - UID of the Personnel Record
- `employee_netid` - NetID of the employee
- `employee_first_name` - First name of the employee
- `employee_last_name` - Last name of the employee
- `manager_netid` - NetID of the employee's project manager
- `project_id` - ID of the project of the employee
- `project_title` - Title of the project of the employee
- `position_title` - Title of the employee's position
- `mtd_earnings` - The amount (USD) the employee was paid this month
- `lm_earnings` - The amount the employee was paid the previous month
- `ytd_earnings` - The amount the employee  was paid the past year
- `itd_earnings` - The amount the employee has been paid since the start of the project

Employees may be paid across multiple projects, by different "accounts" on the same project, or by multiple positions on the same project. In the end, there should be one personnel record for each position an employee holds on each project.

As an example, let's say Jane Smith is the manager of Project A and Project B. John Doe is an employee on both Project A and Project B. John Doe holds two positions on Project B. If Jane Smith is using the API, their full personnel list should include John Doe three times - one for Project A, another for the first position held on Project B, and a third for the second position held on Project B.

### Part III - Interview

After reviewing your submission, we may invite you to a follow-up technical interview. At this interview, we will provide you additional requirements to Part II above.

We will not expect you to implement these changes live. Instead, we would like you to walk us through your submission and discuss how you would plan to address the new requirements. For this part, we will be evaluating your adaptability, communication, and ability to design and engineer with other team members.