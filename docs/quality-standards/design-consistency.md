# Design Consistency: The Anti-Vibe-Coded Guide

Stop your sites from looking rushed. This guide covers the visual and structural patterns that separate professional work from amateur "vibe coded" sites.

## Why Design Consistency Matters

**For Your Business:**
- Visual polish justifies your [$300-700 pricing](../business-model/pricing-economics.md)
- Differentiates you from cheap Fiverr/WordPress sites
- Reduces client revision requests
- Builds professional portfolio pieces
- Creates referral-worthy work

**For Your Clients:**
- Professional appearance builds trust
- Consistent UX reduces confusion
- Better conversion rates
- Competitive advantage in their market

**The Reality:** Technical quality ([SEO](./seo.md), [Performance](./performance.md), [Accessibility](./accessibility.md)) gets you to "functional." Design consistency gets you to "professional."

---

## The Critical Visual Signals

These are the red flags that instantly scream "rushed build." Fix these or don't ship.

### 1. The Purple Gradient Syndrome

**The Problem:**
Random purple gradients, purple glows, purple shadows, purple accents when the brand isn't purple.

**Why It Happens:**
Default AI/template suggestions. Purple is the unofficial color of vibe coded design.

**The Fix:**
```css
/* ❌ Bad - Random purple accent */
.hero {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
}

/* ✅ Good - Brand-aligned color */
.hero {
  background: linear-gradient(135deg, #1e40af 0%, #3730a3 100%);
}
/* Only if blue is actually the brand color */
```

**Rule:** Only use purple if:
- It's explicitly part of the brand identity
- The client requested it
- You have a specific design reason

Otherwise, choose colors based on the client's actual brand or industry conventions.

### 2. Emoji Overload

**The Problem:**
✨ Sparkles everywhere ✨
Emojis as UI elements, in headings, on buttons, as bullet points.

**Why It Happens:**
Quick visual interest without design effort.

**The Fix:**

**Acceptable:**
- One emoji in page title for personality
- Occasional emoji in informal blog content

**Not Acceptable:**
- Emojis instead of icons in navigation
- Emojis on buttons
- Emojis as feature list bullets
- Multiple emojis in single heading

```html
<!-- ❌ Bad -->
<h1>Welcome to Our Site ✨🚀💫</h1>
<button>Get Started ✨</button>
<ul>
  <li>✅ Fast delivery</li>
  <li>✅ Great service</li>
</ul>

<!-- ✅ Good -->
<h1>Professional Plumbing Services</h1>
<button>Request Quote</button>
<ul class="feature-list">
  <li>Fast delivery</li>
  <li>Great service</li>
</ul>
```

**Rule for Client Sites:** Maximum 1-2 emojis per page, never in critical UI elements.

### 3. Fake or Generic Testimonials

**The Problem:**
- AI-generated avatars
- Names like "Sarah P."
- Generic quotes: "Great service!"
- No job titles or links
- Same face used twice

**Why It Happens:**
Trying to add social proof without actual testimonials.

**The Fix:**

**Option A - Real Testimonials:**
```html
<div class="testimonial">
  <img src="real-customer-photo.jpg" alt="John Martinez">
  <blockquote>
    "Fixed my water heater in 2 hours on a Sunday.
    Professional, fair pricing, and cleaned up after themselves."
  </blockquote>
  <cite>
    John Martinez, Homeowner<br>
    Austin, TX
  </cite>
</div>
```

**Option B - No Testimonials:**
If the client doesn't have real testimonials yet, omit the section entirely. Better to have no testimonials than fake ones.

**Option C - Alternative Social Proof:**
- "Serving Austin since 2015"
- "500+ satisfied customers"
- "Licensed & Insured (#12345)"
- Google Business rating (if good)

**Rule:** One real testimonial > Three fake testimonials > No testimonials.

### 4. Inconsistent Border Radius

**The Problem:**
4px here, 12px there, 32px buttons, circular avatars, square images.

**Why It Happens:**
Copy-pasting components without a system.

**The Fix:**

Create a border radius scale and stick to it:

```css
/* Design tokens - Define once */
:root {
  --radius-sm: 4px;   /* Small elements, badges */
  --radius-md: 8px;   /* Buttons, cards */
  --radius-lg: 12px;  /* Large cards, modals */
  --radius-full: 9999px; /* Pills, avatars */
}

/* ✅ Good - Consistent usage */
.button { border-radius: var(--radius-md); }
.card { border-radius: var(--radius-lg); }
.avatar { border-radius: var(--radius-full); }
.badge { border-radius: var(--radius-sm); }

/* ❌ Bad - Random values */
.button { border-radius: 7px; }
.card { border-radius: 15px; }
.avatar { border-radius: 50%; }
.badge { border-radius: 3px; }
```

