# KELŪA Website Brief (Claude Code Design + Build Input)

---

# 1. Background

KELŪA is a wellness-oriented brand and community centered around:
- meditation
- yoga
- pilates
- inner research
- presence
- intentional living
- emotional balance
- slow, conscious rituals

The website must not feel like a generic eCommerce store or a startup landing page.

It should feel like:
- calm
- elegant
- introspective
- refined
- breathable
- emotionally coherent
- modern but soft

The brand should communicate:
- presence
- beauty without noise
- ritual
- community
- depth
- accessibility without being commercial or loud

The website must support both:
- brand-building
- gradual commercial activation

At this stage, the website is primarily a:
- brand and community platform
- curated product showcase
- future events platform
- editorial and newsletter growth tool

---

# 2. Objective

Define and build the first working version of the KELŪA website in a way that:

- communicates the KELŪA brand clearly
- grows the WhatsApp community
- builds newsletter subscribers
- showcases selected products in a curated way
- introduces future events
- creates a premium but calm digital experience
- works beautifully across desktop and mobile
- can later evolve into a fuller commerce/event ecosystem

---

# 3. Current Phase

This is NOT yet a full commerce launch.

Current phase priorities:

1. Strong homepage and brand experience
2. Responsive and visually polished design
3. Community growth
4. Newsletter growth
5. Product presentation without full checkout
6. Events presentation without active booking
7. Clean architecture for future integrations

At this phase:
- products should be visible but not purchasable
- events should be visible but not bookable
- the site should still feel complete and intentional

---

# 4. Core Experience Principles

## Core Principles

- One unified website experience
- Calm, editorial, immersive feel
- Every section must have a clear role
- Do not overload the homepage
- Prioritize emotional clarity and visual rhythm
- All code must be modular and easy to extend
- The site must feel premium and soft, not loud or overdesigned
- Mobile and desktop must feel equally intentional

---

# 🚨 CRITICAL BUILD PRINCIPLE

## The website must be truly responsive and stable across:
- desktop
- tablet
- mobile
- iPhone Safari

This is a non-negotiable requirement.

The previous prototype had a serious mobile issue:
- on iPhone, content appeared shifted to the left
- a blank column appeared on the right
- layout felt broken and unbalanced

This must NOT happen again.

Claude must build with strong responsive discipline from the start.

---

# 📱 Critical Responsive Rules

All layouts must be designed and coded mobile-first or mobile-safe.

## Required implementation rules

- Use `box-sizing: border-box` globally
- Avoid accidental horizontal overflow
- Do NOT use `100vw` on main wrappers if it creates overflow on mobile
- Prefer `width: 100%` and `max-width`
- Avoid fixed pixel widths for layout containers
- Use fluid spacing and typography
- All images must scale correctly on smaller screens
- Navigation must work cleanly on mobile
- No invisible side columns
- No layout shifting due to burger menu area
- No elements should push the viewport wider than the screen
- Test for Safari / iPhone-safe layout behavior
- Avoid brittle fixed positioning unless necessary
- Any sticky/fixed element must be verified not to break preview or mobile
- Main layout must not rely on hacks

## Technical constraints to respect

- No horizontal scrolling
- No hidden off-canvas content affecting layout width
- No oversized absolute-positioned elements extending beyond viewport
- All sections must fit naturally within viewport width
- Buttons and cards must wrap or stack properly on mobile
- Header/nav must not leave empty columns or ghost click zones

---

# 5. Website Purpose by Layer

The site should support 4 main goals:

## A. Brand / Identity
Explain what KELŪA is, how it was born, why it exists, and what it wants to create.

## B. Community
Push users toward:
- WhatsApp community
- Instagram
- Newsletter

## C. Curated Products
Present selected products that fit the KELŪA vision.
For now:
- no real checkout
- no live Shopify purchase flow
- use “Coming Soon” / “Pre-order” / “Selection in Arrivo” states

## D. Future Events
Show the direction and intention of events.
For now:
- no active bookings
- no live Luma dependency required yet
- use a “Coming Soon” / “Stay updated via newsletter” approach

