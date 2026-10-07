# Jira Ticket Implementation Workflow

This guide describes how Codex can implement a Jira ticket in one repository using requirements stored in another repository, validate the change, and push a feature branch to GitHub.

## Required Harness Capabilities

- **Workflow skill:** Add `.agents/skills/jira-ticket-implementation/SKILL.md`. The skill should explain how to read the ticket and spec, inspect the target repository's `AGENTS.md`, create a branch, implement the change, run checks, review the diff, push, and report results.
- **Jira access:** Connect an authorized Jira integration or MCP server that can read issue details and acceptance criteria. Alternatively, include the ticket text in the request.
- **GitHub access:** Use an authorized GitHub integration or authenticated local Git to push a feature branch and, if requested, open a pull request.
- **Shell and repository access:** Codex needs read access to the spec repository and write access to the target repository, plus the ability to run its build and test commands.

A skill provides repeatable instructions; it does not grant access to Jira, GitHub, or files. MCP tools or other integrations provide live data and actions. A slash command is optional convenience and does not replace those capabilities.

## Recommended Workflow

1. Read the Jira issue, acceptance criteria, and any linked details.
2. Read the specified spec file and treat the spec repository as read-only unless asked to change it.
3. Inspect the target repository's instructions, implementation, and documented build commands.
4. Create a ticket-named feature branch, such as `ABC-123-add-order-status`.
5. Implement the requirements and add or update focused tests.
6. Run the repository's documented checks, inspect the diff, and report any failures or assumptions.
7. Push the feature branch and report its name and verification results. Open a pull request if requested.

Do not change Jira status or push to the default branch unless specifically requested. Keep credentials out of source files and logs.

## Access and Permission Setup

The Codex session must be able to write to the target checkout and read the spec checkout. If Codex is opened only in the harness repository, its workspace sandbox may not permit edits to another path. Open Codex in the target repository or explicitly configure the session's workspace roots and permissions. Provide Git credentials through the authorized integration or local credential manager, not through the prompt.

## Example Request

> Use the Jira ticket implementation workflow for ABC-123. Implement it in `D:\work\orders-service`. Read requirements from `D:\work\architecture-specs`, branch `main`, file `orders/ABC-123.md`. Create a feature branch, run the project's checks, push the branch to GitHub, and report the branch name and results.

## Current Harness Scope

The harness currently includes `.agents/skills/spring-boot-project-generator/SKILL.md`, which generates new Spring Boot projects. Ticket implementation in an existing service should use a separate Jira implementation skill rather than expanding the generator skill to cover unrelated work.
