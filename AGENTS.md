# Codex Project Generation Harness

This repository guides Codex to turn a natural-language brief into a runnable Java Spring Boot project. For project-generation requests, read `.agents/skills/spring-boot-project-generator/SKILL.md` and use the current request together with `PROJECT_REQUEST.md` when it contains requirements.

## Generation Rules

- Keep harness instructions and reference files at the repository root. Generate new applications under `generated/<project-slug>/` unless the user specifies another destination.
- Treat the latest user request as authoritative when it conflicts with the request template.
- Resolve routine choices with these defaults: Java 21, Maven, current stable Spring Boot, Spring MVC, and Actuator health. Record assumptions in the generated project README.
- Do not claim Spring Initializr was used unless its project generator was actually invoked. `pom.xml` is Maven configuration; it does not run Initializr.
- Preserve existing user files. Do not overwrite a populated output project without first inspecting and adapting it.
- Keep credentials out of generated source. Use environment-based configuration and safe example values.

## Harness Layout

- `PROJECT_REQUEST.md` — editable project brief template.
- `.agents/skills/spring-boot-project-generator/SKILL.md` — Codex generation workflow.
- `generated/` — destination for generated applications.
- Root `pom.xml` and `src/` — minimal Spring Boot reference starter for the harness.

## Java Conventions

Use lowercase package names, `UpperCamelCase` Java types, `lowerCamelCase` members, and four-space indentation. Put application sources in `src/main/java`, resources in `src/main/resources`, and tests in `src/test/java` within each generated project. Keep each generated application self-contained with its own build file and README.
