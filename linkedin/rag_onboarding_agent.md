# RAG Onboarding Agent

## LinkedIn Fields

**Project name:** RAG Onboarding Agent  
**Associated with:** T-Bank  
**Date:** 2025  
**Project URL:** https://sidnev.dev/projects/rag-onboarding

## LinkedIn Description

RAG-based knowledge assistant for onboarding new backend engineers. The assistant answers questions from internal documentation, shows retrieved sources, tracks onboarding progress, and helps interns move through team-specific setup faster.

• Business problem: new interns and engineers faced scattered documentation, inconsistent onboarding, and frequent dependency on senior engineers for repeated questions.
• Built a chat-based RAG assistant using Python, LangChain, FastAPI, PostgreSQL, Redis, and React.
• Designed a retrieval pipeline with document chunking, source retrieval, context-aware answers, and confidence scoring.
• Added onboarding checklist tracking so users could move from Q&A to structured progress.
• Reduced hallucination risk by grounding answers in retrieved documents and exposing source context to the user.
• Added fallback behavior for low-confidence answers, missing retrieval results, and cases where a human mentor should be involved.
• Result: reduced onboarding time by 40% and senior developer interruptions by 60%.

## Short Version

Built a RAG onboarding assistant with LangChain, FastAPI, PostgreSQL, Redis, and React. It retrieves internal docs, cites sources, tracks onboarding progress, and reduced onboarding time by 40% plus senior developer interruptions by 60%.
