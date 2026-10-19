---
name: security
description: >-
  Apply secure-by-design practices and the OWASP Top 10:2025 to any code that
  handles input, data, authentication, authorization, secrets, dependencies, or
  external requests. Use this skill whenever building, changing, or reviewing
  backend/API code, auth flows, database queries, file uploads, forms that take
  user input, configuration, or dependency changes — even when the user doesn't
  say "security". Enterprise software is a target; a single injection flaw,
  broken access check, or leaked secret can compromise an entire system. Covers
  input validation, access control, authentication, secrets handling, dependency
  and supply-chain safety, secure configuration, and logging.
---

# Security (OWASP Top 10:2025)

Security is not a feature you add at the end — it is a property of how the system
is designed and built. The cheapest vulnerability to fix is the one that never
ships. Treat all input as hostile, grant the least privilege necessary, fail
safely, and assume any component can be attacked. Apply this skill to any code
that touches untrusted input, data, identity, secrets, or dependencies.

The reference framework is the **OWASP Top 10:2025**, the current edition of the
most widely used web application risk list. Below is each category with the
practical defenses that matter when writing code.

## The OWASP Top 10:2025

### A01 — Broken Access Control
The #1 risk. Users doing things they shouldn't be able to.
- Enforce authorization **server-side on every request**, for every object. Never
  trust the client or a hidden field.
- Deny by default; grant access explicitly.
- Check ownership on every record access (prevent IDOR — e.g. `/orders/123`
  returning someone else's order).

### A02 — Security Misconfiguration
- Change or remove default credentials and sample accounts.
- Disable debug modes, verbose errors, and directory listings in production.
- Set security headers (CSP, HSTS, X-Content-Type-Options) and lock down CORS to
  known origins.
- Keep dev/test endpoints out of production.

### A03 — Software Supply Chain Failures *(new in 2025)*
- Pin and lock dependency versions; use a lockfile.
- Scan dependencies for known vulnerabilities (e.g. `npm audit`, Dependabot,
  `pip-audit`) and update promptly.
- Verify integrity of packages and build tooling; be wary of typosquatted or
  unmaintained packages.

### A04 — Cryptographic Failures
- Use TLS everywhere; never send sensitive data over plaintext.
- Hash passwords with a strong adaptive algorithm (bcrypt, scrypt, Argon2) —
  never MD5/SHA-1, never plain storage.
- Use vetted libraries and modern algorithms; don't roll your own crypto.
- Encrypt sensitive data at rest; manage keys properly.

### A05 — Injection
- Use **parameterized queries / prepared statements** for all SQL — never build
  queries by string concatenation.
- Validate and sanitize all input; escape output by context (HTML, attribute,
  JS, URL) to prevent XSS.
- Avoid passing untrusted input to shell commands, `eval`, or template engines.

### A06 — Insecure Design
- Threat-model features that handle money, identity, or sensitive data: what can
  go wrong, who benefits, how is it abused?
- Build in rate limiting, abuse prevention, and sensible business-logic limits.
- Security is a design requirement, not only an implementation detail.

### A07 — Authentication Failures
- Enforce strong password policies and support MFA.
- Protect against credential stuffing and brute force (rate limits, lockouts).
- Manage sessions securely: regenerate IDs on login, set `HttpOnly`/`Secure`/
  `SameSite` cookies, expire sessions, invalidate on logout.

### A08 — Software or Data Integrity Failures
- Verify integrity of code, updates, and critical data (signatures, checksums).
- Don't deserialize untrusted data without validation.
- Secure the CI/CD pipeline; untrusted code must not reach production.

### A09 — Security Logging and Alerting Failures
- Log security-relevant events (logins, failures, access-control denials,
  high-value actions) with enough context to investigate.
- **Never log secrets, passwords, tokens, or full PII.**
- Ensure logs are monitored and alert on suspicious patterns; you can't respond
  to what you can't see.

### A10 — Mishandling of Exceptional Conditions *(new in 2025)*
- Handle errors explicitly and fail **closed** (deny) on unexpected conditions,
  not open.
- Don't leak stack traces, internal paths, or system details in error responses.
- Make sure error paths can't skip security checks or leave the system in an
  inconsistent state.

## Secrets handling (applies across the board)
- Never hardcode secrets, API keys, tokens, or passwords in source code.
- Keep them in environment variables or a secrets manager; keep `.env` and
  credential files out of version control (`.gitignore`).
- If a secret is committed or leaked, rotate it — removing it from a later commit
  is not enough.

## How to apply this in practice

When writing or reviewing code:

1. Identify every trust boundary — where untrusted input enters (requests,
   uploads, params, headers, third-party data).
2. Confirm access control is enforced server-side for the specific user and the
   specific object on every sensitive action.
3. Check that queries are parameterized and output is escaped for its context.
4. Check authentication/session handling and that secrets aren't hardcoded or
   logged.
5. Check dependencies for known vulnerabilities and that config is locked down
   for production.
6. Verify errors fail closed and don't leak internal detail.

Report findings mapped to the relevant OWASP category with the concrete fix.
Prefer eliminating a class of bug (e.g. an ORM/parameterized layer) over patching
one instance.
