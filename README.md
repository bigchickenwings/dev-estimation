# dev-estimation
Tool to estimate a project delivery date based on keywords assumptions

## Current Stage (Last updated at 19/JUN/2022)
This project is still in its early stages, so there's pretty much nothing here!

I also wouldn't suggest contributing (PR) yet as there'll most likely be many changes to the app and its goals.

But feel free to suggest features, ideas, or anything, and even post them on issues!

Issues or suggestions are more than welcome! You can mail me at frpm1001@gmail.com

______

## List of Desired Features
- CRUD user
- CRUD organization
  - organization can have a default days/week to pass down (suggest) to the project
- User can create organization
  - users_organizations holds the authority level of the user within the organization
- CRUD project
  - project also saves the info about days/week
  - can add a buffer time/multiplier to the project
  - can add a team size multiplier (divider, if you will) to the project
  - project saves info about days/progress
  - N:1 organization
- CRUD estimate
  - N:1 project
- CRUD pre-made estimates per organization
  - i.e [CRUD = 1 day of work, login = 2 days of work]...
  - different organizations can set different time estimates and create their own
- Calculate total time of project delivery + elaborate a timeline based on the inputs
- Print a simple text document from it

### Long-term Features
- Can generate cards for trello/project management tools
- Generate a presentation for potential stakeholders based on the inputs

______

## ERD
- The ERD itself is under construction. Below you can see the relationships planned:

- users N:N organizations
  - (not adding specific tables for different authority levels because they can be changed at any given time).
- organization 1:N projects
- projects N:N users
- project 1:N estimates
- estimates N:N pre-made estimates
- estimates N:N custom-made estimates (might not be saved)

______

## Goals
- Get used to do TDD from the beginning of the project
- Have a tool that allows devs to effectively and quickly provide a project delivery date

______

## Commands
Run `github actions` locally using [act](https://github.com/nektos/act):
- Required gems:
  - [`bundler-audit`](https://github.com/rubysec/bundler-audit) for auditioning gem versions
  - [`brakeman`](https://github.com/presidentbeef/brakeman) for vulnerability check
  - [`standard`](https://github.com/testdouble/standard) for linters
- Keep in mind that you also need Docker for using `act`.
```bash
act --container-architecture linux/amd64 pull_request
```

Create `binstubs` to run the action commands locally/in docker:
```bash
bundle binstubs bundler-audit
bundle binstubs brakeman
bundle binstubs standard
```

Running `standard` for linter corrections:
```bash
bin/standardrb --fix
```

Running `Rails inbuilt testing`:
```bash
rails test:all
```