---

# 6. Homepage Structure

The homepage is the most important page and should feel like one continuous, fluid story.

## Required homepage sections

### 1. Hero
Must include:
- logo
- a strong calm headline / brand phrase
- daily quote area
- primary CTA to WhatsApp community
- secondary CTA to discover KELŪA or products
- visually rich but soft atmosphere

### 2. About / Brand Introduction
Must explain:
- who KELŪA is
- how it was born
- why it exists
- what it wants to create in the world

### 3. Community Section
Must support:
- WhatsApp CTA
- Instagram CTA
- emotional invitation to join the brand world

Important:
visible wording should use **“Community”**, not “Comunità”, where applicable in the approved interface language.

### 4. Products Preview
A curated preview of selected products.

At this stage:
- visible cards
- images
- short description
- state label such as:
  - Coming Soon
  - Pre-order
  - Selection in Arrivo
- no real checkout required

### 5. B2B / Large Orders Signal
A small but elegant section for potential wholesale / larger business interest.

### 6. Events Preview
A future-facing section that introduces the kind of events KELŪA wants to organize.

At this stage:
- visible but not active
- can include:
  - Coming Soon
  - Soon
  - Join the newsletter to be the first to know

### 7. Newsletter Section
Must be clearly recognizable as a newsletter signup.

Users must immediately understand:
- this field is for subscribing to the newsletter
- what value they receive by subscribing

### 8. Blog / Journal Preview
A preview area for future editorial content such as:
- anxiety management
- breathing
- mindfulness
- rituals
- emotional wellbeing
- present-moment living

### 9. Manifesto / Closing Section
A final emotional section that leaves a strong impression.

### 10. Footer
Must include:
- navigation
- contact email
- Instagram
- WhatsApp/community access
- legal links placeholders if needed

---

# 7. Visual Direction

The site should feel:

- calm
- fluid
- warm
- elegant
- introspective
- natural
- premium
- human

Avoid:
- flashy startup style
- aggressive animations
- loud gradients
- clutter
- consumer-retail discount language
- cold minimalism
- overmystical clichés

## Visual style principles

- generous spacing
- soft transitions
- refined typography
- natural textures
- subtle movement
- strong readability
- clean hierarchy
- emotionally coherent imagery

---

# 8. Logo Usage

Logo should be:

- clearly visible
- elegant
- not oversized
- well-spaced
- stable across desktop and mobile

Recommended behavior:
- smaller in navbar
- medium presence in hero
- never so large that it dominates the screen awkwardly

Keep logo implementation robust and preview-safe.

---

# 9. Images & Atmosphere

The site should use imagery intentionally.

## Hero background / first screen
It is recommended to include:
- a soft background image
or
- layered atmospheric imagery
or
- a subtle visual composition

Possible visual directions:
- wheat in the wind
- soft fabric movement
- candles
- natural light
- water
- leaves
- breathing space
- yoga/pilates details
- hands
- shadows
- rituals
- nature textures

Important:
text readability must remain high.

## Additional imagery across the site
Images can also be used in:
- products
- blog preview
- community / manifesto areas
- selected transitional sections

Do not overload every section with images.

---

# 10. Product Strategy (Current Phase)

Products should appear on the site now, but not as fully purchasable products yet.

## Current required state
- visible in homepage and/or product listing preview
- product imagery shown
- curated presentation
- not actively purchasable
- clear state communication:
  - Coming Soon
  - Pre-order
  - Selection in Arrivo

## Product source content
Initial product information may come from the Brazilian producer.

Claude may be asked to:
- extract product info
- translate product text into Italian
- rewrite it in a refined KELŪA tone
- structure:
  - short product card copy
  - longer product detail copy

Important:
- do not invent unsupported claims
- remain faithful to source content
- keep tone elegant and clear

## Product images
At this phase, producer-supplied images may be used as temporary product visuals if approved for use.

Later phases may replace them with more branded imagery.

---

# 11. Events Strategy (Current Phase)

Events should be visible as part of the brand direction, but not yet active.

