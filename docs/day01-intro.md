# Day 01 - Introduction to GitHub Actions 🚀

## 🔹 What is GitHub Actions?
GitHub Actions is a **CI/CD (Continuous Integration & Continuous Delivery) tool** built into GitHub.  
It allows you to **automate workflows** directly in your repositories.  

Think of it like:
- Jenkins, but inside GitHub  
- Automating tasks like testing, building, and deployment  
- Event-driven → workflows run when something happens (push, pull request, schedule, or manually)

---

## 🔹 Why do we need GitHub Actions?
- Automate repetitive tasks 🛠️  
- Run tests automatically on every PR ✅  
- Deploy applications to servers or cloud ☁️  
- Improve team collaboration 👥  

---

## 🔹 Core Building Blocks

1. **Workflows** → YAML files inside `.github/workflows/`. They define *what happens*.  
2. **Jobs** → A workflow has one or more jobs. Each job runs in its own runner.  
3. **Steps** → Each job is made of steps. Steps run commands or actions.  
4. **Runners** → The machines (Linux, Windows, Mac) that execute the jobs.  
5. **Events/Triggers** → Define *when* a workflow runs (push, PR, schedule, manual).  

---

## 🔹 Day 01 Practical: Hello World 🌍

Today’s goal → Run your first GitHub Actions workflow.  

Workflow file → [`day01-hello-world.yml`](../.github/workflows/day01-hello-world.yml)  

### ✅ Steps to run:
1. Fork this repo into your account.  
2. Go to the **Actions tab** in your repo.  
3. Select **Day 01 - Hello World** workflow.  
4. Click **Run workflow**.  
5. 🎉 You should see the output:  
👋 Hello, GitHub Actions! This is Day 01 of my learning journey.