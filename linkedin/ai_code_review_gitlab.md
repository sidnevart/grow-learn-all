# AI Code Review for GitLab

## LinkedIn Fields

**Project name:** AI Code Review for GitLab  
**Associated with:** T-Bank  
**Date:** 2025  
**Project URL:** https://sidnev.dev/projects/ai-code-review

## LinkedIn Description

AI-powered merge request review automation integrated with GitLab. The system analyzes code changes, summarizes merge requests, classifies issues by severity, and suggests fixes before human review.

• Business problem: senior engineers spent too much time on repetitive review feedback: style issues, missing tests, common bugs, error handling, and simple security concerns.
• Built a GitLab-integrated review workflow using Python, FastAPI, OpenAI, Docker, and GitLab API.
• Designed an MR analysis pipeline that turns diffs into structured review tasks and generates actionable feedback.
• Solved large-diff context limits by splitting changes into semantic chunks and running targeted prompts by file/change type.
• Reduced noisy AI output with severity classification, repository-specific rules, confidence checks, and human approval workflow.
• Added review summaries, issue categorization, suggested fixes, and developer feedback loops for continuous rule improvement.
• Result: saved 35% of review time and caught 120+ issues per week while keeping human reviewers in control.

## Short Version

Built an AI code review bot for GitLab MRs using Python, FastAPI, OpenAI, and GitLab API. It summarizes changes, classifies issues, suggests fixes, handles large diffs with chunking, and saved 35% of review time while catching 120+ issues/week.
