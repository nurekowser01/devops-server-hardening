# Production SSH Hardening (`devops-ssh-hardening`)

## Security Rule
Never disable password authentication or root access before verifying that key-based access works across multiple sessions. 

## Implementation
1. **Ed25519 Keys:** Only accept Ed25519 or RSA-4096. Reject DSA/RSA-1024.
2. **Disable Root Login:** `PermitRootLogin no`.
3. **Disable Passwords:** `PasswordAuthentication no`.
4. **AllowUsers:** Restrict SSH access to specific users (`AllowUsers devops admin`).
5. **Fail2ban:** Automatically bans IPs with repeated failures.
6. **Port Change (Optional):** Changing port 22 is an obfuscation tactic that reduces log spam. It is *not* a substitute for cryptographic key authentication.