**Rule:** Pick 3-4 values max. Use them everywhere. No exceptions.

### 5. Excessive Hover Animations

**The Problem:**
- Cards lifting aggressively
- Cards rotating
- Elements bouncing
- Shadows that look like flashlights
- Breaking alignment on hover

**Why It Happens:**
Adding movement for the sake of movement.

**The Fix:**

**Subtle is Professional:**
```css
/* ❌ Bad - Aggressive movement */
.card:hover {
  transform: translateY(-20px) rotate(2deg);
  box-shadow: 0 30px 60px rgba(0,0,0,0.5);
  transition: all 0.2s ease;
}

/* ✅ Good - Subtle feedback */
.card {
  transition: box-shadow 0.3s ease;
}

.card:hover {
  box-shadow: 0 4px 12px rgba(0,0,0,0.1);
}
```

**When to Use Hover Effects:**
- Buttons (subtle color/shadow change)
- Links (underline or color shift)
- Interactive cards (gentle shadow increase)

**When NOT to Use Hover Effects:**
- Non-interactive elements
- Text blocks
- Images (unless clickable)
- Already interactive elements (forms)

**Rule:** If hover breaks layout or alignment, remove it.

---

## Spacing & Rhythm Systems

Consistent spacing is the #1 signal of intentional design.

### The 8-Point Grid System

**Why 8pt?**
- Divisible by 2 (responsive scaling)
- Works well with common screen sizes
- Prevents random spacing values

**The Scale:**
```css
:root {
  --space-1: 8px;   /* 0.5rem */
  --space-2: 16px;  /* 1rem */
  --space-3: 24px;  /* 1.5rem */
  --space-4: 32px;  /* 2rem */
  --space-6: 48px;  /* 3rem */
  --space-8: 64px;  /* 4rem */
  --space-12: 96px; /* 6rem */
  --space-16: 128px; /* 8rem */
}
```

**Usage:**
```css
/* ✅ Good - Using the scale */
.section {
  padding-block: var(--space-12); /* 96px top/bottom */
  padding-inline: var(--space-4); /* 32px left/right */
}

.card {
  padding: var(--space-4);
  margin-bottom: var(--space-6);
}

/* ❌ Bad - Random values */
.section {
  padding: 73px 25px; /* Why these numbers? */
}
```

**Tailwind Users:**
Tailwind already uses an 8pt-based system. Stick to it:
```html
<!-- ✅ Good - Consistent spacing -->
<section class="py-24 px-8">
  <div class="space-y-12">
    <div class="p-8">...</div>
  </div>
</section>

<!-- ❌ Bad - Random values -->
<section class="py-[73px] px-[25px]">
  <div class="space-y-[47px]">
    <div class="p-[13px]">...</div>
  </div>
</section>
```

**Rule:** No spacing values outside your defined scale. Ever.

### Typography Hierarchy

Inconsistent typography destroys visual polish.

**The System:**
```css
/* Type scale */
:root {
  --text-xs: 0.75rem;   /* 12px - Labels, captions */
  --text-sm: 0.875rem;  /* 14px - Small text */
  --text-base: 1rem;    /* 16px - Body text */
  --text-lg: 1.125rem;  /* 18px - Lead paragraph */
  --text-xl: 1.25rem;   /* 20px - h4 */
  --text-2xl: 1.5rem;   /* 24px - h3 */
  --text-3xl: 1.875rem; /* 30px - h2 */
  --text-4xl: 2.25rem;  /* 36px - h1 */
  --text-5xl: 3rem;     /* 48px - Display */
}

/* Font weights */
:root {
  --font-normal: 400;
  --font-medium: 500;
  --font-semibold: 600;
  --font-bold: 700;
}

/* Line heights */
:root {
  --leading-tight: 1.25;   /* Headings */
  --leading-normal: 1.5;   /* Body */
  --leading-relaxed: 1.75; /* Long-form */
}
```

