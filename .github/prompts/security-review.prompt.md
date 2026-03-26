---
agent: agent
description: "Run security analysis on the codebase. Detect vulnerabilities, hardcoded secrets, injection risks, and provide remediation."
tools: ['codebase', 'terminal', 'fetch', 'findTestFiles']
---

# Security Review

Invoke the **security-reviewer** agent to perform comprehensive security analysis.

## What This Prompt Does

1. **Scan for vulnerabilities** — OWASP Top 10, CWE/SANS Top 25
2. **Detect hardcoded secrets** — API keys, tokens, passwords in source
3. **Check dependencies** — Known CVEs in third-party packages
4. **Verify input validation** — SQL injection, XSS, command injection
5. **Review authentication** — Auth flows, session management, CSRF

## Severity Levels

- **CRITICAL**: Immediate exploitation risk (hardcoded secrets, SQL injection, RCE)
- **HIGH**: Significant risk requiring fix before deployment (XSS, auth bypass, IDOR)
- **MEDIUM**: Should be fixed but not immediately exploitable
- **LOW**: Best practice improvement

## Security Checklist

- [ ] No hardcoded secrets (API keys, passwords, tokens)
- [ ] All user inputs validated
- [ ] SQL injection prevention (parameterized queries)
- [ ] XSS prevention (sanitized HTML)
- [ ] CSRF protection enabled
- [ ] Authentication/authorization verified
- [ ] Rate limiting on all endpoints
- [ ] Error messages don't leak sensitive data
- [ ] Dependencies checked for known CVEs
- [ ] Sensitive data encrypted at rest and in transit

## Response Protocol

If a CRITICAL issue is found:
1. STOP and flag immediately
2. Provide specific remediation steps
3. Check for similar issues elsewhere in the codebase
4. Recommend secret rotation if credentials were exposed
