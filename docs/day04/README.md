

# 🚀 Day 04: Job Artifacts in GitHub Actions

Today we’re exploring **Job Artifacts** — files created during one job and shared with another.
They’re super useful when you need to pass build outputs, logs, or test reports between jobs in a workflow.

---

## 📦 What Are Artifacts?

Artifacts are files generated during a workflow run that you can:

* **Upload** at the end of one job.
* **Download** in another job.
* Keep them stored in GitHub for inspection later.

Think of them as the "glue" between jobs.

---

## 🛠 Actions We Used

* **`actions/upload-artifact@v4`** → Uploads files created in a job (example: build output).
* **`actions/download-artifact@v5`** → Downloads previously uploaded files for another job to use.

---

## 📂 Node App

The app is in:

```
docs/day04/day04-node-app
```

It has:

* `index.js` (sample code)
* `tests/` (simple Jest test)
* `build` script → generates a `dist/index.html`

---

## ⚡ Workflow

The workflow is here:

```
.github/workflows/day04-artifacts.yml
```

It has 3 jobs:

1. **Test Job**

   * Runs linting & tests on the Node app.

2. **Build Job**

   * Runs after tests pass.
   * Builds the app into `dist/`.
   * Uploads `dist/` as an artifact.

3. **Deploy Job**

   * Downloads the `dist/` artifact.
   * Lists files (demo purpose).
   * Prints a fake deploy message.

---

## ▶️ How to Run

1. **Fork the repo**

2. **Push code to `main`** branch OR manually trigger with `workflow_dispatch`. 

3. **Go to Actions tab** → Select **Day 04 Workflow**.


4. **Run the workflow**.

   * Test → Build → Deploy jobs will run.
   * Deploy job shows the downloaded `dist/index.html`.

---

## ✅ Expected Output

* Lint & test run successfully.
* `dist/` folder uploaded as artifact.
* Deploy job downloads artifacts and prints:

```
index.html
Deploying......
```

---

This makes artifacts feel **practical, simple, and powerful** ⚡

