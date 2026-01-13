# KRYSTALIS • essentiel — AI Development Guidelines

## Project Overview

**KRYSTALIS • essentiel** is a luxury European dermo-cosmetic brand website with a **phased roadmap**.

**Current Phase (v0):** Coming-soon landing page with email subscription. Production-ready, fully functional, single `index.html` file.

**Future Phases:** AI-powered personalization—skin diagnostics, concierge chat, text-to-speech product narratives (documented in [README.md](../README.md)).

**Design Philosophy:**
- Single-file HTML architecture (`index.html` only—no separate CSS/JS files, no build tools)
- Vanilla JavaScript (no frameworks)
- Pure CSS in `<style>` block (CSS variables for theming, Tailwind CDN ready for future expansion)
- Luxury aesthetic: Cinzel serif for headers, Montserrat sans-serif for body, turquoise/gold palette, glassmorphic design

---

## Architecture

```
/workspaces/krystalis-essentiel/
├── index.html              # SINGLE FILE: HTML + <style> + <script>
├── README.md               # Brand docs & future feature roadmap
├── CNAME                   # DNS configuration (GitHub Pages)
└── .github/
    └── copilot-instructions.md  # This file
```

**Key Constraint:** All code must be in `index.html`. No separate CSS/JS files, no build artifacts, no node_modules.

---

## Tech Stack

### Current Implementation
- **HTML/CSS:** Pure CSS in `<style>` block (CSS variables for color theming)
- **JavaScript:** Vanilla (email input validation, event listeners)
- **Fonts:** Google Fonts CDN — `Cinzel` (serif, headers) and `Montserrat` (sans-serif, body)
- **External Resources:** Only Google Fonts; no APIs, frameworks, or dependencies
- **Color System:** CSS custom properties (`:root` variables)
  - `--pearl-white: #F9F9F9` (bg)
  - `--turquoise: #00A8B5` (primary CTA)
  - `--satin-gold: #C5A059` (accents, dividers)
  - `--deep-black: #1A1A1A` (text)

### Planned Additions (Future Phases)
- **Tailwind CSS CDN:** Utility-first styling when adding product grid & diagnostic form
- **Google Gemini API:** Text generation (diagnostics), web search (concierge), TTS (product narratives)
- **Web Audio API:** Browser playback for TTS narration

---

## Current Implementation

### Page Structure
```
Container (glassmorphic card, centered)
├── "Coming Soon" badge (turquoise pill)
├── Logo: "KRYSTALIS • ESSENTIEL" (Cinzel, •accent in turquoise)
├── Tagline: "L'Architecture du Soin" (gold)
├── Divider (gold line)
├── h1 Heading: "Bienvenue"
├── Description paragraphs (luxury messaging in French)
├── Divider
├── Email subscription section
│   ├── Label: "Soyez parmi les premiers informés"
│   ├── Input + Button (S'abonner)
│   └── Success/error message div
├── Social links (3 placeholder icons: Instagram, LinkedIn, Email)
└── Footer: Company name & copyright (Black Diamond Ltd, UIC 207807571)
```

### CSS Architecture
- **CSS Variables** (`:root`): Centralized color palette — update once, reusable everywhere
- **Glassmorphism:** `backdrop-filter: blur(10px)`, semi-transparent white background, subtle border
- **Animations:** `.fadeIn` keyframe on `.container` (1s, opacity + translateY)
- **Responsive:** `padding: 20px` on `body`, `max-width: 600px` container, flexbox centering
- **Typography:** Cinzel for headers (uppercase, `letter-spacing: 1-3px`), Montserrat for body (weight 300/400/600)

### JavaScript Behavior
- `subscribeEmail()` function: Validates email input (non-empty, contains `@`), displays success/error messages
- Color-coded feedback: Red (`#e74c3c`) for errors, turquoise for success
- Enter key listener: Pressing Enter in email input triggers `subscribeEmail()`
- Console logging: `console.log('Email subscribed:', email)` for future backend integration

---

## Development Workflow

### Local Testing
```bash
# Start simple HTTP server
python3 -m http.server 8000
# or: npx http-server
# Visit http://localhost:8000
```

### Making Changes
1. **Edit** `index.html` in VS Code
2. **Refresh** browser (Cmd+R / Ctrl+R) to see changes
3. **Test** email validation, responsive layout (DevTools: mobile/tablet/desktop)
4. **Commit** single file with clear message: `git add index.html && git commit -m "Add feature description"`

