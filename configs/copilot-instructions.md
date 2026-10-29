# GitHub Copilot Instructions

Apply the following production standards when generating code, tests, or completions:

## General Rules
- Always generate fully typed code (TypeScript with strict interfaces, Python with full typing annotations).
- Avoid bloated dependencies when standard library or clean native methods suffice.
- Ensure error handling is explicit with meaningful error messages and status codes.

## Security & Secrets
- Never hardcode API keys, database credentials, or tokens in completions. Use environment variable lookups.
- Enforce input sanitization to prevent SQL injection, XSS, and command injection.

## Performance & Testing
- Avoid N+1 queries in ORMs; suggest eager loading or joins.
- Generate unit tests for critical edge cases whenever creating new utility functions.
