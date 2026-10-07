# Codex Java Project Generation Harness

This repository is a Codex harness for generating Java Spring Boot applications from a natural-language project brief. The root Spring Boot app is a small reference starter; generated projects belong under `generated/` so they stay separate from harness instructions.

## Generate a Project

1. Describe the app in `PROJECT_REQUEST.md`, or give Codex the requirements directly in your request.
2. Ask Codex to generate the project. It reads `AGENTS.md` and follows `.agents/skills/spring-boot-project-generator/SKILL.md`.
3. Codex creates a self-contained Maven project in `generated/<project-slug>/` unless you specify another location.

The harness defaults to Java 21, Maven, Spring Boot's current stable release, Spring MVC, and Actuator health. Codex should record assumptions and tell you how to run the result.

## Reference Starter

The root `pom.xml` and `src/` show a minimal Spring Boot app with web and Actuator dependencies. Run the reference app with `mvn spring-boot:run` when Java 21 and Maven 3.6.3 or newer are installed. Its health endpoint is `http://localhost:8080/actuator/health`.

## Harness Files

- `AGENTS.md` — repository-level Codex rules and output layout.
- `PROJECT_REQUEST.md` — reusable project brief template.
- `.agents/skills/spring-boot-project-generator/SKILL.md` — detailed generation workflow.
- `generated/` — output folder for generated applications.