---

## Brand Conventions

### Color System (CSS Variables)
All colors defined in `:root`:
```css
--pearl-white: #F9F9F9       /* Background */
--turquoise: #00A8B5        /* Primary CTA, hover states, accents */
--satin-gold: #C5A059       /* Secondary accents, dividers, borders with opacity/30 */
--deep-black: #1A1A1A       /* Text, dark hover states */
```
**Rule:** Never hardcode hex values—always use `var(--color-name)`.

### Typography Rules
- **Headers:** `font-family: 'Cinzel'`, uppercase, `letter-spacing: 1-3px`, `font-weight: 700`
- **Body:** `font-family: 'Montserrat'`, weights: 300 (light), 400 (regular), 600 (semibold)
- **Font Loading:** Single Google Fonts CDN link in `<head>` — do not add additional fonts
- **Font Sizing:** Use `rem` units for scaling (e.g., `font-size: 2rem` for large headers, `0.85rem` for labels)

### Email Validation Pattern (Current Implementation)
```javascript
function subscribeEmail() {
    const email = emailInput.value.trim();
    
    // Validation checks
    if (!email) { /* show error */ }
    if (!email.includes('@')) { /* show error */ }
    
    // Success: update message, clear input, log
    message.style.color = '#00A8B5';
    emailInput.value = '';
}
```
- Always validate before processing
- Display feedback in `.emailMessage` div with color-coding (red `#e74c3c` for error, turquoise for success)
- Clear input field after successful submission

### CSS Class Naming
- Use semantic, lowercase names: `.email-section`, `.email-input-group`, `.coming-soon-badge`
- Group related styles: `.email-*` for all email-related elements
- Style states explicitly: `input:focus`, `button:hover`, `a:hover`

---

## Future Phases: AI Integration Guidelines

When adding diagnostic form, product grid, or concierge chat:
- **Product Names:** Use exact names from [README.md](../README.md): L'Éclat, Krystal-Lift, Regard Fixe, Cica-Snail, Pureté Intime
- **Language:** All user-facing text in French (buttons, labels, placeholders, messages)
- **Styling:** Extend existing CSS variables and Cinzel/Montserrat fonts; add Tailwind CDN `<link>` if needed
- **API Integration:** Replace `const apiKey = "";` with actual Gemini key; keep all code in `index.html`
- **Accessibility:** Maintain WCAG AA contrast on turquoise/white; keyboard navigation via Tab/Enter

## Deployment

No build process—simply host `index.html` on a static server:

```bash
# Local testing
python3 -m http.server 8000
# Visit http://localhost:8000

# Or with Node
npx http-server
```

**Pre-Deployment Checklist (Current Phase):**
1. Test email subscription form validation (empty, invalid email, valid email)
2. Test responsiveness (DevTools: mobile 320px, tablet 768px, desktop 1920px)
3. Verify Google Fonts load correctly
4. Check color contrast and readability

**Pre-Deployment Checklist (Future Phases):**
1. Add Gemini API key: `const apiKey = "YOUR_KEY";`
2. Test API calls for diagnostics, concierge chat, TTS
3. Verify Tailwind CDN loads if added
4. Update product list in system prompts if products change

---

## Critical Rules for Future Development

1. **Always use CSS variables** (`--turquoise`, `--satin-gold`, etc.)—never hardcode hex values
2. **Keep everything in `index.html`**—Tailwind CDN and Gemini API calls must stay in this file
3. **French language** for all user-facing text (placeholders, buttons, messages, error states)
4. **Maintain glassmorphic aesthetic:** backdrop-filter blur, subtle shadows, rounded corners
5. **Form inputs follow email pattern:** `addEventListener('keypress', e => { if (e.key === 'Enter') { /* action */ } })`

## Key References

- **Brand Documentation:** [README.md](../README.md) — Product specs, company info, product roadmap
- **Gemini API:** https://ai.google.dev/ (for future AI features)
- **Google Fonts:** Cinzel (headers), Montserrat (body)—loaded via CDN `<link>`
- **Products:** L'Éclat, Krystal-Lift, Regard Fixe, Cica-Snail, Pureté Intime
- **Company:** BLACK DIAMOND LTD (UIC 207807571)
- **GitHub Pages:** CNAME file configured for custom domain
