# Day 06 – GitHub Actions Contexts

Today’s topic is **GitHub Actions Contexts**. Contexts let you access useful information about workflows, jobs, runners, and events. They’re available as expressions like `${{ github }}`, `${{ runner }}`, `${{ job }}`, and more.

For today’s exercise, we are focusing on the **`github` context** by logging issue event details.

## 🚀 Workflow: Output Issue Event Details
You will find today’s workflow in:

```

docs/day06/.github/workflows/day06-contexts.yml

````

This workflow is triggered whenever an **issue** is opened, edited, or closed. It logs useful details about the issue.

```yaml
name: Output Issue Event Details

on:
  issues:
    types: [opened, edited, closed]

jobs:
  log-issue-details:
    runs-on: ubuntu-latest
    steps:
      - name: Print issue details
        run: |
          echo "Action: ${{ github.event.action }}"
          echo "Issue Number: ${{ github.event.issue.number }}"
          echo "Issue Title: ${{ github.event.issue.title }}"
          echo "Issue Body: ${{ github.event.issue.body }}"
          echo "User: ${{ github.event.issue.user.login }}"
          echo "URL: ${{ github.event.issue.html_url }}"
````

---

## 📝 Exercise

* Open, edit, or close an issue in your repo.
* Check the workflow logs under **Actions tab**.
* You’ll see details about the issue printed directly from the `github` context.

---

## 🔍 Extra Examples

While today’s workflow uses the `github` context, here are other useful contexts:

* **`runner` context** → Logs OS, architecture, and environment details.
* **`job` & `steps` context** → Track step outcomes inside jobs.

We’ll cover these in the blog post.



