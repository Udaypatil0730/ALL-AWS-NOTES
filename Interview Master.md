Linux User, Security & Access Control – Interview Revision Sheet
1️⃣ Non-Interactive Users (Service Accounts)
What is a non-interactive user?

A non-interactive user is a system or service account that cannot log in via SSH or terminal, but can still be used by applications, agents, or cron jobs.

/sbin/nologin vs /bin/false

/sbin/nologin

Blocks interactive login

Shows a clear message

Allows services and scripts to run

Industry-preferred option

/bin/false

Immediately exits

No message

Can break some services

Used only in rare, highly restricted cases

Best practice

Use /sbin/nologin for service and application users.

Real-time use cases

Backup agents

Monitoring tools (Prometheus, node exporter)

Web servers (Apache, Nginx)

CI/CD tools (Jenkins)

Application runtime users

SFTP-only users

Interview-ready answer

“In production, we create dedicated non-interactive users for services like backup agents, monitoring tools, and web servers to enforce least privilege. We typically use /sbin/nologin because it cleanly blocks shell access without impacting service execution.”

2️⃣ User Creation Tasks (Real-world Mapping)
Tasks performed

Created users with:

Custom UID

Custom home directory

Non-interactive shell

Created temporary users with expiry date

Created users consistently in lowercase

Why this is real

Service isolation

Compliance requirements

Temporary contractor access

Audit-friendly identity management

Interview-ready answer

“We create users with specific UIDs, home directories, and shells based on the application or service requirement. Temporary users are created with expiry dates to avoid access sprawl.”

3️⃣ Temporary User with Expiry Date
Why expiry matters

Contractors

Temporary project access

Compliance and audits

Prevents forgotten accounts

Interview-ready answer

“For temporary access, we create users with account expiry dates so access is automatically revoked without manual intervention.”

4️⃣ Custom Apache / Application Users
Why custom users?

Each application runs under its own user

Limits blast radius

Improves security isolation

Example

User: rose

UID: 1310

Home: /var/www/rose

Shell: non-interactive

Interview-ready answer

“We avoid running applications under shared users. Each application has a dedicated system user to improve isolation and reduce security risks.”

5️⃣ Group-Based Access Control
What was done

Created a common admin group

Added users to group across servers

Created user if missing

Why this matters

Centralized access control

Easy permission management

Scales across servers

Interview-ready answer

“We manage access using groups instead of assigning permissions directly to users, which simplifies administration and follows RBAC principles.”

6️⃣ Disabling Root SSH Login
Why root SSH is disabled

Root is a high-value target

No accountability

Violates security baselines (CIS)

Real-world practice

Disable PermitRootLogin

Use sudo with named users

Log and audit actions

Interview-ready answer

“In production, direct root SSH login is disabled. Administrators log in with individual accounts and elevate privileges using sudo to ensure traceability and security.”

7️⃣ CLI vs Terraform (Very Important Concept)
Real-time approach

CLI: quick testing, troubleshooting

Terraform: production, repeatable infrastructure

Truth (interview-safe)

“In real projects, infrastructure is created using Terraform or other IaC tools. CLI is mainly used for learning, validation, or emergency fixes.”

8️⃣ Why These Tasks Are Asked in Interviews

These tasks validate:

Linux fundamentals

Security awareness

Least privilege principle

Real production hygiene

DevOps mindset (manual → automated)

9️⃣ One-Line Summary (Strong Ending Answer)

“The tasks I practiced reflect real production responsibilities — managing secure service users, enforcing least privilege, controlling access via groups, disabling risky defaults like root SSH, and understanding when to use CLI versus Infrastructure as Code.”

🔹 How to Use This Sheet

Read once daily

Memorize interview answers (bold sections)

Add one sheet per day

Before interview: revise only these sheets

Final note (mentor advice)

Doing this daily revision sheet practice will:

Reduce anxiety

Improve confidence

Make answers sound natural

Separate you from average candidates
