# Resume Forge

`resume-forge` is a resume-generation skill for AI coding agents. It turns one or more historical resumes plus either a user-provided JD or agent-discovered target jobs into one or more one-page, ATS-friendly PDF resumes generated through LaTeX.

## What It Does

- Guides the user through resume intake from multiple historical resume versions and either a target JD or an agent-led job search flow
- Auto-infers resume configuration such as language, stage, paper size, seniority, and section order
- Supports tailor/optimize, from-scratch, format-conversion, and quick-edit workflows
- Uses agent-agnostic confirmation patterns: structured prompts when available, plain-text fallback otherwise
- Can search for 3-6 suitable jobs, provide recommendation reasons plus job links, and wait for user confirmation before tailoring
- Merges experience, project, and skill data across resume versions with minimal conflict confirmation
- Rewrites bullets with a STAR-style structure while keeping every claim grounded in user-provided facts
- Enforces single-language consistency for bullets unless the JD explicitly requires bilingual output
- Compiles to PDF and blocks final delivery until the output passes a one-page self-check
- Stops auto-compression gracefully when further shrinking would damage relevance or readability
- Applies resume filename rules for campus/intern and experienced candidates

## Repository Structure

- `SKILL.md`: the core skill definition and workflow
- `RESUME_TEMPLATE.tex`: one-page LaTeX resume template
- `STYLE_GUIDE.md`: output constraints and self-check rules
- `README.md`: repository overview

## Key Guarantees

- PDF-only final delivery
- Strict one-page output
- ATS-friendly formatting
- Truth-only resume content
- Minimal, selective confirmation when information is ambiguous

## Typical Workflow

1. Provide one or more historical resumes.
2. Either provide the target job description text/URL or let the agent search for suitable jobs.
3. Confirm one or more target jobs.
4. Let the agent infer the initial configuration.
5. Confirm only the uncertain or user-overridden fields.
6. Generate and refine the resume content for each confirmed job.
7. Compile LaTeX to PDF and keep iterating until each resume is exactly one page.

## Expected Output

The skill writes intermediate files under `.claude-resume/` and treats the final deliverable as:

```text
.claude-resume/output/<RESUME_FILENAME>.pdf
```

If the user confirms multiple target jobs in one run, the skill should place each tailored version under its own job folder:

```text
.claude-resume/output/<JOB_SLUG>/<RESUME_FILENAME>.pdf
```

`resume.tex` is considered an intermediate artifact and must not replace the final PDF delivery.

## Usage Notes

- Do not commit personal resume data or generated PDFs unless you intend to share them.
- The repository includes a `.gitignore` that ignores `.claude-resume/` and common LaTeX build artifacts.
- The skill is designed for resume tailoring, resume generation from scratch, and format conversion into a one-page PDF resume.

## Example Prompt

```text
Use the resume-forge skill to review my historical resumes, search for the best backend roles for me,
show each recommended job with a reason and link, let me choose which ones to target,
and then generate a one-page tailored PDF resume for each confirmed role.
```
