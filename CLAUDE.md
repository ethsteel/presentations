# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This repository contains presentation materials for the STEEL Team (Specifications and Testing for the Ethereum Execution Layer). The primary content is RevealJS-based presentations created using HackMD and stored as Markdown files.

## Repository Structure

- `YYYY-MM-DD_event-name/` - Date-prefixed directories for each presentation
  - `slides.md` - Main presentation content in Markdown format with RevealJS configuration
  - `img/` - Images and assets for the presentation
- Each presentation follows HackMD/RevealJS format with YAML frontmatter configuration

## Working with Presentations

### Slide Format
- Presentations use Markdown with RevealJS slideOptions in YAML frontmatter
- Horizontal slide breaks: `---`
- Vertical slide breaks: `----` (if needed)
- Custom CSS styling included in `<style>` blocks within slides

### Image References
- Images must use GitHub permalink URLs with `?raw=true` suffix for HackMD compatibility
- Cannot use relative paths due to HackMD limitations
- Format: `https://github.com/ethsteel/presentations/blob/[commit-hash]/[path-to-image]?raw=true`

### HackMD Integration
- Presentations are linked to HackMD for live editing and presentation
- Changes from GitHub need manual pulling in HackMD interface
- VS Code preview available with `vscode-reveal` extension

## Development Workflow

When working with presentation content:
1. Edit slides.md files directly in repository
2. Use absolute GitHub URLs for images (with ?raw=true)
3. Test slide formatting with VS Code reveal extension if available
4. Manual sync required in HackMD after pushing changes

## Key Considerations

- This is a documentation/presentation repository with no build processes
- Focus on content clarity and proper RevealJS formatting
- Maintain consistent directory naming with date prefixes
- Ensure image URLs are accessible from HackMD environment