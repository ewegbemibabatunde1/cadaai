# CADAAI International Website Redesign
## Community Anti-Drug Abuse Advocacy Initiative (Delta State, Nigeria)
### Master Technical Documentation & Deployment Guide

---

## 1. Project Overview & Institutional Identity

The **Community Anti-Drug Abuse Advocacy Initiative (CADAAI)** is a premier non-governmental organization in Delta State, Nigeria, committed to eradicating substance abuse among youths and vulnerable populations through proactive education, sustainable empowerment, and compassionate rehabilitation.

This project delivers a complete visual redesign and frontend redevelopment of the CADAAI digital platform. The new architecture is engineered to international design competition standards (Awwwards, CSS Design Awards, Webby Awards) while strictly preserving CADAAI's authentic organizational identity, factual content, verified bank details, and the 16-section information architecture.

### Repository File Structure
```
CADAAI/
├── index.html                   # Complete standalone website (Embedded scoped CSS, Semantic HTML5, Vanilla ES6+ JS)
├── README.md                    # Master technical documentation & deployment guide
└── assets/
    ├── logos/
    │   ├── logo.png             # Official CADAAI brand logo (Transparent PNG)
    │   ├── icon.png             # Official CADAAI insignia / seal (Transparent PNG)
    │   └── icon2.png            # Official CADAAI emblem variation (Transparent PNG)
    ├── images/
    │   ├── hero-bg.jpg          # Cinematic hero background
    │   ├── about-youth.jpg      # Editorial youth education in Delta State
    │   ├── featured-campaign.jpg# Delta School Tour: Orhuwhorun Campaign
    │   ├── gallery-school.jpg   # Gallery 01: School Campaign
    │   ├── gallery-community.jpg# Gallery 02: Community Outreach
    │   ├── gallery-seminar.jpg  # Gallery 03: Drug Awareness Seminar
    │   ├── gallery-counselling.jpg # Gallery 04: Counselling Session
    │   ├── gallery-empowerment.jpg # Gallery 05: Youth Empowerment
    │   ├── gallery-volunteer.jpg   # Gallery 06: Volunteer Activity
    │   ├── gallery-partnership.jpg # Gallery 07: Partnership Event
    │   └── gallery-recovery.jpg    # Gallery 08: Recovery Program
    └── fonts/                   # Reserved directory for offline web font hosting
```

---

## 2. Information Architecture (All 16 Sections Preserved & Elevated)

1. **Header & Navigation:** Editorial header with glassmorphism on scroll, CADAAI brand logo, desktop nav links, accessible mobile drawer toggle, and "Donate Now" CTA pill.
2. **Hero Section:** "Building a Drug-Free Generation in Delta State" headline, CADAAI official seal badge, dual action buttons, and trust bar indicators.
3. **About CADAAI:** Editorial magazine-style layout, authentic Delta State youth documentary photography, institutional accreditation callout, and mission narrative.
4. **Vision, Mission & Goals:** Three-pillar architectural layout featuring distinct numeric milestones (`01`, `02`, `03`) and the 2030 target of 100,000 youths reached.
5. **Impact in Numbers:** Dynamic viewport-triggered count-up animation honoring verified target milestones (5,000+ Students, 150+ Campaigns, 35+ Schools, 500+ Sessions) with transparent field auditing footnote.
6. **Core Values:** Tactile stone presentation of Compassion, Integrity, Commitment, and Innovation.
7. **Our Policy Thrust:** Four-phase policy framework (Education, Counselling, Advocacy, Empowerment).
8. **Understanding the Impact of Drug Abuse:** High-contrast dual clinical dossiers detailing Immediate Acute Effects vs. Long-Term Chronic Consequences.
9. **Our Key Programs:** Categorized eight-program directory (Prevention, Support, Education, Growth, Community, Recovery, Mobilization, Policy).
10. **The Rehabilitation Journey:** Three-stage patient and family roadmap (01 Overcome, 02 Regain, 03 Reintegrate).
11. **Featured Campaign — Delta School Tour:** Prominent editorial card showcasing the Orhuwhorun High School Campaign with field metrics (1,200+ students mobilized).
12. **Impact Gallery:** Eight curated documentary photographs with an accessible native modal Lightbox featuring keyboard navigation (`ArrowLeft`, `ArrowRight`, `Escape`).
13. **Be a Catalyst for Change / Donation Vault:** High-credibility donation block featuring Moniepoint MFB, official account name, one-click copy-to-clipboard for `6118664416`, and direct donation verification flow.
14. **Contact Us:** Comprehensive communication suite with verified office location (123 Advocacy Way, Asaba), telephone, email, social links, and accessible contact form with real-time feedback.
15. **Map Integration:** Responsive Google Map embed targeting Asaba, Delta State, with office location details and directions link.
16. **Institutional Footer:** Complete institutional footer featuring CADAAI logo, crisis hotline badge, navigation links, programmatic categories, newsletter subscription form, copyright, and IntellivastAI web design credit.

