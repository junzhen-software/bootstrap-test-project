# Reproducible Execution Playbook

This playbook provides example execution paths. Adapt versions to the supported project toolchain and record the exact versions actually used. Examples do not authorize access, writes, merges, deployments or external uploads.

## Required execution record

For every verification or state-changing operation, record:
- OS and version;
- tool/runtime name and version;
- exact command or API operation (redact secrets);
- working directory/repository and fixed branch/SHA;
- expected exit code or API success condition;
- actual exit code/status and raw log location;
- fallback used if the preferred tool was unavailable.

## Git CLI path (Git 2.40+ examples)

Run from a trusted local clone. Read-only checks:

```bash
git --version
git status --short --branch
git rev-parse HEAD
git show --no-patch --format=fuller HEAD
git branch --all --verbose
git tag --list
```

Expected: `git --version` exits 0; repository inspection commands exit 0 when run inside a valid repository. A non-zero exit must be recorded, not hidden.

To verify a file hash on Linux/macOS:

```bash
sha256sum path/to/file
```

On Windows PowerShell:

```powershell
$PSVersionTable.PSVersion
Get-FileHash -Algorithm SHA256 -LiteralPath 'path\to\file'
```

Expected: one SHA-256 digest is returned for the exact file bytes. Record the digest and file path. Do not compare hashes after newline or encoding conversion.

## GitHub CLI path (gh 2.50+ examples)

```bash
gh --version
gh auth status
gh repo view OWNER/REPO --json name,defaultBranchRef,isPrivate
gh pr view 24 --repo OWNER/REPO --json state,isDraft,mergedAt,headRefOid,baseRefOid
gh issue list --repo OWNER/REPO --state open
```

Expected: commands return structured repository/PR/Issue data and exit 0 when authenticated and authorized. Authentication status must not be copied into logs if it exposes sensitive details.

## GitHub REST API fallback (when gh is unavailable)

Use an authorized GitHub API client or the platform's connected GitHub tools. Example read-only requests:

```http
GET /repos/OWNER/REPO
GET /repos/OWNER/REPO/git/ref/heads/BRANCH
GET /repos/OWNER/REPO/commits/COMMIT_SHA
GET /repos/OWNER/REPO/contents/PATH?ref=COMMIT_SHA
GET /repos/OWNER/REPO/pulls/NUMBER
GET /repos/OWNER/REPO/issues?state=open
```

Expected: HTTP 200 and the required fields are present. Record API version, request method/path (never tokens), response status, timestamp and relevant response identifiers. For content endpoints, record the exact ref and decode base64 bytes before hashing.

If an API operation is unavailable, use the equivalent authorized UI workflow and capture the page URL, exact ref/SHA, timestamp and observed result. A screenshot or summary without the exact object identity is insufficient for a consequential acceptance claim.

## Tool unavailable / failed

1. Record the attempted command/API operation, tool version if available, timestamp and exact error/exit code.
2. Do not report the operation as completed.
3. Use a documented alternative path (CLI → REST/API → authorized UI), if available and permitted.
4. Re-run the same acceptance check through the alternative path and preserve its evidence.
5. If no authorized alternative exists, mark the criterion BLOCKED or NOT VERIFIED and identify the required owner action.

Never invent a tool version, successful exit code, API response or test result.
