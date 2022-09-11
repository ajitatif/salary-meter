[![Contributor Covenant](https://img.shields.io/badge/Contributor%20Covenant-2.1-4baaaa.svg)](CODE_OF_CONDUCT.md)

# salary-meter
A crowdsourced salary statistics gathering tool, with zero personal info stored

# Design

## Requirements 

- Must ensure the uniqueness of users
- Users must login before viewing salaries
- Users may browse averages before submitting their salary
- More detailed statistics may be revealed after submission

## Choice of Technology

The design should be simple; nothing fancy. Just whatever works. 
Also, it should be extendable to microservices with as less effort as possible in case 
the project goes viral. The tech stack should also be appealing to the community 
to induce a motivation to contribute. It also has to be maintainable by the founder, 
therefore the project will built upon JRE technologies.  

The most popular choice would be Spring framework, but since it lacks proper support 
on native images and the poor startup time on microservices; a better alternative 
is Quarkus which is based on Jakarta EE standards.  

Quarkus supports Qute template engine out of the box, so this is a good place to start

## Frontend Technologies

Since the founder is no expert in FE topics, this decision is still to be made. 
However, since using a template engine is already decided; it might be safe to 
assume that the FE will be _initially_ hosted on the project itself, being hosted 
by the whatever Application Server the project comes with.  

It is likely, however, that the Front End files will be on cloud storages in a 
relatively short time.  

## Database Structure

### Salary

| Field             | Type | Description |
|-------------------| --- | --- |
| amount            | number | The salary, as provided by the user |
| first_compensated | date | The date of first compensation, as in payroll |
| created_at | datetime | The date of creation |
| updated_at | datetime | The date of update |
| user_id | number | The user's ID who has provided this info |
| company_id | number | Company's ID where the user had this salary at the given date |
| role_id | The Role, namely the position for this salary |

### Salary Skills

| Field             | Type | Description |
|-------------------| --- | --- |
| salary_id | number | |
| requirement_id| number | | 

### Skill

| Field             | Type | Description |
|-------------------| --- | --- |
| id | number | | 
| name | varchar(63) | | 

### User

| Field         | Type | Description                          |
|---------------| --- |--------------------------------------|
| id            | number |                                      |
| nickname      | varchar(31) | A generated name for the user |
| linkedin_id   | text | The ID at the source of user's signup |