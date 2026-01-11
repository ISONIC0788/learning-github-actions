
# 🚀 Learning GitHub Actions

Welcome to my learning repository! Here, I am documenting my journey from a beginner to building complex CI/CD pipelines using GitHub Actions.

## 🧠 Key Concepts Mastered

I have implemented the following DevOps concepts in this repository:

* **CI/CD Pipelines:** Automating the testing, building, and deployment process.
* **Matrix Strategies:** Running jobs in parallel across multiple Node.js versions (18, 20, 22).
* **Artifact Management:** Uploading build files (`dist/`) and downloading them in subsequent jobs.
* **Job Dependencies:** Using `needs` to ensure deployment only happens after successful tests.
* **Conditionals:** Using `if` statements to control when steps run (e.g., only uploading artifacts for a specific version).
* **Automation:** Using `github-script` to interact with the GitHub API (Welcome Bot).
* **Secrets:** Managing sensitive data securely.

## 📂 Workflow Breakdown

### 1. The Main CI/CD Pipeline (`.github/workflows/pipline.yml`)
This is the core workflow that simulates a real-world production pipeline.
* **Trigger:** Runs on `push` and `workflow_dispatch`.
* **Build & Test Job:** * Uses a **Matrix** to test across Node.js 18, 20, and 22.
    * Caches `npm` dependencies for speed.
    * Uploads the production build as an artifact (only for Node 20).
* **Deploy Job:** * Waits for `build-and-test` to finish.
    * Downloads the artifact and simulates a deployment.

### 2. Issue Welcome Bot (`.github/workflows/githubscript.yml`)
An automation workflow that interacts with users.
* **Trigger:** Runs when a new **Issue** is opened.
* **Action:** Uses JavaScript (`actions/github-script`) to automatically post a friendly comment thanking the user.

### 3. Secrets Management (`.github/workflows/envWorkflow.yml`)
A demonstration of security best practices.
* Shows how to securely access encrypted secrets using `${{ secrets.SUPER_SECRET }}` so they don't appear in logs.

## 🛠️ Technologies Used
* GitHub Actions
* Node.js
* npm
* JavaScript