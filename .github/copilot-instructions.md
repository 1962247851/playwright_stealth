# OrdinaryRoad.Playwright.Stealth

Stealth tweaks for Microsoft.Playwright to reduce bot-detection signals.

## General

* Keep the public API stable; only add new APIs when requested.
* Use C# 12 and .NET 8.
* Respect nullable reference types and treat warnings as errors.
* Keep stealth scripts under `src/Playwright.Stealth/Resources/js` in sync with `StealthScriptProvider`.

## Build and Test

```bash
dotnet build -c Release OrdinaryRoad.Playwright.Stealth.sln
dotnet test OrdinaryRoad.Playwright.Stealth.sln -c Release
```

Integration tests auto-install Playwright browsers on first run via `Microsoft.Playwright.Program.Main`.

## Formatting

* Follow `.editorconfig`.
* Prefer file-scoped namespaces and single-line using directives.
* Insert a newline before the opening brace of any block.
* Use `nameof` instead of string literals for member names.

## Testing

* Use TUnit + TUnit.Assertions.
* Naming pattern: `Method_Scenario_ExpectedResult`.
* No "Arrange/Act/Assert" comments.
* Integration tests should avoid brittle selectors and use generous timeouts for external sites.

## Playwright Guidelines

* Apply stealth to a browser context before creating pages.
* Prefer `WaitUntilState.DOMContentLoaded` for external sites to reduce flakiness.
* Avoid relying on page copy text for bot detection assertions; check JS signals instead.
