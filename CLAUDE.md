# Kedro Case Study - Claude Code Guide

This repository contains a Slidev presentation for a Product Management case study about Kedro's configuration evolution.

## Project Structure

```
kedro-case-study/
├── slides.md              # Main presentation file (uses src directives)
├── slides/                # Individual slide files
│   ├── 01-intro.md        # What is Kedro
│   ├── 02-why.md          # Why we built it
│   ├── 03-investment.md   # Investment & commercial value
│   ├── 04-problem.md      # Key problem (configuration overhead)
│   ├── 05-approach.md     # How we approached the solution
│   ├── 06-impact.md       # Tracking impact & success
│   └── 07-commercial.md   # Commercial model considerations
├── package.json           # Node.js dependencies and scripts
├── brief.md              # Interview case study requirements
├── notes.md              # Working notes
└── references.md         # Reference materials
```

## Available Commands

### Development

- `npm run dev` - Start Slidev development server with hot reload
- `npm run build` - Build presentation for production
- `npm run export` - Export presentation as PDF

### File Operations

- Edit individual slides in the `slides/` directory
- Main presentation flow is controlled in `slides.md` using `src` directives
- Each slide file can be worked on independently

## Presentation Overview

This case study covers:

1. **Introduction to Kedro** - What it is and who uses it
2. **Problem Context** - Why we built it and what problems it solves
3. **Investment Analysis** - Resources invested and commercial value
4. **Key Challenge** - Configuration overhead as the main user pain point
5. **Solution Approach** - Research, telemetry, and user testing methodology
6. **Impact Measurement** - Metrics and success tracking
7. **Commercial Model** - Revenue streams and go-to-market strategy

## Working with Slides

### Adding New Slides

1. Create new `.md` file in `slides/` directory
2. Add `src` directive to main `slides.md` file:
   ```markdown
   ---
   src: ./slides/new-slide.md
   ---
   ```

### Slide Structure
Each slide file should contain:

- Slide content in markdown
- Optional frontmatter for layout/styling
- Speaker notes in HTML comments at the end

### Common Layouts

- Default: Standard slide
- `layout: center` - Centered content
- `layout: image-right` - Image on right, content on left
- `class: text-center` - Center-aligned text

## Development Workflow

1. **Start development server**: `npm run dev`
2. **Edit slides**: Modify files in `slides/` directory
3. **Preview changes**: Browser auto-refreshes on file save
4. **Build for presentation**: `npm run build` when ready
5. **Export to PDF**: `npm run export` for sharing

## Presentation Tips

- Use presenter mode (press `P`) to see speaker notes
- Navigate with arrow keys or space bar
- Press `F` for fullscreen mode
- Press `O` for slide overview
- Press `D` for dark mode toggle

## File Editing Notes

- `slides.md` controls the overall presentation flow
- Individual slide files are focused on content only
- Transitions and layouts can be specified in the main file
- Speaker notes should be added as HTML comments in each slide file