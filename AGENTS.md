# Recap Agent Guide

This repository is a Swift Package for building markdown-driven "What's New" screens in SwiftUI. Use this file as the primary source of guidance for AI coding agents working in the repo.

## Read This First

- `README.md` for package usage, release markdown format, and public customization examples.
- `Package.swift` for supported platforms and target layout.
- `Sources/Recap/Public/` for the supported public API surface.
- `Demo/Demo/Assets/Releases.md` for a complete releases markdown example.
- `Demo/Demo/DemoRecapScreen.swift` and `Demo/Demo/App.Demo.swift` for end-to-end demo integration.

## Repository Layout

- `Sources/Recap/Public/` contains the public API that app integrations should prefer.
- `Sources/Recap/Internal/` contains implementation details that should only be changed for library work.
- `Sources/Recap/Resources/` contains package resources such as localized strings.
- `Tests/` contains Swift test coverage for parsing, versioning, and display policy behavior.
- `Demo/` contains the sample Xcode project used to validate package behavior in an app context.

## Core Public APIs

Prefer these APIs before inventing custom integration logic:

- `ReleasesParser(fileName:)` for bundled release markdown.
- `RecapScreen(releases:)` as the standard entry point for presentation.
- `RecapDisplayPolicy` and `RecapDisplayPolicy.Trigger` for version-gated presentation rules.
- `View+Recap` modifiers for styling and behavior customization.
- `RecapScreenPaginationStyle.automatic` unless a task explicitly requires forced `.labeled` or `.compact`.

## Working Conventions

- Treat `Sources/Recap/Public/` as the contract for downstream users.
- Avoid changing internal implementation when the requested behavior can be achieved with existing public APIs.
- Keep examples aligned with the README and demo app so package docs and sample code stay consistent.
- Preserve behavior across iPhone, iPad, and Mac Catalyst when touching pagination or presentation logic.
- Keep release-facing copy user-focused rather than commit-style.

## Release Markdown Rules

When creating or editing a Recap releases markdown file:

- Keep the newest release first.
- Follow the schema documented in `README.md`.
- Use one release section per app version.
- Use user-facing feature titles and descriptions.
- Choose `Major`, `Minor`, or `Patch` based on product impact, not commit count.
- Reuse the structure and tone of `Demo/Demo/Assets/Releases.md`.

## Validation

- Run `swift test` for package verification.
- If the task affects app presentation or integration guidance, also inspect the demo project in `Demo/Demo.xcodeproj`.

## Documentation Sync

- Keep this file, `README.md`, demo examples, and the public API in sync.
- If a task is specific to Recap integration, release authoring, or screen customization, the companion skill lives at `.agents/skills/recap-integration/SKILL.md`.
