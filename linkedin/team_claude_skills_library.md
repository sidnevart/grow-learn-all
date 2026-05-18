# Team Claude Skills Library

## LinkedIn Fields

**Project name:** Team Claude Skills Library  
**Associated with:** T-Bank  
**Date:** 2025  
**Project URL:** https://sidnev.dev/projects/claude-skills-library

## LinkedIn Description

Internal Go-based platform that lets teams publish, share, and reuse Claude skills across the entire engineering organization. Instead of every team building custom AI prompts from scratch, engineers pull pre-built skills from a shared library — cutting duplication, standardizing quality, and shipping AI features in hours instead of weeks.

• Business problem: teams were duplicating Claude skill development — similar prompts, context windows, and tool integrations were being rebuilt independently across squads, wasting time and producing inconsistent AI behavior.

• Built a Go-based skill registry and runtime that packages Claude prompts, context, and tool bindings into versioned, reusable modules any team can deploy.

• Designed the skill schema to include prompt templates, dynamic context injection, retry policies, and standardized output formats — so skills behave predictably across different services.

• Added a deployment pipeline that takes a skill definition and spins up a containerized service endpoint, making a new AI capability production-ready without touching infrastructure code.

• Embedded a token-economy mechanism into the platform — a one-command installable kit of hooks and CLAUDE.md rules that automatically compresses expensive Claude operations (git diffs, tree listings, test reports, logs) and cuts token consumption by ~60%. Proven on production codebases: −53% tokens per task, −66% session cost, 38% cache hit ratio.

• Scaled the library to 600+ skills shared across the bank, from code review assistants to data analysis copilots.

• Demonstrated the platform's speed in a live demo: spun up the full project, deployed the runtime, and built a working intern task-tracking and management app — all in 40 minutes.

• Result: eliminated skill duplication, standardized AI behavior across teams, and reduced time-to-production for new AI features from weeks to hours.

## Short Version

Built a Go-based internal platform for publishing and reusing Claude skills across a bank's engineering org. The library now holds 600+ skills, includes an automatic token-economy kit that cuts AI costs by ~60%, and ships AI features in hours. Demonstrated end-to-end delivery by deploying the platform and building a working intern management app in 40 minutes.
