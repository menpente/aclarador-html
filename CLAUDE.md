# CLAUDE.md - AI Assistant Guide for Aclarador HTML

This document provides essential context for AI assistants working on this codebase.

## Project Overview

**Aclarador HTML** is a single-file web application that analyzes and rewrites text documents using "Plain Language" principles from the Aragonese Government Style Manual. It uses a multi-agent architecture powered by the Groq API (Llama 3.3 70B model).

### Key Characteristics
- **Single HTML file**: All code (HTML/CSS/JS) in `aclarador-html-tool.html` (~1,561 lines)
- **Zero build process**: No bundlers, transpilers, or package managers needed
- **Browser-based**: Uses File System Access API for folder/file selection
- **Privacy-first**: Only text content is sent to the API; all other processing is local
- **Language**: UI and documentation are in Spanish

## Repository Structure

```
/
├── aclarador-html-tool.html    # Main application (53 KB)
├── README-aclarador-html.md    # User documentation (Spanish)
├── LICENSE                     # Apache 2.0
└── CLAUDE.md                   # This file
```

## Architecture

### Multi-Agent System

The application implements 6 specialized agents plus a coordinator:

| Agent | Purpose | Key Methods |
|-------|---------|-------------|
| `AnalyzerAgent` | Text classification, issue detection, agent routing | `classifyText()`, `detectIssues()`, `recommendAgents()` |
| `RewriterAgent` | Main rewriting using Groq API | `rewriteText()` - calls external LLM |
| `GrammarAgent` | Grammar and punctuation checking | `checkGrammar()`, `detectRepeatedWords()` |
| `StyleAgent` | Readability and style analysis | `findStyleIssues()`, `calculateReadabilityScore()` |
| `SEOAgent` | SEO optimization analysis | `analyzeSEO()`, `analyzeWordFrequency()` |
| `ValidatorAgent` | Final quality assurance | `validateImprovements()`, `calculateQualityScore()` |
| `AgentCoordinator` | Orchestrates all agents | `processText()` |

### Code Organization in HTML File

```
Lines 1-17:      HTML head, external libraries (Mammoth.js, PDF.js)
Lines 18-451:    CSS styling (modern flexbox/grid, responsive)
Lines 454-500:   HTML markup (UI structure)
Lines 502-1559:  JavaScript
  - Global state variables
  - System prompt (SYSTEM_PROMPT constant)
  - BaseAgent class (abstract base)
  - Six agent implementations
  - AgentCoordinator class
  - File system functions
  - UI rendering functions
  - Initialization code
```

## Development Guidelines

### Making Changes

1. **Edit the single HTML file directly** - no build step required
2. **Test in browser** - open file locally or via web server
3. **Browser requirements**: Chrome/Edge 86+, Firefox 111+ (experimental), Safari 15.2+ (partial)

### Code Conventions

- **ES6+ JavaScript**: Uses classes, async/await, arrow functions
- **No frameworks**: Vanilla JS throughout
- **HTML escaping**: Always use `escapeHtml()` for user content
- **Error handling**: Wrap API calls in try-catch blocks
- **Comments**: Use `// ========== Section Name ==========` for major sections

### Key Functions to Know

```javascript
// File handling
selectFolder()              // Opens folder picker
selectFiles()               // Opens file picker
readFileContent(file)       // Reads file content (handles DOCX, PDF, text)

// Processing
processFiles()              // Main entry point for analysis
coordinator.processText()   // Runs text through all agents

// UI
renderFiles()               // Updates file list display
renderResults()             // Shows analysis results
downloadFile(filename, content)  // Generates download link
```

### API Integration

- **Endpoint**: `https://api.groq.com/openai/v1/chat/completions`
- **Model**: `llama-3.3-70b-versatile`
- **API key**: Stored in `localStorage.getItem('groq_api_key')`

### Plain Language Principles (Core Rules)

1. **One idea per sentence** - Maximum 30 words
2. **Active voice** - Avoid passive constructions
3. **Common vocabulary** - Simple, precise words
4. **Strategic punctuation** - Improve clarity
5. **Remove redundancy** - Concise text
6. **Avoid jargon** - Accessible language

## External Dependencies

All loaded via CDN (no npm/yarn):

| Library | Version | Purpose |
|---------|---------|---------|
| Mammoth.js | 1.6.0 | DOCX file parsing |
| PDF.js | 3.11.174 | PDF text extraction |

## Supported File Types

Text-based: `.txt`, `.md`, `.html`, `.css`, `.js`, `.json`, `.xml`, `.csv`, `.log`
Documents: `.docx`, `.pdf`

## Common Tasks

### Adding a New Agent

1. Create class extending `BaseAgent` (after line 600)
2. Implement `async process(text)` method returning object with `success`, `data`, `error`
3. Register in `AgentCoordinator.constructor()` agents array
4. Update `AgentCoordinator.processText()` to use new agent

### Modifying the System Prompt

Edit the `SYSTEM_PROMPT` constant (around line 520). This controls how the Llama model rewrites text.

### Changing UI Styles

All CSS is in the `<style>` block (lines 18-451). Uses CSS custom properties where applicable.

### Adding File Type Support

1. Update `readFileContent()` function
2. Add MIME type handling if needed
3. Consider adding library for parsing (like Mammoth for DOCX)

## Testing

No automated tests exist. Manual testing process:

1. Open `aclarador-html-tool.html` in browser
2. Enter Groq API key
3. Select folder with test documents
4. Select files and run analysis
5. Verify results show before/after comparison

## Troubleshooting

| Issue | Solution |
|-------|----------|
| Folder picker doesn't appear | Use Chrome/Edge (Firefox needs flag) |
| API errors | Check Groq API key validity and rate limits |
| DOCX not parsing | Check Mammoth.js CDN availability |
| PDF extraction empty | Some PDFs have image-only content |

## Git Workflow

- Main development branch: Check current branch before pushing
- Commit messages: Descriptive, in English preferred
- No CI/CD configured - manual deployment

## Notes for AI Assistants

- **Language**: Code comments are in English, UI text and documentation are in Spanish
- **Single file constraint**: All changes go in the one HTML file
- **No build tools**: Don't suggest adding npm, webpack, etc.
- **Privacy focus**: Never suggest sending additional data to external services
- **Accessibility**: Consider screen readers and keyboard navigation
- **Browser compatibility**: Test features against File System Access API support
