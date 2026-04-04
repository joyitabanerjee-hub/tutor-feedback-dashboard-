# Tutor Feedback Dashboard — Planning Document

**Date:** 2026-03-09
**Status:** Planning phase

## Data Source

Google Sheets Form Responses: [Link](https://docs.google.com/spreadsheets/d/1KPSez_Qc0SDWbPZkLzzs1oBkuYgnwqHZkXX3dwnpBgs/edit?gid=1190754995#gid=1190754995)

Local CSV copy: `form_responses.csv`

## Data Summary

- **56 responses** from tutors
- **4 grades**: Grade 1 (20), Grade 2 (6), Grade 3 (19), Grade 4 (11)
- **13 chapters** across grades
- **52 unique chapter-lesson pairs**

### Form Structure (32 columns)

| Column | Field | Type |
|--------|-------|------|
| 0 | Timestamp | Date |
| 1 | Name | Text (tutor name) |
| 2 | Phone Number | Text |
| 3 | Grade | Number (1-4) |
| 4-21 | Chapter Name / Lesson Name (up to 9 pairs) | Text |
| 22 | By the end of the learning section, most students will: | Multi-select / Text |
| 23 | Do the learning sections have enough examples and guided practice? | Text |
| 24 | The learnings: | Multi-select (engaging, boring, etc.) |
| 25 | The learning sections are: | Multi-select (right length, too long, etc.) |
| 26 | The language used for learnings: | Multi-select |
| 27 | Additional suggestions for improving learning section | Free text |
| 28 | The questions in the practice section are: | Multi-select |
| 29 | Additional suggestions for improving practice section | Free text |
| 30 | Rate the overall lesson from 1 to 5 | Rating scale |
| 31 | Additional suggestions for improving the lesson | Free text |

### Rating Distribution

| Rating | Count | % |
|--------|-------|---|
| 5 - Excellent | 26 | 46% |
| 4 - Very Good | 22 | 39% |
| 3 - Satisfactory | 7 | 13% |
| 2 - Needs Improvement | 1 | 2% |

---

## Discussion Log

### Session 1 — 2026-03-09

**Questions asked:**

1. Granularity? → **Lesson-level, aggregated to chapter-level**
2. Decisions driven? → **Widget-level if glaring + multiple reports; otherwise draw principles. High-level summary per lesson. Flag too-long/too-short for rework.**
3. Audience? → **Content team + leadership (high-level insights)**
4. Refresh cadence? → **Auto-refresh every Monday from Google Sheet**
5. Free-text analysis? → **Yes — auto-categorize themes, sentiment, top recurring suggestions**
6. Grade-wise comparison? → **Yes**
7. Format? → **Web-based dashboard with link, downloadable as PDF**
8. Tutor leaderboard? → **Yes — visual showing tutors with most feedback submissions**

**Decisions confirmed:**

- Deduplicate: if same tutor reviewed same lesson twice, keep only latest
- 3 duplicates found: Mehak Hemnani (Number System), Mamta Baid (Mental Math), Shalini Lalwani (Magic with More Numbers)
- Tutor name normalization needed: "mehak hemnani" / "Mehak Hemnani" / "mehal", "Rajiv Kumar" / "Rajiv", "Monika Agrawal" / "Monika", "Manesha Kathpalia" / "MAnesha kathpalia", "aashina chhabra" / "AashinaChhabra" / "Aashina Chhabra"

**Data insights from analysis:**

- 15 unique tutors (after normalization: ~11)
- Top contributors: Shalini Lalwani (6), Mamta Baid (6), Bhavna Jain (5), Aashina Chhabra (5+1+1=7), Monika Agrawal (5+1=6)
- 84% of learnings rated "engaging"; 16% "need more fun"
- 88% learning sections "just right length"; 7% "too short"; 5% "too long"
- 91% language "explains well"; edge cases: text heavy, confusing context
- Top free-text themes: fun (11), video issues (9), difficult (5), drag-and-drop (3), visual needs (3)

**Resolved — Tutor name mapping (confirmed same person):**

| Raw names | Normalized |
|-----------|-----------|
| mehak hemnani, Mehak Hemnani, mehal | Mehak Hemnani |
| Rajiv Kumar, Rajiv | Rajiv Kumar |
| Monika Agrawal, Monika | Monika Agrawal |
| Manesha Kathpalia, MAnesha kathpalia | Manesha Kathpalia |
| aashina chhabra, AashinaChhabra, Aashina Chhabra | Aashina Chhabra |

**After normalization: 11 unique tutors**

**Resolved (Session 1 continued):**

- Grade filter: Yes, filterable by grade
- Dashboard structure: Confirmed (6 sections as proposed)
- Principles: Auto-generate from recurring themes
- PDF export: Full dashboard

**Final Dashboard Spec:**

### Section 1: Overview
- Total responses, unique tutors, grades covered
- Average rating + rating distribution (donut/bar chart)
- Quick stats: % engaging, % right length, % adequate examples

### Section 2: Grade-wise View
- Grade filter tabs (Grade 1–4)
- Per grade: chapter cards with avg rating, engagement %, length flags, response count
- Grade-level comparison bars (engagement, length, language across grades)

### Section 3: Chapter → Lesson Drill-down
- Click chapter → see all lessons
- Per lesson: rating, learning engagement, practice quality, length flag
- Summarized feedback from all tutors (1 or more sources)

### Section 4: Feedback Themes
- Auto-categorized from free text (drag-and-drop, video, language, etc.)
- Frequency bars, filterable by grade/chapter
- Word cloud or tag cloud of top keywords

### Section 5: Action Items & Principles
- Lessons flagged: too long/short, low ratings, repeated complaints
- Specific feedback quotes as evidence
- Auto-generated principles from recurring patterns (e.g., "Grade 1: Prefer click/tap over drag-and-drop")

### Section 6: Tutor Contributions
- Bar chart / leaderboard of tutors by submission count
- Grades and chapters each tutor covers

### Technical
- Web-based (HTML/JS), single file, hosted locally or shareable link
- Auto-refresh from Google Sheet every Monday
- Full PDF export via browser print / html2pdf
- Data: CSV parsed client-side, or pre-processed JSON

### Section 7: Tutor Communication
- Auto-generated summary of all feedback
- Top 2-3 actions being taken (drawn from top themes)
- Most active tutors per week (bar chart + weekly spotlight)
- Exportable as standalone document for sharing with tutors
- Saved as `tutor-feedback-summary-week{N}.md`

**Status: Built — v1 complete**
