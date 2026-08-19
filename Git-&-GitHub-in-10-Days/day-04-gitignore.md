# Day 04 — .gitignore and Tracked vs Untracked Files

## What is `.gitignore`?

`.gitignore` is a special Git configuration file that specifies files and directories that Git should ignore.

It is commonly used to exclude generated files, dependencies, local configuration, logs, and secrets.

## Common `.gitignore` Rules

```text
node_modules/
```

Ignore the `node_modules` directory.

```text
.env
```

Ignore the `.env` file.

```text
dist/
```

Ignore the `dist` directory.

```text
*.log
```

Ignore all files ending with `.log`.

## Tracked vs Untracked

### Untracked File

A file that exists in the repository directory but has not been added to Git's tracking system.

### Tracked File

A file that Git already knows about and includes in its version control.

## Important `.gitignore` Rule

`.gitignore` mainly prevents untracked files from being added to Git.

If a file is already tracked, adding it to `.gitignore` does not automatically stop Git from tracking it.

## `.env` and Secrets

Never commit sensitive credentials such as:

- API keys
- Database passwords
- JWT secrets
- Private credentials

Use `.gitignore` to exclude local secret files.

Example:

```text
.env
```

## `.env.example`

Use `.env.example` to document required environment variables without exposing real secrets.

Example:

```env
DATABASE_URL=
JWT_SECRET=
```

## Common Node.js `.gitignore`

```text
node_modules/
.env
.env.local
dist/
coverage/
*.log
```

## `git check-ignore`

```bash
git check-ignore -v <file>
```

Shows which `.gitignore` rule is causing a file to be ignored.

Example:

```bash
git check-ignore -v debug.log
```

## Useful `.gitignore` Patterns

Specific file:

```text
.env
```

Directory:

```text
node_modules/
```

File extension:

```text
*.log
```

Negation:

```text
*.log
!important.log
```

The negation pattern can re-include a file that would otherwise be ignored.

## Important Rules

1. `node_modules` should normally not be committed.
2. `.env` should normally not be committed.
3. `package.json` should normally be committed.
4. `package-lock.json` should normally be committed for npm projects.
5. `.gitignore` itself should normally be committed.
6. Never rely on deleting a secret later; avoid committing secrets in the first place.
7. If a secret is accidentally exposed, rotate or revoke the credential.

## Key Takeaways

- `.gitignore` controls which untracked files Git should ignore.
- Tracked files are not automatically untracked by adding them to `.gitignore`.
- `node_modules/`, `.env`, build output, and logs are common ignore targets.
- `.env.example` can document required environment variables without exposing secrets.
- `git check-ignore -v` helps debug ignore rules.