**Application:**
```css
/* ✅ Good - Systematic typography */
h1 {
  font-size: var(--text-4xl);
  font-weight: var(--font-bold);
  line-height: var(--leading-tight);
}

body {
  font-size: var(--text-base);
  font-weight: var(--font-normal);
  line-height: var(--leading-normal);
}

/* ❌ Bad - Random values */
h1 {
  font-size: 37px;
  font-weight: 650;
  line-height: 1.3;
}
```

**Common Mistakes:**
- Headings too bold (900 weight)
- Body text too light (300 weight)
- Inconsistent line heights
- Too many font sizes

**Rule:** Define 6-8 sizes, 3-4 weights. Use only those.

---

## Component Consistency

Components should look like they belong together.

### Elevation & Shadows

Pick ONE shadow system and use it everywhere.

```css
/* Define elevation levels */
:root {
  --shadow-sm: 0 1px 2px rgba(0,0,0,0.05);
  --shadow-md: 0 4px 6px rgba(0,0,0,0.1);
  --shadow-lg: 0 10px 15px rgba(0,0,0,0.1);
  --shadow-xl: 0 20px 25px rgba(0,0,0,0.1);
}

/* ✅ Good - Consistent elevation */
.card { box-shadow: var(--shadow-md); }
.card:hover { box-shadow: var(--shadow-lg); }
.modal { box-shadow: var(--shadow-xl); }

/* ❌ Bad - Random shadows */
.card { box-shadow: 0 3px 7px rgba(0,0,0,0.15); }
.button { box-shadow: 0 2px 8px #00000033; }
```

**Rule:** Same shadow values across all components at the same elevation level.

### Button Consistency

All buttons should share core DNA.

```css
/* Base button */
.btn {
  padding: var(--space-2) var(--space-4);
  border-radius: var(--radius-md);
  font-weight: var(--font-semibold);
  transition: all 0.2s ease;
}

/* Variants */
.btn-primary {
  background: var(--color-primary);
  color: white;
}

.btn-secondary {
  background: transparent;
  border: 2px solid var(--color-primary);
  color: var(--color-primary);
}

/* States */
.btn:hover {
  transform: translateY(-1px);
  box-shadow: var(--shadow-md);
}

.btn:active {
  transform: translateY(0);
}
```

**What Should Be Consistent:**
- Padding (same for all buttons)
- Border radius (same for all buttons)
- Font weight (same for all buttons)
- Transition timing (same for all buttons)
- Hover behavior (same for all buttons)

**What Can Vary:**
- Colors (primary vs secondary)
- Size (small vs large)
- Icon presence

**Rule:** If you copy-paste a button and change the padding, you're doing it wrong.

---

## Interaction Quality

How things behave matters as much as how they look.

### Loading States

**The Problem:**
Clicking a button and nothing happens for 3 seconds. Amateur hour.

**The Fix:**

Every async action needs visual feedback:

```html
<!-- ✅ Good - Loading state -->
<button
  class="btn"
  onclick="handleSubmit(this)"
>
  <span class="button-text">Submit</span>
  <span class="button-loader hidden">
    <svg class="spinner">...</svg>
  </span>
</button>

<script>
async function handleSubmit(button) {
  // Show loading state
  button.disabled = true;
  button.querySelector('.button-text').classList.add('hidden');
  button.querySelector('.button-loader').classList.remove('hidden');

  // Perform action
  await submitForm();

  // Reset state
  button.disabled = false;
  button.querySelector('.button-text').classList.remove('hidden');
  button.querySelector('.button-loader').classList.add('hidden');
}
</script>
```

**Common Places Needing Loading States:**
- Form submissions
- "Load more" buttons
- Search bars
- Login/signup
- Any API call triggered by user

**Rule:** If it takes >500ms, show a loading state.

### Functional Interactive Elements

**The Problem:**
- Carousels that don't slide
- Tabs that don't switch
- Accordions that don't open
- Modals that won't close
- Dark mode toggles that do nothing

**The Fix:**

Test every interactive element before shipping:

**Pre-Ship Interactive Checklist:**
- [ ] All buttons trigger actions
- [ ] All forms submit successfully
- [ ] All links go to correct destinations
- [ ] All navigation items work
- [ ] Modals open AND close
- [ ] Dropdowns expand AND collapse
- [ ] Accordions toggle properly
- [ ] Tabs switch content
- [ ] Search actually searches
- [ ] Filters actually filter

**Rule:** If it looks clickable, it must work. If it doesn't work, remove it.

### Responsive Behavior

