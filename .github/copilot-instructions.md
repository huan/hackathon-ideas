# Hackathon Ideas Documentation Repository

**ALWAYS reference these instructions first and fallback to search or bash commands only when you encounter unexpected information that does not match the info here.**

This repository contains curated hackathon project ideas and research concepts by Huan Li. It is a documentation-only repository containing markdown files with detailed project specifications, runbooks, and research proposals.

## Repository Structure and Navigation

The repository contains the following key files:
- `README.md` - Simple repository description
- `ad-signal.md` - Comprehensive hackathon runbook for building "AdSignal" project (418 lines)
- `llm-in-the-loop-genetic-prompt-optimization-for-hard-resoning-tasks.md` - Research paper proposal on LLM prompt optimization (263 lines)

### Common Repository Contents

```bash
# Repository root structure
ls -la /home/runner/work/hackathon-ideas/hackathon-ideas
.
..
.git/
.github/
README.md
ad-signal.md
llm-in-the-loop-genetic-prompt-optimization-for-hard-resoning-tasks.md
```

## Working Effectively

### Initial Setup and Validation
- This is a documentation-only repository - there are NO build systems, dependencies, tests, or applications to run
- Install markdown linting tools: `npm install -g markdownlint-cli`
- Validate repository status: `git --no-pager status`
- Check recent commits: `git --no-pager log --oneline -5`

### Markdown Validation and Linting
- **ALWAYS** run markdown linting before making changes: `markdownlint *.md`
- The existing files have multiple linting issues (line length violations, heading structure issues, etc.) - this is normal
- When editing existing files, try to maintain consistency with existing style rather than fixing all linting issues
- For new files, follow proper markdown conventions

### Content Analysis and Understanding
- Use `wc -l *.md` to see file sizes
- Use `grep -n "^#" <filename>.md` to see document structure and headings
- Use `head -20 <filename>.md` to quickly preview file contents
- The documents contain:
  - **ad-signal.md**: Complete hackathon runbook with architecture, implementation plans, data contracts, and demo scripts
  - **llm-research.md**: Academic paper structure with abstract, methodology, experiments, and results

## Common Tasks

### Reading and Understanding Documents
- **AdSignal project**: A system that analyzes ads shown in iOS apps to determine user interests and trigger personalized notifications
- **LLM research**: Genetic algorithm approach to optimizing prompts for hard reasoning tasks
- Both documents contain technical implementation details, code snippets, and structured methodologies

### Adding New Ideas
- Create new markdown files following the existing frontmatter pattern:
```yaml
---
title: "Your Project Title"
author: "Huan Li"
date: YYYY-MM-DD
tags:
  - relevant-tag
---
```

### Git Operations
- Check status: `git --no-pager status`
- View diffs: `git --no-pager diff`
- The repository uses standard git workflow
- Remote URL: https://github.com/huan/hackathon-ideas

### Validation Steps
- **ALWAYS** run `markdownlint *.md` before committing changes
- Verify markdown syntax: `head -50 <new-file>.md` to check formatting
- Count lines for reference: `wc -l *.md`
- Check heading structure: `grep -n "^#" <filename>.md`

## Important Notes

### No Build/Test Infrastructure
- **DO NOT** look for package.json, Makefile, or build scripts - they don't exist
- **DO NOT** try to run applications or servers - this is documentation only
- **DO NOT** install project dependencies - there are none

### Content Focus
- Projects are focused on innovative technology applications
- Documents include detailed technical specifications
- Both existing projects involve mobile/web applications with backend services
- Code examples are provided as reference implementations, not executable code

### Documentation Standards
- Maintain consistent heading hierarchy
- Include technical diagrams using mermaid syntax where appropriate
- Provide comprehensive implementation details
- Include data contracts and API specifications
- Add demo scripts and testing procedures

## Time Expectations
- Markdown linting: ~5 seconds for all files
- Reading/analyzing documents: 2-5 minutes per major section
- Adding new content: Varies based on complexity, typically 10-30 minutes for structured ideas

## Repository Insights
- Total documentation: ~683 lines across 3 files
- Primary focus: Mobile app development, AI/ML applications, and research concepts
- Style: Technical specifications with implementation roadmaps
- Audience: Developers and researchers looking for hackathon project ideas

Remember: This repository is purely educational and conceptual - focus on documentation quality, technical accuracy, and clear communication of ideas rather than executable code.
