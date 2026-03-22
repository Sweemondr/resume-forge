# Resume Forge

`resume-forge` is a resume-generation skill for AI coding agents. It turns one or more historical resumes plus a target job description into a one-page, ATS-friendly PDF resume generated through LaTeX.

## What It Does

- Guides the user through resume intake from multiple historical resume versions and a target JD
- Auto-infers resume configuration such as language, stage, paper size, seniority, and section order
- Merges experience, project, and skill data across resume versions with minimal conflict confirmation
- Rewrites bullets with a STAR-style structure while keeping every claim grounded in user-provided facts
- Enforces single-language consistency for bullets unless the JD explicitly requires bilingual output
- Compiles to PDF and blocks final delivery until the output passes a one-page self-check
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
2. Provide the target job description text or URL.
3. Let the agent infer the initial configuration.
4. Confirm only the uncertain or user-overridden fields.
5. Generate and refine the resume content.
6. Compile LaTeX to PDF and keep iterating until the resume is exactly one page.

## Expected Output

The skill writes intermediate files under `.claude-resume/` and treats the final deliverable as:

```text
.claude-resume/output/<RESUME_FILENAME>.pdf
```

`resume.tex` is considered an intermediate artifact and must not replace the final PDF delivery.

## Usage Notes

- Do not commit personal resume data or generated PDFs unless you intend to share them.
- The repository includes a `.gitignore` that ignores `.claude-resume/` and common LaTeX build artifacts.
- The skill is designed for resume tailoring, resume generation from scratch, and format conversion into a one-page PDF resume.

## Example Prompt

```text
Use the resume-forge skill to merge my two historical resumes with this backend engineer JD,
generate an ATS-friendly one-page Chinese PDF resume, and ask me only about ambiguous facts.
```