**Common Responsive Failures:**
- Text overflowing containers
- Cards stacking weird
- Buttons too wide on mobile
- Layout collapsing
- Horizontal scrolling

**The Fix:**

Test at these breakpoints:
- **375px** - iPhone SE (smallest modern phone)
- **768px** - iPad portrait (tablet)
- **1024px** - iPad landscape / small laptop
- **1440px** - Standard desktop

```css
/* Mobile-first approach */
.container {
  padding: var(--space-4); /* 32px on mobile */
}

.grid {
  display: grid;
  grid-template-columns: 1fr; /* Stack on mobile */
  gap: var(--space-4);
}

/* Tablet and up */
@media (min-width: 768px) {
  .container {
    padding: var(--space-8); /* 64px on tablet+ */
  }

  .grid {
    grid-template-columns: repeat(2, 1fr); /* 2 columns */
  }
}

/* Desktop */
@media (min-width: 1024px) {
  .grid {
    grid-template-columns: repeat(3, 1fr); /* 3 columns */
  }
}
```

**Rule:** Design for mobile first, enhance for desktop. Test on real devices.

---

## Copy & Content Quality

Design isn't just visual. Words matter.

### Avoid Generic Taglines

**The Problem:**
Meaningless hero copy that could apply to any business.

**Bad Examples:**
- "Build your dreams"
- "Launch faster"
- "Create without limits"
- "Where ideas become reality"
- "The future of [industry]"

**Good Examples (Specific & Clear):**
- "Emergency plumbing in Austin. 24/7 service, 30-min response"
- "Tax preparation for small businesses. $299 flat rate"
- "Custom WordPress sites for lawyers. 2-week delivery"

**The Formula:**
```
[Service] for [Audience]. [Key Benefit/Differentiator]
```

**Rule:** If your tagline could work for any business, it's bad copy.

### Copyright & Footer Text

**The Problem:**
Sloppy footer text signals overall sloppiness.

```html
<!-- ❌ Bad -->
<footer>
  <p>Copyright 2024 YourSiteName</p>
  <p>All right reversed</p>
  <p>Made by Me</p>
</footer>

<!-- ✅ Good -->
<footer>
  <p>&copy; 2024 Johnson Plumbing LLC. All rights reserved.</p>
  <p>Licensed & Insured | License #12345</p>
</footer>
```

**Rule:** Get the small details right. They signal professionalism.

### Placeholder Text

**The Problem:**
Shipping with "Lorem ipsum" or test content.

**Pre-Ship Content Checklist:**
- [ ] No "Lorem ipsum" anywhere
- [ ] No "Test heading" or "Sample text"
- [ ] No "Insert content here"
- [ ] No "[Your business name]" placeholders
- [ ] No "TODO: write this section"
- [ ] All phone numbers are real
- [ ] All email addresses work
- [ ] All addresses are correct

**Rule:** Search for "lorem", "test", "sample", "TODO", "[" before shipping.

---

## Technical Foundations

Design quality requires technical excellence.

### Meta Tags & SEO Basics

Visual design gets users to click. Meta tags get them to find you.

**Required Meta Tags:**
```html
<head>
  <!-- Title (50-60 characters) -->
  <title>Johnson Plumbing - 24/7 Emergency Service in Austin, TX</title>

  <!-- Description (150-160 characters) -->
  <meta name="description" content="Licensed plumber in Austin. Emergency repairs, installations, drain cleaning. 30-min response time. Call now!">

  <!-- Open Graph for social sharing -->
  <meta property="og:title" content="Johnson Plumbing - 24/7 Emergency Service">
  <meta property="og:description" content="Licensed plumber in Austin. Emergency repairs, installations, drain cleaning.">
  <meta property="og:image" content="https://example.com/og-image.jpg">
  <meta property="og:url" content="https://example.com">

  <!-- Favicon -->
  <link rel="icon" type="image/png" href="/favicon.png">

  <!-- Viewport -->
  <meta name="viewport" content="width=device-width, initial-scale=1">
</head>
```

**See also:** [Complete SEO Guide](./seo.md)

### Functional Requirements

**Every site must have:**
- [ ] Working favicon (not default browser icon)
- [ ] Proper page titles (unique per page)
- [ ] Meta descriptions
- [ ] Open Graph image (1200x630px)
- [ ] 404 page (not default server error)
- [ ] Mobile viewport meta tag
- [ ] HTTPS (Cloudflare Pages handles this)

**See also:** [Quality Gates Checklist](./quality-gates.md)

---

