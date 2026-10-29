[#agents/shared/security-lens.md]

In code, also look for: missing authentication or authorization checks, access to another user's or tenant's data, injection (SQL, shell, path traversal, HTML/XSS), unvalidated input at trust boundaries, unsafe redirects, and permissive CORS or cookie settings.

Trace each new input from where it enters to where it is used. Describe the attacker and the path for each finding; theoretical hardening with no reachable exploit in this change is not a finding. Never copy a secret, token, password or personal data value into your output; name the file and line instead.
