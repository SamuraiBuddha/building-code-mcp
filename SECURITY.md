# Security Policy

## Supported Versions

| Version | Supported          |
| ------- | ------------------ |
| 1.0.x   | :white_check_mark: |
| < 1.0   | :x:                |

## Reporting a Vulnerability

We take security seriously at Building Code MCP. If you discover a security vulnerability, please follow these steps:

### 1. Do NOT Create a Public Issue

Security vulnerabilities should never be reported via public GitHub issues as this could put users at risk.

### 2. Email Us Privately

Send details to: **security@ehrigbim.com**

Include:
- Type of vulnerability
- Full paths of source file(s) related to the issue
- Location of affected source code (tag/branch/commit)
- Step-by-step instructions to reproduce
- Proof-of-concept or exploit code (if possible)
- Impact of the issue

### 3. Response Timeline

- **Initial Response**: Within 48 hours
- **Status Update**: Within 5 business days
- **Resolution Target**: Within 30 days for critical issues

## Security Best Practices for Users

### API Key Management

```javascript
// NEVER do this
const API_KEY = 'sk-abc123...';

// ALWAYS do this
const API_KEY = process.env.ICC_API_KEY;
```

### Environment Variables

1. Copy `.env.example` to `.env`
2. Never commit `.env` files
3. Use strong, unique API keys
4. Rotate keys regularly
5. Use different keys for dev/staging/production

### Data Handling

- **No Case Data Storage**: We never store client case data
- **Cache Only**: Only public code sections are cached
- **Encryption**: All API communications use TLS
- **Audit Logs**: All queries are logged (not content)

### Access Control

```javascript
// Implement role-based access
const userRoles = {
  admin: ['read', 'write', 'delete'],
  user: ['read'],
  guest: []
};
```

## Security Features

### Built-in Protections

- **Input Validation**: All inputs sanitized
- **Rate Limiting**: API calls throttled
- **SQL Injection Prevention**: Parameterized queries
- **XSS Protection**: Output encoding
- **CSRF Protection**: Token validation

### Dependency Management

```bash
# Regular security audits
npm audit

# Auto-fix vulnerabilities
npm audit fix

# Check for updates
npm outdated
```

### Secure Configuration

```javascript
// config/security.js
module.exports = {
  // API Rate Limiting
  rateLimit: {
    windowMs: 15 * 60 * 1000, // 15 minutes
    max: 100 // limit each IP to 100 requests
  },
  
  // Session Configuration
  session: {
    secret: process.env.SESSION_SECRET,
    resave: false,
    saveUninitialized: false,
    cookie: {
      secure: true, // HTTPS only
      httpOnly: true,
      maxAge: 3600000 // 1 hour
    }
  },
  
  // CORS Settings
  cors: {
    origin: process.env.ALLOWED_ORIGINS?.split(',') || false,
    credentials: true
  }
};
```

## Common Vulnerabilities to Avoid

### 1. Injection Attacks

```javascript
// VULNERABLE
const query = `SELECT * FROM codes WHERE section = '${userInput}'`;

// SECURE
const query = 'SELECT * FROM codes WHERE section = ?';
db.query(query, [userInput]);
```

### 2. Sensitive Data Exposure

```javascript
// VULNERABLE
logger.info('API call made', { apiKey: process.env.API_KEY });

// SECURE
logger.info('API call made', { keyId: maskApiKey(process.env.API_KEY) });
```

### 3. Authentication Issues

```javascript
// Implement proper authentication
app.use(async (req, res, next) => {
  const token = req.headers.authorization?.split(' ')[1];
  
  if (!token) {
    return res.status(401).json({ error: 'No token provided' });
  }
  
  try {
    const decoded = jwt.verify(token, process.env.JWT_SECRET);
    req.user = decoded;
    next();
  } catch (error) {
    return res.status(401).json({ error: 'Invalid token' });
  }
});
```

## Security Checklist for Contributors

- [ ] No hardcoded secrets or API keys
- [ ] All user inputs validated and sanitized
- [ ] Database queries use parameterization
- [ ] Authentication required for sensitive operations
- [ ] Error messages don't leak sensitive information
- [ ] Dependencies are up-to-date
- [ ] Security headers implemented
- [ ] HTTPS enforced
- [ ] Logging doesn't include sensitive data
- [ ] Rate limiting implemented

## Incident Response Plan

### 1. Detection
- Automated monitoring alerts
- User reports
- Security audits

### 2. Assessment
- Determine scope and impact
- Identify affected users
- Document timeline

### 3. Containment
- Isolate affected systems
- Revoke compromised credentials
- Apply temporary fixes

### 4. Eradication
- Remove vulnerability
- Update dependencies
- Deploy patches

### 5. Recovery
- Restore normal operations
- Monitor for recurrence
- Update documentation

### 6. Lessons Learned
- Post-incident review
- Update security practices
- Share knowledge with team

## Compliance

### Attorney-Client Privilege

- Never log case details
- Don't store litigation data
- Respect confidentiality
- Implement data retention policies

### Industry Standards

- OWASP Top 10 compliance
- SOC 2 Type II (planned)
- ISO 27001 (roadmap)

## Security Tools

### Recommended

- **Snyk**: Vulnerability scanning
- **ESLint Security Plugin**: Code analysis
- **OWASP ZAP**: Penetration testing
- **npm audit**: Dependency checking

### CI/CD Integration

```yaml
# .github/workflows/security.yml
name: Security Scan
on: [push, pull_request]
jobs:
  security:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Run Snyk
        uses: snyk/actions/node@master
        env:
          SNYK_TOKEN: ${{ secrets.SNYK_TOKEN }}
```

## Contact

**Security Team Email**: security@ehrigbim.com

**PGP Key**: [Coming Soon]

**Bug Bounty Program**: [Coming Soon]

---

*Last Updated: August 21, 2025*
*Version: 1.0.0*