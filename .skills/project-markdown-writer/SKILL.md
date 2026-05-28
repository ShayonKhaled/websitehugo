---
name: project-markdown-writer
description: Write project markdown posts with complete sections. Use when creating new project files with Overview, Problem, What I built, How I built it or Tech stack, Results, and Link.
---

# Project Markdown Writer

Create publish-ready project markdown files with all required sections in content/projects.

## Sections

1. Overview
2. Problem
3. What I built
4. How I built it or Tech stack (choose one based on context)
5. Results
6. Link

## Collect

1. Project title
2. One-line description
3. Timeframe (e.g., May 2024 - Aug 2024)
4. Tags
5. Build details and decisions
6. Measurable results or qualitative outcomes
7. GitHub or project URL

Ask follow-ups only for missing critical fields.

## File Placement

1. Save in content/projects/
2. Filename: kebab-case from title
3. One project per file

## Front Matter Template

```
---
title: "<Project Title>"
description: "<One-line summary>"
date: "<YYYY-MM-DD>"
timeframe: "<Mon YYYY - Mon YYYY>"
draft: false
tags:
  - <tag-1>
  - <tag-2>
params:
  project_url: "<GitHub URL or project URL>"
---
```

## Body Template

```
## Overview

<What the project does and why it matters.>

## Problem

<Gap or issue it solves.>

## What I built

- <Key feature>
- <Key feature>
- <Key feature>

## How I built it

(Use for process-focused projects: design iteration, prototyping, methodology)

- <Step or decision>
- <Technology choice>
- <Lesson learned>

OR

## Tech stack

(Use for technology-focused projects: tools, libraries, frameworks, hardware)

- <Language or framework>
- <Hardware or service>
- <Development tool>

## Results

- <Metric or impact if available>
- <Outcome or observation>

## Link

GitHub repository: <URL>

Or:

Project URL: <URL>
```

## Decision Rules

1. **How I built it vs Tech stack**: "How I built it" for projects emphasizing process or iteration. "Tech stack" for projects emphasizing tools and technology.
2. **Results**: One metric if available (time saved, performance gain). Otherwise qualitative.
3. **Voice**: First-person throughout ("I built", "I discovered").
4. **No fluff**: Concise, direct language. No em dashes. Bullet points preferred.
5. **Link**: GitHub URL if available, otherwise project or live demo URL.
6. All six sections required, none omitted.

## Checklist

1. All six sections present
2. Section 4 is either "How I built it" or "Tech stack", not both
3. First-person voice throughout
4. Timeframe formatted correctly
5. One metric in Results if possible, else qualitative
6. No em dashes or fluff
7. YAML front matter valid

## Example Prompts

1. Write a project markdown file for my gesture sensor controller.
2. Rewrite this draft with all required sections.
3. Create project markdown from these notes.