---

## 3. WordPress Scoping & Architectural Isolation Plan

To ensure the new website functions independently and does not conflict with existing WordPress themes, plugins, Elementor, or global CSS resets, the codebase strictly adheres to the following rules:

### 3.1 CSS Scoping
All CSS styles are scoped under the `#cadaai-site` root namespace selector. No generic naked HTML element selectors (`body`, `h1`, `h2`, `p`, `a`, `button`, `section`) are declared at the root level.
```css
#cadaai-site {
  /* Design system tokens & reset */
  --cad-blue-800: #0b4f8c;
  --cad-green-600: #27ae60;
  font-family: 'Inter', sans-serif;
}

#cadaai-site * {
  box-sizing: border-box;
}

#cadaai-site .cad-hero { ... }
```

### 3.2 JavaScript Encapsulation
All application JavaScript is wrapped in an Immediately Invoked Function Expression (IIFE) running in strict mode (`'use strict'`). Zero variables or functions leak to the global `window` object:
```javascript
(function () {
  'use strict';
  // All event listeners, observers, lightbox controllers, and clipboard handlers
})();
```

---

## 4. Production Deployment Instructions

### Method A: Standalone Subfolder Deployment (Recommended Initial Staging)
1. Using cPanel File Manager or SFTP, navigate to the web root:
   ```
   public_html/
   ```
2. Create a new directory named `cadaai`:
   ```
   public_html/cadaai/
   ```
3. Upload `index.html` and the entire `assets/` folder into `public_html/cadaai/`.
4. Test and review the live redesigned site immediately at:
   ```
   https://cadaai.com.ng/cadaai/
   ```
   *This staging path leaves the current production website and WordPress `/wp-admin/` completely untouched.*

### Method B: Direct Homepage Replacement via `.htaccess` (Permanent Go-Live)
When the stakeholder approves the redesign for the main homepage (`https://cadaai.com.ng/`):

1. Keep WordPress intact in `public_html/` so that admin functions (`/wp-login.php`, `/wp-admin/`) continue to function without interruption.
2. In `public_html/.htaccess`, add the following rewrite rule before the `# BEGIN WordPress` block to serve the standalone `index.html` exclusively for the homepage request:
   ```apache
   # CADAAI Homepage Direct Serving
   RewriteEngine On
   RewriteRule ^$ cadaai/index.html [L]
   ```
3. Alternatively, copy `CADAAI/index.html` to `public_html/home.html` and configure the DirectoryIndex:
   ```apache
   DirectoryIndex home.html index.php
   ```

---

## 5. External Integrations & Verification Checklist

| Item | Details on New Site | Status / Action Required |
|---|---|---|
| **Banking** | Moniepoint MFB, Account `6118664416`, Community Anti-Drug Abuse Advocacy Initiative | Verified with copy button and WhatsApp receipt confirmation trigger. |
| **Helpline** | `+234 810 086 0610` (`wa.me/2348100860610`) | Active clickable links and floating WhatsApp action button. |
| **Contact Form** | Client-side validated with feedback message | Currently routes to visual ticket receipt. To connect to an email relay without exposing API keys, point form `action` to a serverless endpoint (e.g., Formspree, Brevo, or an isolated PHP mail handler `contact-relay.php`). |
| **Map** | Asaba, Delta State interactive map | Active responsive iframe with direct Google Maps location query. |

---

## 6. Accessibility & Performance Standards

- **Semantic HTML5:** Built using `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<aside>`, and `<footer>` elements with proper landmark ARIA roles.
- **Accessible Lightbox:** Focus management, ESC key closure, arrow key image browsing, and descriptive `alt` tags.
- **Color Contrast:** All body text meets or exceeds WCAG 2.1 AA 4.5:1 contrast standards against backgrounds.
- **Motion Sensitivity:** Respects `prefers-reduced-motion: reduce` by disabling smooth scroll loops and transition animations for sensitive users.
- **Zero Heavy Dependencies:** Zero jQuery, zero Bootstrap, zero heavy CSS libraries. Pure native ES6+ JavaScript and CSS3 custom properties for rapid sub-second load times.

