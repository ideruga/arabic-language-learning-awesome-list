# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a standalone Arabic typing trainer web application built as a single HTML file with embedded CSS and JavaScript. The app teaches Arabic typing using a progressive letter-pair system and provides three modes: letters, words, and texts.

## Architecture

### Single File Structure
- **index.html**: Complete application containing HTML structure, CSS styling, and JavaScript logic
- No build system, package management, or external dependencies required
- Self-contained neon-themed Arabic keyboard trainer

### Key Components (all in index.html)

**State Management**
- Global `state` object manages session data (lines 256-269)
- Includes mode, selected pair, sequence progress, timing, and keyboard mappings

**Arabic Keyboard System**
- `ARABIC_KEYBOARD_ROWS` defines visual keyboard layout (lines 192-196)
- `KEYMAP` provides English-to-Arabic character mapping (lines 199-203)
- Virtual keyboard rendered dynamically with visual feedback

**Progressive Learning System**
- `LETTER_PAIRS` array defines finger-position-based character pairs (lines 206-217)
- Progressive unlock system - selecting a pair includes all previous pairs
- Visual pair selector with hover preview functionality

**Three Learning Modes**
- Letters: Progressive pair-based character practice
- Words: Common Arabic words from `WORD_BANK` (line 228-230)
- Texts: Sample text passages from `TEXT_BANK` (lines 232-234)

## Development Commands

### Testing the Application
```bash
# Open in browser (no server required)
open index.html

# Or serve locally if needed
python -m http.server 8000
# Then visit http://localhost:8000
```

### No Build Process
This is a static HTML file with no compilation, bundling, or preprocessing required.

## Key Implementation Details

**Input Handling**
- Maps English keyboard input to Arabic characters via `KEYMAP`
- Supports backspace navigation and space character handling
- Real-time accuracy and WPM calculation

**Visual Feedback System**
- Key highlighting for next expected character (`glow` class)
- Success/error feedback (`ok`/`bad` classes)
- Press animations and progressive pair preview

**Responsive Design**
- CSS Grid and Flexbox layout with `clamp()` for responsive text sizing
- Neon theme with CSS custom properties for consistent theming
- Mobile-friendly touch interactions

## Extending the Application

**Adding New Letter Pairs**
- Extend `LETTER_PAIRS` array with new character combinations
- Follow finger-position progression pattern

**Adding Content**
- Expand `WORD_BANK` for more word practice
- Add entries to `TEXT_BANK` for longer text exercises
- Maintain Arabic text direction (`dir="rtl"`)

**Styling Changes**
- Modify CSS custom properties in `:root` (lines 9-22) for theme adjustments
- Keyboard key styling in `.key` class (lines 80-92)