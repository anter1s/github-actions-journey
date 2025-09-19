# Day 05 – Outputs in GitHub Actions

In this demo, we’ll learn how to use **outputs** in GitHub Actions to pass data between jobs.

## Steps

1. **Set an output in Job 1**
   - We’ll generate a value (like a build ID or timestamp).
   - Store it as an output using `echo "name=value" >> $GITHUB_OUTPUT`.

2. **Consume the output in Job 2**
   - Access it with `needs.<job_id>.outputs.<output_name>`.

---

## Run It Yourself 🚀

1. Fork the repo: [GitHub Actions Journey](https://github.com/abdulraheem381/github-actions-journey)
2. Navigate to `.github/workflows/day05-outputs.yml`
3. Trigger the workflow manually or push a commit
4. Check the logs under **Job 2 – Deploy** to see the output being reused
