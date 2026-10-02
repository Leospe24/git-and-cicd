# Stage 3: CI/CD Automation Theory

## 1. What is CI/CD?
- **CI (Continuous Integration):** Automating checks (linting, testing, security scans, building) every time you push code to a repository. The goal is to catch bugs *before* they can reach production.
- **CD (Continuous Deployment / Delivery):** Automatically taking that tested code and pushing it to a live server, AWS, or a Docker registry.

## 2. The "Runner"
When you push code, GitHub automatically spins up a temporary, blank Linux server in the cloud. This server is called a **Runner**. It lives for just a few minutes to execute your tasks, and then it is immediately destroyed.

## 3. The Instruction Manual (YAML)
How does the Runner know what to do? You must write an instruction manual in a `.yml` (YAML) file. 
GitHub only looks for these manuals in a very specific, hidden folder at the root of your project: `.github/workflows/`.

## 4. Anatomy of a Workflow
Every CI/CD pipeline in GitHub Actions is built using 3 main blocks:

1. **Triggers (`on`):** WHEN should this pipeline run? 
   *(e.g., `on: push` to the `main` branch, or when a Pull Request is opened).*
2. **Jobs:** WHAT is the overarching objective? 
   *(e.g., `test-code`, `build-docker-image`). A single pipeline can have multiple jobs running in parallel.*
3. **Steps:** EXACTLY how do we achieve the objective? 
   *(e.g., Step 1: Download code, Step 2: Install Node.js, Step 3: Run `npm test`).*