## Project-Type Specific Standards

Different projects have different design priorities.

### Local Business Website

**Context:** Your main business model ([Building sites for local businesses](../business-model/README.md))

**Design Priorities:**
1. **Clarity over creativity** - They need customers, not design awards
2. **Mobile-first** - Most searches are mobile
3. **Fast loading** - Emergency searches need quick answers
4. **Trust signals** - License numbers, years in business, real photos

**Common Sections:**
- Hero with service area
- Services overview (3-6 key services)
- Call-to-action (phone, form)
- Trust markers (licensed, insured, reviews)
- Contact info (phone, hours, location)

**Design Don'ts:**
- No excessive animations
- No complex navigation
- No auto-playing videos
- No popups on mobile
- No generic stock photos

**Template Structure:**
```html
<header>
  <nav>Logo + Phone + Menu</nav>
</header>

<main>
  <section class="hero">
    Service + Location + CTA
  </section>

  <section class="services">
    3-6 key services
  </section>

  <section class="trust">
    Licensed + Insured + Reviews
  </section>

  <section class="contact">
    Form + Phone + Hours + Map
  </section>
</main>

<footer>
  Contact + Legal + Links
</footer>
```

**See also:** [Business Model Guide](../business-model/README.md)

### Landing Page / SaaS

**Design Priorities:**
1. **Clear value proposition** (above fold)
2. **Single conversion goal** (don't confuse visitors)
3. **Social proof** (testimonials, logos, metrics)
4. **Visual hierarchy** (guide eye down page)

**Common Sections:**
- Hero (value prop + CTA)
- Problem/Solution
- Features (3-4 key features)
- Social proof
- Pricing (if applicable)
- Final CTA

**Design Don'ts:**
- No multiple competing CTAs
- No vague benefit statements
- No fake testimonials
- No cluttered hero sections

### Portfolio / Personal Site

**Design Priorities:**
1. **Showcase work first** (not bio)
2. **Fast loading** (lots of images)
3. **Easy navigation** (to specific projects)
4. **Contact accessibility** (make hiring you easy)

**Design Don'ts:**
- No auto-playing anything
- No excessive personal branding
- No hiding contact info
- No slow image galleries

---

## Design Consistency Checklist

Use this before shipping any client project.

### Visual Consistency ✅
- [ ] Border radius values limited to 3-4 options
- [ ] Spacing follows 8pt grid (or defined system)
- [ ] Typography uses defined scale (6-8 sizes max)
- [ ] Colors limited to defined palette
- [ ] Shadows use consistent elevation system
- [ ] No random purple unless brand-appropriate
- [ ] Emoji usage minimal (<2 per page)

### Component Consistency ✅
- [ ] All buttons share core styles
- [ ] All cards use same structure
- [ ] All forms follow same patterns
- [ ] All links behave consistently
- [ ] All interactive elements have hover states
- [ ] All hover effects are subtle

### Interaction Quality ✅
- [ ] Loading states on all async actions
- [ ] All interactive elements work
- [ ] No broken links or buttons
- [ ] Animations don't break layout
- [ ] Responsive at 375px, 768px, 1024px
- [ ] No horizontal scrolling on mobile

### Content Quality ✅
- [ ] No generic/vague taglines
- [ ] Footer text grammatically correct
- [ ] No placeholder text (lorem, test, TODO)
- [ ] Testimonials are real or omitted
- [ ] Copyright year current
- [ ] All contact info accurate

### Technical Quality ✅
- [ ] Unique page titles
- [ ] Meta descriptions present
- [ ] Open Graph tags configured
- [ ] Favicon present (not default)
- [ ] 404 page exists
- [ ] HTTPS enabled

**Pass Rate:** 90%+ of checklist items = Ship it
**Below 80%:** Not ready for client review

---

## Common Design System Mistakes

### Mistake 1: Too Many Variables

```css
/* ❌ Bad - Decision paralysis */
:root {
  --spacing-1: 4px;
  --spacing-2: 8px;
  --spacing-3: 12px;
  --spacing-4: 16px;
  --spacing-5: 20px;
  --spacing-6: 24px;
  --spacing-7: 28px;
  --spacing-8: 32px;
  /* ... 20 more spacing values */
}

/* ✅ Good - Useful scale */
:root {
  --space-2: 8px;
  --space-4: 16px;
  --space-6: 24px;
  --space-8: 32px;
  --space-12: 48px;
  --space-16: 64px;
}
```

**Rule:** Fewer, well-chosen options > Many confusing options

### Mistake 2: Inconsistent Component Usage

```html
<!-- ❌ Bad - Components look different -->
<button class="px-4 py-2 rounded-md">Button 1</button>
<button class="px-6 py-3 rounded-lg">Button 2</button>
<button class="px-3 py-1 rounded">Button 3</button>

<!-- ✅ Good - Consistent base, clear variants -->
<button class="btn btn-primary">Button 1</button>
<button class="btn btn-secondary">Button 2</button>
<button class="btn btn-small">Button 3</button>
```

**Rule:** Create component classes, not one-off styles

### Mistake 3: No Design Tokens

```css
/* ❌ Bad - Magic numbers everywhere */
.card { padding: 24px; }
.section { padding: 96px 0; }
.button { padding: 12px 24px; }
.modal { padding: 32px; }

/* ✅ Good - Named tokens */
.card { padding: var(--space-6); }
.section { padding: var(--space-24) 0; }
.button { padding: var(--space-3) var(--space-6); }
.modal { padding: var(--space-8); }
```

**Rule:** Define once, use everywhere

---

## AI-Assisted Design Consistency

### Prompt for Consistency Check

Use this when reviewing AI-generated code:

```
Audit this code for design consistency issues:

[paste HTML/CSS]

Check for:
1. Inconsistent spacing values (not on 8pt grid)
2. Random border-radius values
3. Typography not following scale
4. Shadow values that vary randomly
5. Color values used only once
6. Hover effects that break layout
7. Missing loading states
8. Non-functional interactive elements

List all issues and suggest fixes using a design token system.
```

### Prompt for Component Creation

```
Create a [component type] following these design standards:

- 8pt spacing grid (8, 16, 24, 32, 48, 64, 96px)
- Border radius: 8px for cards, 6px for buttons
- Typography: text-base (16px) body, text-xl (20px) headings
- Colors: [your brand colors]
- Shadow: 0 4px 6px rgba(0,0,0,0.1) for cards
- Transitions: 0.2s ease for interactions

The component should:
- Work on mobile (375px+)
- Have proper loading states if interactive
- Use semantic HTML
- Include hover states for interactive elements
```

**See also:** [Quality-Focused Prompts](../prompting/quality-focused-prompts.md)

---

## Resources

### Design Systems Examples
- [Tailwind UI](https://tailwindui.com/) - Well-structured components
- [Shadcn/ui](https://ui.shadcn.com/) - Consistent component patterns
- [Material Design](https://material.io/) - Comprehensive design system

### Tools
- [Coolors](https://coolors.co/) - Color palette generation
- [Type Scale](https://typescale.com/) - Typography scale calculator
- [Contrast Checker](https://webaim.org/resources/contrastchecker/) - WCAG contrast ratios
- Chrome DevTools - Inspect spacing/sizing

### Related Documentation
- [Quality Gates](./quality-gates.md) - Pre-ship checklist
- [Accessibility](./accessibility.md) - WCAG compliance
- [Performance](./performance.md) - Speed optimization
- [SEO](./seo.md) - Search optimization
- [Quality-Focused Prompts](../prompting/quality-focused-prompts.md) - AI prompts for quality

---

## Key Takeaways

### Quality = Consistency

**Professional sites have:**
- Predictable spacing
- Consistent components
- Systematic typography
- Intentional colors
- Subtle interactions
- Working features

**Amateur sites have:**
- Random spacing
- Inconsistent components
- Random typography
- Arbitrary colors
- Chaotic interactions
- Broken features

### Start with Systems, Not Styles

**Wrong approach:** Style each element as you build it

**Right approach:** Define design tokens first, then build components using those tokens

### Test Everything

**Before shipping:**
- Test all interactive elements
- Check spacing consistency
- Verify typography hierarchy
- Test responsive breakpoints
- Remove placeholder content
- Validate meta tags

### Design Consistency = Higher Rates

Professional, consistent design justifies your [$300-700 pricing](../business-model/pricing-economics.md) and differentiates you from cheap alternatives.

---

**Related Guides:**
- [Quality Gates Checklist](./quality-gates.md) - Quick pre-ship check
- [Quality Standards Overview](./README.md) - All quality pillars
- [Business Model](../business-model/README.md) - How quality drives revenue
- [Workflow Guide](../workflow/README.md) - When to check quality

**Back to:** [Main Guide](../../README.md)
