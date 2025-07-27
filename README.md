# 🚀 Website CI/CD Deployment Pipeline (GitHub Actions)

A complete CI/CD pipeline for deploying websites using GitHub Actions, with caching, testing, build artifacts, and reusable deployments.

## 🎯 Goal

To simulate a real-world DevOps pipeline suitable for production-grade environments with minimal tools — focusing on automation and clarity.

## 🔧 Tech Stack

- Node.js + npm
- GitHub Actions
- Docker (optional)
- Artifact storage (GitHub built-in)
- Render or AWS (optional for deployment)

---

## 🔄 Workflow Overview
Push to main

├── Lint Job

├── Test Job

│ └── Uploads test report on failure

├── Build Job (needs: test)

│ └── Uploads /dist as artifact

├── Deploy Job (needs: build)

│ └── Downloads /dist and deploys

└── Report Job (needs: [lint, deploy], runs only on failure)


---

## 🧪 Features Implemented

✅ Lint with `npm run lint`  
✅ Test with `npm run test` and result upload  
✅ Matrix testing across Node versions and OS  
✅ Dependency caching using `actions/cache`  
✅ Reusable deploy workflow with input/output  
✅ Failure reporting with `toJson(github)`  
✅ Output printing with `needs.deploy.outputs.result`  

---

## ⚙️ Usage

### 1. Push to `main` branch  
Triggers the entire pipeline.

### 2. Setup reusable workflow
Your `.github/workflows/reusable.yml` can be imported in other workflows via `uses`.

---

## 📁 File Structure
.github/workflows/
│

├── website-deployment.yml # Main full pipeline

├── use-reuse.yml # Workflow that calls reusable deploy

├── reusable.yml # Reusable deploy logic

└── matrix.yml # Cross-version build workflow


---

## 🌍 Live Deployment

_Not connected to a cloud provider yet, but can easily integrate with:_  
- Render.com  
- AWS S3 + CloudFront  
- Firebase Hosting
