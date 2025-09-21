# 🔑 Day 07 – Secrets & Variables in GitHub Actions

Secrets and variables let us manage **dynamic values** and **sensitive data** in workflows.

---

## 🌱 Environment Variables
These are values you define **inside the workflow** or **per job**.

Example:
```yaml
env:
  APP_ENV: production
````

You can then use it in steps:

```bash
echo "Running in $APP_ENV mode"
```

---

## ⚙️ GitHub Variables

These are repo-level or org-level variables you define under:
**Settings → Variables → Actions**.

For example, you could define:

```
DEFAULT_BRANCH = main
```

And use it in workflows:

```yaml
${{ vars.DEFAULT_BRANCH }}
```

---

## 🔐 GitHub Secrets

Secrets store **sensitive values** like API keys or tokens.
They are always **masked in logs**.

Steps to add a secret:

1. Go to repo → **Settings** → **Secrets and variables** → **Actions**
2. Click **New repository secret**
3. Add something like:

   * Name: `DEMO_API_KEY`
   * Value: `12345-my-demo-key`

Usage in workflows:

```yaml
${{ secrets.DEMO_API_KEY }}
```

⚠️ You will never see the actual value in logs – it’s hidden for security.

---

## 🛠 Exercise

1. Fork this repo
2. Add a secret in your fork:

   * Key: `DEMO_API_KEY`
   * Value: any string you like (e.g. `my-secret`)
3. Run the workflow → check logs.

You’ll see:

* Environment variables printed
* GitHub variable printed
* Secret used (masked)

