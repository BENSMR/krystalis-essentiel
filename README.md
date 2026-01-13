# KRYSTALIS • essentiel

Luxury European dermo-cosmetic brand website with **AI-powered skin diagnostics and concierge**.

## Features

- **Smart Skin Diagnostic:** AI analyzes skin type, concerns, and lifestyle context to recommend personalized routines
- **AI Concierge:** 24/7 chat interface powered by Google Gemini for expert skincare guidance
- **Text-to-Speech:** Luxurious French narration of product descriptions via Google Gemini TTS
- **Responsive Design:** Tailwind CSS for mobile, tablet, and desktop experiences
- **Single-File Architecture:** No build tools, no dependencies—pure HTML + Tailwind + Gemini API

## Products

1. **L'Éclat** - Crème Fondamentale Régénératrice (Hydratation Intense)
2. **Krystal-Lift** - Sérum Anti-Âge Haute Précision (Biotechnologie)
3. **Regard Fixe** - Soin Cryo-Métallique Drainant (Zone Regard)
4. **Cica-Snail** - Concentré Réparateur Cristallin (Réparation)
5. **Pureté Intime** - Soin Dermo-Protecteur Doux (Bien-être)

## Brand Identity

| Element | Value |
|---------|-------|
| **Tagline** | L'Architecture du Soin |
| **Subtitle** | Dermo-Cosmétique de Haute Précision |
| **Company** | Black Diamond Ltd (UIC 207807571) |
| **Primary Color** | Turquoise (`#00A8B5`) |
| **Secondary Color** | Satin Gold (`#C5A059`) |
| **Typography** | Cinzel (headers), Montserrat (body) |

## Tech Stack

- **HTML/CSS:** Tailwind CSS CDN + custom `<style>` overrides
- **JavaScript:** Vanilla (no frameworks)
- **AI:** Google Gemini API (text generation, TTS, web search)
- **Fonts:** Google Fonts (Cinzel, Montserrat)
- **Images:** Unsplash CDN

## Getting Started

### Local Development
```bash
# Serve the site locally
python3 -m http.server 8000
# Visit http://localhost:8000
```

### Configuration

**Set your Gemini API key:**
1. Obtain an API key from [Google AI Studio](https://aistudio.google.com/)
2. In `index.html`, find line with `const apiKey = "";`
3. Replace with your actual key: `const apiKey = "YOUR_KEY_HERE";`

## File Structure

```
index.html                 # Single-file app: HTML + Tailwind + Gemini integration
.github/
  └── copilot-instructions.md   # AI development guidelines
```

## Key Sections

- **Hero:** Parallax background, luxury messaging, CTA to diagnostic
- **Diagnostic Form:** Skin type + concerns + context → AI-generated routine recommendation
- **Product Grid:** 5 products with hover effects, TTS playback, "Découvrir" CTAs
- **Concierge Chat:** Floating widget with real-time AI responses (with web search)
- **Footer:** Brand info, company details

## AI Features

### Diagnostic Assistant
- Analyzes skin profile (type, concerns, lifestyle)
- Recommends personalized routine from product collection
- System prompt ensures luxury tone and product focus

### Concierge Chat
- Real-time conversation with Gemini AI
- Web search enabled for current skincare trends/advice
- Personality: Expert, compassionate, European perspective

### Text-to-Speech
- Product descriptions narrated in luxurious French
- Voice: Aoede (calm, sophisticated)
- Auto-plays on product card sound icon click

## Accessibility

- Color contrast: WCAG AA compliant on turquoise/white
- Keyboard navigation: All forms and buttons accessible via Tab/Enter
- Semantic HTML: Proper heading hierarchy, alt text on images
- Focus states: Visible focus rings on interactive elements

## Performance

- **No Build Step:** Single `index.html` serves directly
- **Image Optimization:** Unsplash handles CDN caching
- **API Caching:** Gemini responses cached in-memory during session
- **Load Time:** < 2s typical (mostly Google Fonts + Gemini API latency)

## Future Enhancements

- [ ] Product detail pages (individual routes or modal)
- [ ] E-commerce integration (Shopify sync)
- [ ] Multi-language support (FR/EN/DE)
- [ ] Customer review section
- [ ] Appointment booking for skincare consultations
- [ ] Newsletter signup with AI copywriting

## Support

For questions about the codebase, refer to [.github/copilot-instructions.md](.github/copilot-instructions.md) for comprehensive AI development guidelines.

---

**Black Diamond Ltd** © 2026  
*L'excellence européenne au service de votre peau.*
