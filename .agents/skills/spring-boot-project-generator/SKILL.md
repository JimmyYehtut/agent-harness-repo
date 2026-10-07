---
name: spring-boot-project-generator
description: Turn a natural-language application brief into a complete Java Spring Boot project in this repository. Use when asked to generate, scaffold, or bootstrap a Java project.
---

# Spring Boot Project Generator

Generate a self-contained Java application from the user's requirements. The goal is a project the user can build and run, not just a dependency file or an empty application shell.

## Inputs and Destination

1. Read the current user request and `PROJECT_REQUEST.md` if it exists. Treat the current request as the latest source of truth; use the template to fill in missing context.
2. Infer a concise project slug and Java package from the requested name. Ask a question only when an unresolved product requirement prevents a useful implementation; otherwise make a reasonable choice and document it.
3. Write new projects to `generated/<project-slug>/` by default. Honor an explicit user destination. Inspect existing files before modifying any populated output directory.

## Project Defaults

- Java 21 and Maven.
- Current stable Spring Boot release, verified against official Spring documentation when choosing or changing the version.
- Spring MVC for HTTP applications and Actuator health unless the brief calls for another stack.
- Standard Maven layout: `src/main/java`, `src/main/resources`, and `src/test/java`.
- Environment variables for secrets and deployment-specific configuration; include safe examples, never real credentials.

## Generate the Application

- Implement the features described in the brief, including the main application entry point, domain/application code, HTTP endpoints where needed, and configuration.
- Keep the generated project independent of the harness: include its own `pom.xml`, README with prerequisites and run instructions, and `.gitignore`.
- Add focused automated tests for generated behavior. Run them when the user requests verification and the required Java/Maven toolchain is available; report clearly when the environment prevents execution.
- Prefer Spring Initializr when it is available and actually invoked. Otherwise create the equivalent project files directly. Never describe a manually authored `pom.xml` as having initialized or run Spring Initializr.
- Avoid adding databases, security providers, cloud services, or AI model integrations unless the brief requires them. For unspecified choices, document the assumption rather than inventing credentials or external services.

## Completion Summary

Report the generated project path, the main features and assumptions, and the command to run it. Include verification results only for commands that were actually run.
