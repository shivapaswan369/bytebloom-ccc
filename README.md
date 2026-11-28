# ByteBloom CCC — Study Garden

A bilingual (Hindi + English) CCC practice prototype with a pastel, student-friendly interface.

## Current prototype
- Homepage with separate Previous Papers, Chapter Practice, Repeated Concepts, and Leaderboard areas.
- All 10 CCC Revision 4 syllabus chapters available from the start.
- 190 bilingual practice questions: 50 starter questions, 40 paraphrased September 2026 memory-based recall concepts, and 100 new original syllabus-based questions in a separate `question-bank.js` file.
- Chapter practice filters by Normal / Medium / Hard and displays real available counts; one-question-at-a-time flow with answer explanations.
- A 100-question, 90-minute timed mock is enabled (MCQ-only; True/False items are not yet in the bank).
- Profile name + avatar picker.
- Local browser progress and local leaderboard demonstration.
- Responsive design for phone and desktop.

## Important limitations (not yet production)
- Question bank remains incomplete: 190 questions total, currently 17–23 per chapter; continue expanding toward 50 minimum and 100 target per chapter.
- Difficulty coverage is uneven: 8 Normal, 3 Hard, and 6–12 Medium per chapter (memory-based recall items are Medium).
- Starter questions are syllabus-based, not official NIELIT paper text.
- Previous-paper sets are partial research cards. Two third-party September 2026 recall collections (11 Sep and 15 Sep) have been paraphrased into 40 sample questions; these are not official papers or complete exam sets.
- Repeated-question area currently means common/recurrent concepts; no verified cross-paper frequency counts are claimed.
- Score/progress is local to one browser. Shared leaderboard, account login, and cross-device sync are NOT implemented.
- Timed 100-question practice is available, but it is MCQ-only and not a fully faithful exam format until True/False items and broader reviewed coverage are added.

## Official research sources
1. NIELIT CCC Revised Syllabus Revision 4, implemented 01 October 2023: https://nielit.gov.in/sites/default/files/headquarter/pdf/20231006_CCC_Revised_Syllabus.pdf
2. NIELIT CCC exam candidate instructions: https://www.nielit.gov.in/sites/default/files/InstructionsCCC.pdf
3. NIELIT public Old Question Papers archive: https://www.nielit.in/content/old-question-papers-0 — checked entries show O/A/B/C-level papers; this does not verify public CCC previous papers.

## Exam pattern verified from NIELIT instructions
- 100 objective questions / 100 marks
- 90 minutes
- MCQ and True/False question types
- No negative marking
- Questions randomly selected from a fixed question bank

## Syllabus chapters (Revision 4)
1. Introduction to Computer
2. Introduction to Operating System
3. Word Processing
4. Spreadsheet
5. Presentation
6. Introduction to Internet and WWW
7. Email, Social Networking and e-Governance
8. Digital Financial Services
9. Overview of Future Skills and Cyber Security
10. Introduction to Artificial Intelligence

## Security plan before public/shared use
The static prototype must not be presented as secure multi-user production. Production should use a trusted auth provider and database with:
- password hashing handled by auth provider (never store raw passwords)
- public profile limited to username/avatar
- private per-user attempts and progress
- Row-Level Security (RLS) for database access
- server-side score validation / controlled score writes
- rate limits, input validation, abuse controls
- no service-role keys in browser code
- minimal retention and a cleanup policy
- HTTPS and backups

## Deployment
This repository is the deployed project source for the project site: `https://shivapaswan369.github.io/bytebloom-ccc/`. GitHub Pages must publish from the repository's configured branch/root. Confirm deployment status in **Settings → Pages** and the Actions tab after each commit.

## Current implementation status
- Chapter practice now validates requested question counts against the number actually available in that chapter.
- Local-storage reads now recover from malformed/corrupted JSON instead of crashing on load.
- Quiz question shuffling uses Fisher–Yates rather than a biased random-sort method.
- Profile usernames are sanitized before saving.
- Still not implemented: real accounts/login, server-side student activity tracking, shared leaderboard, secure cloud progress, True/False mock items, and daily contest UI. Daily contest feature also remains to be implemented; scheduled content updates do not by themselves create a contest UI.
