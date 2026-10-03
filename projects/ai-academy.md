# Fazaian AI Academy

**Status: under development.** Core workflows are implemented and tested; the application is not deployed to students and is not presented as a finished product.

---

## Overview

An AI-assisted student learning application currently under development, with core textbook, chapter, quiz, results and progress workflows implemented.

A student opens a book for their class and subject, picks a chapter, generates a practice quiz from that chapter's content, answers it, sees the result, and watches their progress build up over time. The study planner shows what is ahead.

This is my own project rather than a client engagement.

## Problem

Students revising from a textbook have the material but no way to test themselves against it. Practice questions either do not exist for the chapter in front of them, or come from a different edition and a different syllabus.

The usual fix is a question bank, which goes stale and never covers everything. The alternative is generating practice questions from the approved textbook content itself, so what the student is tested on is what they are actually studying.

## My role

Sole developer — data model, application, AI integration, testing and debugging.

## Implemented functionality

Built, tested and working:

- Book listing by class and subject
- Chapter selection within a book
- AI quiz generation from chapter content
- Quiz submission and answer handling
- Quiz results
- Student progress page
- Study planner showing chapters
- Textbook / PDF content workflow feeding the question generation
- Supabase-backed data structure behind all of the above
- OpenAI integration through Supabase Edge Functions

## Technology

Expo / React Native · Supabase · Supabase Edge Functions · OpenAI · PDF and textbook content workflow

## Development challenges

- **Getting usable questions out of textbook content.** Raw extracted text is not the same as teachable content, and question quality depends entirely on what reaches the model.
- **Structuring the data so content, chapters, quizzes, results and progress stay connected** — a quiz result is meaningless if it cannot be tied back to the chapter it came from.
- **Keeping API keys out of the client.** A mobile application cannot hold an OpenAI key.
- **Testing a multi-step flow end to end** — book, chapter, generation, submission, result, progress — where a failure at any step looks the same from the screen.

## Solutions and work performed

- Built the content workflow so chapter material is prepared before it reaches the model, rather than sending raw extraction
- Designed the Supabase schema around the relationships the progress tracking needs, not just the screens
- Moved the OpenAI calls server-side into Supabase Edge Functions, so no key is present in the application
- Worked through the full flow repeatedly in a development build, debugging each step in isolation
- Authentication was temporarily bypassed in that development build so the flows could be exercised directly. **That is a development-stage shortcut, not the design** — authentication is restored before anything is released, and the application is not deployed in that state

## Current status

Under active development. Core workflows implemented and tested; no deployment to students, no user base, and no usage, performance or revenue figures — none have been measured and none are claimed.

## Planned development

Not built. Listed to show the intended direction:

- AI-generated daily, weekly and monthly study planning
- Exam and target-date based study schedules
- Notifications for late or pending study
- Parent and guardian linkage
- Expanded student progress monitoring
- Group discussion, with child-safety moderation, personal-contact-information blocking and unsafe-language moderation
- Past papers module, with student uploads and an admin approval workflow
- Expanded assignments
- Additional subjects, classes and books
- Additional administrative functionality

The child-safety work is listed as a requirement of the discussion feature rather than an add-on. A student discussion space without moderation is not a feature I would ship.

## Skills demonstrated

AI application development · React Native / Expo · Supabase and database-backed workflows · serverless functions · OpenAI integration · schema design · debugging multi-step flows · product thinking · education technology · structured feature planning

## Privacy and security note

No Supabase project URL, API key, OpenAI key, database credential, token, internal identifier, storage link, configuration value or test account appears here or anywhere in this portfolio. No student data exists in the project, and none would be published if it did.
