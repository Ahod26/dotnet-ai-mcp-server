# Security Policy

## Reporting a Vulnerability

If you discover a security vulnerability in the DotNet AI MCP Server, please report it responsibly.

### How to Report

1. **Do not** open a public GitHub issue for security vulnerabilities
2. Email your findings to the repository owner directly
3. Include as much detail as possible:
   - Description of the vulnerability
   - Steps to reproduce
   - Potential impact
   - Suggested fix (if any)

### What to Expect

- Acknowledgment of your report within 48 hours
- Regular updates on the progress
- Credit for responsible disclosure (if desired)

## Scope

This security policy applies to:

- The DotNet AI MCP Server hosted at `https://dotnetaimcp.net`
- This open-source repository

### Out of Scope

- Third-party repositories (semantic-kernel, openai-dotnet, etc.) — report to their respective owners
- Microsoft Learn documentation — report to Microsoft

## Security Considerations

### Data Handling

- **No data collection**: We do not store prompts, queries, or user information
- **Read-only access**: The server only fetches public content from GitHub and Microsoft Learn
- **No authentication**: No credentials or tokens are required from users

### Server Security

- All connections are served over HTTPS
- The server implements standard rate limiting
- No user-submitted code is executed

## Supported Versions

| Version | Supported          |
| ------- | ------------------ |
| Latest  | :white_check_mark: |
