# Kelvin Lamptey GitHub Profile README Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Create a world-class, dynamic GitHub Profile README (`README.md`) and automated contribution snake workflow for Kelvin N.O. Lamptey (`kelvin-lamptey`) reflecting the design, systems, and branding from the portfolio.

**Architecture:** 
- GitHub Profile README (`README.md`) leveraging dynamic SVG services (`readme-typing-svg`, `capsule-render`, `github-readme-stats`, `github-readme-streak-stats`, `github-readme-activity-graph`, `skillicons.dev`, and Shields.io badges).
- Automated GitHub Actions workflow (`.github/workflows/snake.yml`) running on a daily cron schedule using `Platane/snk` to generate snake-eating-commit-dots SVGs.

**Tech Stack:** Markdown, GitHub Actions CI/CD, SVG, Simple Icons, GitHub REST APIs.

---

### Task 1: Create GitHub Actions Workflow for Contribution Snake

**Files:**
- Create: `C:/Users/kelvi/Documents/Code/A/kelvin-lamptey/.github/workflows/snake.yml`

**Step 1: Write the workflow definition**
Configure a daily GitHub Actions cron + workflow_dispatch to generate both dark and light snake animations from `@kelvin-lamptey` contributions and push them to the `output` branch.

```yaml
name: Generate Contribution Snake

on:
  schedule:
    # Runs every 24 hours at midnight UTC
    - cron: "0 0 * * *"
  workflow_dispatch:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest
    permissions:
      contents: write
    steps:
      - name: Generate Snake SVG
        uses: Platane/snk/svg-only@v3
        with:
          github_user_name: kelvin-lamptey
          outputs: |
            dist/github-contribution-grid-snake.svg
            dist/github-contribution-grid-snake-dark.svg?palette=github-dark&color_snake=%232259ec&color_dots=%23161b22,%230e4429,%23006d32,%2326a641,%2339d353

      - name: Push Snake SVG to output branch
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

**Step 2: Verify syntax & directory structure**
Ensure `.github/workflows` directory exists and yaml is well-formatted.

---

### Task 2: Create the Executive GitHub Profile README.md

**Files:**
- Create: `C:/Users/kelvi/Documents/Code/A/kelvin-lamptey/README.md`

**Step 1: Write the full profile README structure**
The README includes:
1. **Header**: Dynamic Capsule Render Banner + SVG Typing Title with Electric Blue theme (`#2259ec`) + Visitor Counter.
2. **Executive Bio & Role Highlights**: Computer Science @ GCTU, Co-founder & CTO @ KENOL Tech, Yango STEM Fellow, building African tech infrastructure.
3. **The Commit Dots & Activity Section**:
   - Animated Contribution Snake (eating green dots)
   - Dynamic Commit Activity Graph (`ashutosh00710/github-readme-activity-graph`) with customized dark blue theme (`#2259ec` accent).
4. **GitHub Analytics & Metrics**:
   - `github-readme-stats` card (Stars, Commits, PRs, Issues, Contribution Rank).
   - `github-readme-streak-stats` card (Current Streak, Longest Streak, Total Contributions).
   - `top-langs` card (Most used programming languages).
5. **Categorized Tech Stack Badges**:
   - Languages: Go, TypeScript, JavaScript, Python, Java, PHP, HTML5, CSS3, SQL.
   - Frontend & Mobile: Vue.js, React, React Native, Expo, Next.js, Astro, HTMX, Tailwind CSS.
   - Backend & Databases: Node.js, Express, NestJS, Bun, PostgreSQL, Supabase, Prisma ORM, Django.
   - DevOps & Cloud: Docker, Linux, Git, GitHub Actions, Microsoft Azure, WordPress.
6. **Featured Systems & Open-Source Projects**:
   - KENOL Cloud (PaaS/SaaS)
   - SmartScript (AI Grading & Analytics)
   - TruMark (Federated Attendance & Azure Face)
   - Shinaa (Campus Key Management & Hall Scheduling)
   - TruMember (Club Management & SMS/Voice)
   - Shoot 'em Dead (Java/Processing Game)
7. **Social Links & Footprint**:
   - Interactive badge buttons linking to LinkedIn, WhatsApp, X/Twitter, YouTube, Portfolio Website, Instagram, Telegram.
8. **Subtle Footer / Quote**.

---

### Task 3: Review & Validation

**Step 1: Inspect README rendering and verify all links and image endpoints**
- Ensure all SVG generators, raw branch paths, and asset URLs are valid and functional.
- Validate dark-mode and light-mode responsiveness.

---
