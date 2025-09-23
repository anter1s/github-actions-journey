
# Day 08 – Functions in GitHub Actions

In **Day 08** of my GitHub Actions journey, I explored **functions** — but here’s an important detail:
Unlike contexts (`github.*`) or expressions, GitHub Actions does not provide direct built-in functions like `upper()` or `lower()`.

👉 Instead, we can **combine shell utilities** (like `tr` and `jq`) inside workflow steps to manipulate data.

---

## Workflow File

You can find the workflow file here:
📂 `.github/workflows/day08-functions.yml`

```yaml
name: Day08 - Functions Demo

on:
  push:
    branches:
      - main

jobs:
  functions-demo:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v4

      - name: Uppercase branch name
        run: |
          echo "Uppercase branch name: $(echo ${{ github.ref_name }} | tr '[:lower:]' '[:upper:]')"

      - name: Lowercase repository name
        run: |
          echo "Lowercase repo name: $(echo ${{ github.repository }} | tr '[:upper:]' '[:lower:]')"

      - name: Join commit IDs
        run: |
          COMMIT_IDS=$(jq -r '[.commits[].id] | join(", ")' "$GITHUB_EVENT_PATH")
          echo "Joined commit IDs: $COMMIT_IDS"
```

---

## Explanation

### 🔠 1. Uppercase Branch Name

We used the Linux command `tr` to convert the branch name into uppercase:

```bash
echo ${{ github.ref_name }} | tr '[:lower:]' '[:upper:]'
```

### 🔡 2. Lowercase Repository Name

Similarly, converting the repository name into lowercase:

```bash
echo ${{ github.repository }} | tr '[:upper:]' '[:lower:]'
```

### 🔗 3. Join Commit IDs

To handle arrays, we used **jq** (a JSON processor) to join all commit IDs into a single string:

```bash
jq -r '[.commits[].id] | join(", ")' "$GITHUB_EVENT_PATH"
```

This way, we get a **comma-separated list** of commit hashes for every push event.

---

## Why This Matters

Functions (or rather **function-like behavior**) are extremely powerful in GitHub Actions:

* You can **normalize branch/repo names** for consistency
* You can **transform event data** (like commit IDs, PR details, issue body, etc.)
* You can prepare values for **deployment scripts, notifications, or artifact names**

In real-world workflows, these techniques make pipelines more **flexible, dynamic, and production-ready**.