## Current required state
- visible event section
- visually integrated into the site
- not clickable for purchase
- communicate:
  - events are coming soon
  - users should join the newsletter to stay updated

Examples of acceptable states:
- Coming Soon
- Soon
- Our events are on the way
- Join the newsletter to be first to know

## Luma
Luma may be integrated later when real events exist.
Do not force a full Luma integration in this phase unless explicitly requested.

---

# 12. Community & Contact Logic

The site should support clear paths to:
- WhatsApp
- Instagram
- newsletter signup
- contact email

## Important
Any CTA intended for WhatsApp must point to the real WhatsApp URL.
It must never point to internal placeholder routes or broken links.

Any newsletter field must clearly communicate that it is for newsletter subscription.

---

# 13. Technical Build Direction

Preferred approach:
- clean frontend-first architecture
- modular code
- lightweight
- easy to maintain
- preview-safe
- production-friendly

## General coding principles

- keep components structured
- avoid unnecessary dependencies
- do not overengineer
- do not break existing stable sections when editing isolated parts
- preserve working navbar/logo unless explicitly asked to change them
- edit surgically, not destructively

## Editing behavior
When making revisions:
- do not rewrite the whole homepage unnecessarily
- only change requested sections
- preserve stable working code
- avoid cascading regressions

---

# 14. Animation Principles

Animations should be:
- subtle
- calm
- lightweight
- elegant
- non-distracting

Preferred motion:
- fade in
- soft rise
- gentle parallax
- slow hover nuance

Avoid:
- aggressive motion
- heavy cinematic effects
- distracting floating systems
- anything that hurts performance

---

# 15. CTA Strategy

Every key section should have a clear CTA, but the site must not feel pushy.

## Primary CTA priorities
1. Join WhatsApp community
2. Join newsletter
3. Discover products
4. Explore the KELŪA world

## Current CTA logic
Products:
- not buy now
- use “Coming Soon”, “Pre-order”, “Discover”, or newsletter-driven CTA

Events:
- not book now
- use newsletter-driven CTA

---

# 16. Content Tone

Tone should be:
- calm
- refined
- human
- intentional
- warm
- non-generic
- non-cliché
- emotionally aware

Avoid:
- loud marketing language
- fake spirituality
- exaggerated wellness clichés
- startup buzzwords
- hard-selling retail copy

---

# 17. Key Pages for Current Phase

## Must support now
- Homepage
- About section/page
- Product preview section
- Events preview section
- Newsletter section
- Footer/contact structure

## Can come later
- Full product detail pages
- Full event pages
- Blog article pages
- Shopify integration
- Luma integration
- B2B dedicated page

---

# 18. Critical QA Requirements Before Accepting Any New HTML

Before considering any generated HTML/CSS acceptable, verify:

- Desktop layout is visually balanced
- Mobile layout does not shift left
- No empty right column on iPhone
- No horizontal overflow
- Navbar works correctly
- Burger area does not create layout imbalance
- All sections are visible
- No JS errors break reveal/visibility logic
- CTA links point to the correct destinations
- Newsletter section clearly reads as newsletter
- “Community” wording is consistent where required

---

# 19. Instructions for Claude Code (VERY IMPORTANT)

When generating or editing code:

- Do not redesign the whole site unless explicitly asked
- Respect the current approved structure
- Work section by section
- Preserve working navbar, logo, and fixed bugs unless asked to change them
- Prioritize mobile safety and layout integrity
- Never introduce overflow or offset bugs
- If a section is temporarily disabled for debugging, restore it carefully
- Do not assume placeholder links are final
- Use real contact links when provided
- Keep edits surgical and reversible

When outputting code:
- be concise
- return only the necessary changed blocks when possible
- do not repeat the full project brief
- do not rewrite stable sections unnecessarily

---

# 20. Expected Outputs from Claude Code

- stable responsive HTML/CSS/JS
- homepage refinements
- hero with image direction
- product preview with coming soon state
- event preview with coming soon state
- newsletter clarity improvements
- modular sections ready for future integration
- future-safe structure for Shopify and Luma
