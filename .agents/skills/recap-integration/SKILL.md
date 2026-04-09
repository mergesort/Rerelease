---
name: recap-integration
description: Integrates the Recap Swift package into SwiftUI apps, authors Recap-compatible releases markdown, and configures RecapDisplayPolicy and RecapScreen customization. Use when adding Recap into an app, updating Releases.md, or customizing the behavior of a Recap screen.
---

# Recap Integration

Use this skill when integrating, configuring, or using the Recap library.

Project-wide repository guidance now lives in `AGENTS.md` at the repo root. Use this skill for Recap-specific integration decisions that go beyond the shared repo guidance.

## What to read first

Start with these files:

- `AGENTS.md`
- `README.md`
- `Sources/Recap/Public/RecapScreen.swift`
- `Sources/Recap/Public/View+Recap.swift`
- `Sources/Recap/Public/RecapDisplayPolicy.swift`
- `Sources/Recap/Public/RecapDisplayPolicy.Trigger.swift`
- `Demo/Demo/Assets/Releases.md`
- `Demo/Demo/DemoRecapScreen.swift`

Read additional public API files in `Sources/Recap/Public/` only if the task touches a specific type.

## Core workflow

1. Identify whether the task is about integration, release authoring, display policy, or screen customization.
2. Prefer Recap's public APIs over custom implementations.
3. Match existing Recap naming and examples from the README and demo app.
4. Keep examples and release content user-facing and concise.

## Mac Catalyst guidance

If the task touches Mac Catalyst:

- Preserve the distinction between automatic pagination, labeled buttons, and compact buttons.
- Be careful not to regress iPhone or iPad behavior while changing Catalyst presentation.

## Avoid

- Do not invent a different release markdown format.
- Do not parse releases manually if `ReleasesParser` is sufficient.
- Do not replace `RecapDisplayPolicy` with custom version-comparison logic unless the user explicitly needs behavior outside the public API.
