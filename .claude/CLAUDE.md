# Claude User Memory

## JIRA Ticket Preferences

When creating JIRA tickets, use this template and save output to `jira-ticket.md`:

```
As a < user > I want to < goal > so that < reason >

Context 

Describe in more details the issue the user have, their needs, and any other requirements. 

Acceptance Criteria

Describe the conditions that have to be fulfilled so the story is done. 

[Optional ?] Scenarios: 
Given
When
Then

Test Plan?

[This later on can be referenced in the PR process to guide other reviewers on how to test this issue]

Refinement

[mm-dd] Feedback, assessment of current data / metric availability, notes, follow-ups from the refinement process, internal/external dependencies.
```