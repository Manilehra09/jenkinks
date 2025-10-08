# 🧩 Jenkins Build Trigger Types

This document explains the **different ways to create or trigger builds in Jenkins** — manually, automatically, or through integrations.

---

## 🔘 1. Manual Build Trigger
**Description:**  
Start the build manually by clicking **“Build Now”** in the Jenkins UI.

**Use Case:**
- For ad-hoc builds or testing a pipeline.
- When you don’t want it to run automatically.

✅ *Simple and direct — no automation involved.*

---

## 🔁 2. Build Periodically (Cron Trigger)
**Description:**  
Schedule builds using **CRON syntax** (e.g., every hour, daily, weekly).

**Example Configuration:**
```bash
H/15 * * * *   # every 15 minutes
H 2 * * *      # every day at 2 AM
```

**Use Case:**
- Nightly builds
- Regular deployments or tests

✅ *Perfect for time-based automation.*

---

## 🪝 3. Git / SCM Polling (Poll SCM)
**Description:**  
Jenkins polls the Git (or SVN) repository at intervals to check for changes.

**Configuration Example:**
```bash
H/5 * * * *  # check every 5 minutes
```

**Behavior:**
- Jenkins checks for new commits.
- If changes are detected → build is triggered.

✅ *Automates builds whenever code changes are detected.*

---

## 🧠 4. SCM Webhook Trigger (GitHub/GitLab Integration)
**Description:**  
Jenkins listens for **webhooks** from your Git provider.

**Behavior:**
- When a push, PR, or merge event happens → webhook notifies Jenkins → build triggers instantly.

✅ *Faster and more efficient than SCM polling.*

---

## 🔄 5. Build After Other Projects Are Built
**Description:**  
Trigger this job automatically after another job finishes.

**Configuration:**
- Go to **Post-build Actions** in another job.
- Choose **“Build other projects”**.

**Use Case:**
- Multi-job workflows (e.g., Build → Test → Deploy).
- Chain jobs together in a sequence.

✅ *Useful for pipeline-like chaining without a full Jenkinsfile.*

---

## 💬 6. Trigger Builds Remotely (via URL / API)
**Description:**  
Start a build via **HTTP API call**.

**Setup:**
1. Enable “Trigger builds remotely” in job settings.
2. Use the provided **URL + token**.

**Example:**
```bash
curl -X POST "https://jenkins.example.com/job/app/build?token=MY_TOKEN"
```

✅ *Great for integrating Jenkins with other systems.*

---

## ⚙️ 7. Parameterized Trigger
**Description:**  
Trigger builds with **custom parameters** (like environment, version, etc.).

**Example:**
```bash
curl -X POST https://jenkins/job/app/buildWithParameters?BRANCH=dev&DEPLOY_ENV=staging
```

✅ *Flexible and interactive for DevOps teams.*

---

## 🧩 8. Upstream/Downstream Triggers (Pipeline-based)
**Description:**  
In **pipeline jobs**, stages or jobs can trigger other jobs dynamically.

**Example:**
```groovy
build job: 'deploy-job', wait: false
```

✅ *Powerful for advanced CI/CD orchestration.*

---

## ☁️ 9. Build Triggered by External Events
**Examples:**
- Docker Hub webhook
- AWS CodeCommit webhook
- Jira / Slack integration triggers

✅ *Used for event-driven automation.*

---

## 🧭 Summary Table

| Trigger Type | Description | Typical Use |
|---------------|--------------|--------------|
| Manual | Click “Build Now” | One-time or test builds |
| Build Periodically | CRON-based | Scheduled builds |
| Poll SCM | Checks Git for changes | Auto builds on code changes |
| SCM Webhook | Real-time trigger from GitHub/GitLab | Fast CI/CD |
| After Other Projects | Chain builds | Sequential pipelines |
| Remote Trigger | API-based | Integrations / scripts |
| Parameterized | User-defined variables | Multi-env deployments |
| Upstream/Downstream | Trigger from pipeline | Multi-job orchestration |

---

📘 **Author:** Kubearc  
📅 **Topic:** Jenkins Build Trigger Types  
