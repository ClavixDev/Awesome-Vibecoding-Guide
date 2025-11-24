# Quality-Focused Prompts

System prompts and quality checks that prevent "vibe coded" output. Use these to ensure AI-generated code meets professional standards.

## Why Quality-Focused Prompts Matter

**The Problem:**
AI tools default to "make it work" not "make it professional." Without quality guidance, you get:
- Inconsistent spacing and design
- Generic copy and placeholder patterns
- Missing loading states and error handling
- Fake or generic content
- Random styling choices

**The Solution:**
Add quality requirements to your prompts. Bake professionalism into every AI interaction.

**Integration with Existing Prompts:**
- These prompts **augment** task-specific prompts ([Task-Specific Patterns](./task-specific-patterns.md))
- Use **with** your workflow ([Development Workflow](../workflow/README.md))
- Support quality standards ([Quality Standards](../quality-standards/README.md))

---

## Base Quality System Prompt

Use this as a foundation for any code generation task.

### Core Quality Prompt

```
You are a professional front-end developer building client-facing websites.
Every output must meet production quality standards.

Design System Requirements:
- Use 8-point spacing grid (8, 16, 24, 32, 48, 64, 96px only)
- Border radius: Choose from 4px, 8px, 12px, or full (9999px) - be consistent
- Typography: Define max 6-8 sizes, use semantic scale
- Colors: Stick to defined brand palette, avoid random purple/neon
- Shadows: Use 3-4 elevation levels maximum

Code Quality Standards:
- Semantic HTML (proper heading hierarchy, meaningful tags)
- All interactive elements must be functional
- Include loading states for any async operations
- Mobile-responsive (test breakpoint: 375px minimum)
- All images must have alt text
- No placeholder content (lorem ipsum, test, TODO)

Interaction Standards:
- Animations subtle and purposeful (no chaotic motion)
- Hover effects don't break layout or alignment
- All buttons, links, forms must work
- Focus states visible for accessibility
- No auto-playing media

Never include:
- Random purple gradients (unless brand-appropriate)
- Emoji overload (max 1-2 per page)
- Generic taglines ("build your dreams", "launch faster")
- Fake testimonials or placeholder reviews
- Inconsistent component styling
- Missing meta tags or SEO basics
```

**When to use:** Add to the beginning of any feature development or component creation prompt.

**See also:** [Design Consistency Guide](../quality-standards/design-consistency.md)

---

## Component-Specific Quality Prompts

### Building New Components

```
Create a [component type] following these standards:

Design Tokens:
- Spacing: Use var(--space-4), var(--space-6), var(--space-8) only
- Radius: var(--radius-md) for this component type
- Typography: var(--text-base) for body, var(--text-lg) for headings
- Colors: Use CSS custom properties for all colors
- Shadow: var(--shadow-md) for cards, var(--shadow-lg) for elevated elements

Technical Requirements:
- Semantic HTML (use proper tags: <section>, <article>, <nav>, etc.)
- Mobile-first (write mobile styles first, desktop in media queries)
- Accessible (ARIA labels if needed, keyboard navigation support)
- Loading states for interactive elements
- Error states for forms/inputs

Output Requirements:
1. Component code (HTML + CSS)
2. Usage example
3. Mobile responsive styles
4. Any required JavaScript for interactivity
5. Accessibility considerations noted

Do not include:
- Inline styles (use CSS classes)
- Random spacing values
- Generic placeholder text
- Non-functional interactive elements
```

**Example usage:**
```
Create a contact form following these standards:
[paste component quality prompt]

Requirements:
- Name, email, message fields
- Submit button with loading state
- Success/error messages
- Mobile optimized
```

---

### Reviewing Existing Components

```
Audit this component for quality issues:

[paste component code]

Check for:
1. Design consistency issues:
   - Inconsistent spacing (not on 8pt grid)
   - Random border-radius values
   - Typography not following a scale
   - Colors used only once (not in design system)

2. Accessibility issues:
   - Missing alt text on images
   - No ARIA labels on interactive elements
   - Poor color contrast
   - Missing focus indicators
   - Improper heading hierarchy

3. Interaction issues:
   - Missing loading states
   - Non-functional elements
   - Hover effects breaking layout
   - No error handling

4. Mobile responsiveness:
   - Fixed widths that break on mobile
   - Text too small
   - Touch targets too small (<44px)
   - Horizontal scrolling

5. Content issues:
   - Placeholder text (lorem, test, TODO)
   - Generic copy
   - Fake testimonials
   - Missing meta information

List all issues with severity (Critical/High/Medium/Low) and provide
specific fixes using design system tokens.
```

**When to use:** Before shipping components, or when debugging quality issues.

**See also:** [Quality Gates Checklist](../quality-standards/quality-gates.md)

---

## Page-Level Quality Prompts

### Building Full Pages

```
Create a [page type] following professional standards:

Page Structure:
- Semantic HTML5 structure (<header>, <main>, <footer>, <section>)
- Proper heading hierarchy (single h1, logical h2-h6)
- Mobile-first responsive design
- Consistent spacing rhythm (8pt grid)

Required Meta Tags:
- Unique <title> (50-60 chars): "[Primary Keyword] - [Brand]"
- Meta description (150-160 chars)
- Viewport meta tag
- Open Graph tags (title, description, image, URL)
- Favicon link

Content Requirements:
- Specific, non-generic copy
- Real value proposition in hero (under 15 words)
- No placeholder text
- Real testimonials OR omit testimonial section
- Accurate contact information

Technical Requirements:
- All interactive elements functional
- Loading states on forms/async actions
- Error handling for user inputs
- Mobile responsive (375px minimum)
- Images optimized and have alt text
- No console errors

Performance:
- Lazy load below-fold images
- Defer non-critical JavaScript
- Minimize render-blocking resources
- Target: Lighthouse score 90+ on all metrics
```

**Example for local business:**
```
Create a homepage for a plumbing business following professional standards:
[paste page quality prompt]

Business info:
- Name: Johnson Plumbing
- Location: Austin, TX
- Services: Emergency repairs, installations, drain cleaning
- USP: 30-minute response time, 24/7 availability

Include:
- Hero with service + location + phone CTA
- Services section (3-4 key services)
- Trust signals (licensed, insured, years in business)
- Contact form + phone + hours
```

**See also:** [Business Model - Local Business Sites](../business-model/README.md)

---

### Landing Page Quality Prompt

```
Create a landing page following conversion-focused standards:

Structure:
- Hero: Clear value prop + single primary CTA
- Problem/Solution section
- Features (3-4 maximum, benefit-focused)
- Social proof (testimonials OR metrics)
- Final CTA section

Copy Standards:
- Value proposition: Specific, under 15 words
- Headlines: Benefit-focused, not feature-focused
- CTA copy: Action-oriented ("Get Started" not "Submit")
- No generic phrases ("transform your business")

Design Requirements:
- Single primary CTA (don't confuse with multiple actions)
- Visual hierarchy guides eye down page
- Consistent spacing and alignment
- Mobile-first (most traffic is mobile)
- Fast loading (target LCP < 2.5s)

Conversion Optimization:
- CTA above fold (visible without scrolling)
- CTA repeated at bottom
- Form fields minimal (only essential info)
- Loading state on form submission
- Clear privacy/security messaging if collecting data

Do not include:
- Multiple competing CTAs
- Auto-playing video
- Pop-ups (especially on mobile)
- Fake testimonials
- Generic stock photos
- Vague benefit statements
```

**See also:** [Design Consistency - Landing Pages](../quality-standards/design-consistency.md)

---

## Quality Review Prompts

### Pre-Ship Quality Audit

```
Comprehensive quality audit for client delivery:

[paste website URL or codebase]

Run through these checks:

1. Visual/Design Consistency:
   - Spacing follows consistent system?
   - Border radius values consistent?
   - Typography uses defined scale?
   - Colors from defined palette?
   - No "vibe coded" signals (purple gradients, emoji overload)?

2. Functionality:
   - All buttons/links work?
   - Forms submit successfully?
   - Navigation works on mobile?
   - Loading states present?
   - No broken images or 404s?

3. Mobile Responsiveness:
   - Works at 375px width?
   - No horizontal scrolling?
   - Touch targets adequate size?
   - Text readable without zooming?

4. Content Quality:
   - No placeholder text (lorem, test, TODO)?
   - Testimonials real or removed?
   - Copy specific (not generic)?
   - Contact info accurate?
   - Copyright text correct?

5. Technical/SEO:
   - Meta tags present and unique?
   - Images have alt text?
   - Heading hierarchy proper?
   - Lighthouse scores 85+?
   - No console errors?

Output a checklist with ✅/❌ for each item, plus priority fixes.
```

**When to use:** Before client handoff, before deployment.

**See also:** [Quality Gates](../quality-standards/quality-gates.md)

---

### Accessibility Audit Prompt

```
WCAG 2.1 Level AA accessibility audit:

[paste HTML/CSS]

Check for:

Semantic HTML:
- Proper heading hierarchy (h1 → h2 → h3, no skips)
- Semantic tags used appropriately (<nav>, <main>, <article>)
- Lists use <ul>/<ol> tags
- Tables have <thead>, <tbody>, captions

Images & Media:
- All images have descriptive alt text
- Decorative images have alt=""
- Complex images have long descriptions
- No auto-playing media

Forms:
- All inputs have associated <label>
- Error messages clear and helpful
- Required fields marked
- Form validation accessible

Interactive Elements:
- All interactive elements keyboard accessible
- Focus indicators visible
- Tab order logical
- ARIA labels on icon buttons

Color & Contrast:
- Text contrast ratio ≥ 4.5:1 (normal text)
- Text contrast ratio ≥ 3:1 (large text 18pt+)
- UI component contrast ≥ 3:1
- Information not conveyed by color alone

For each issue found:
- Severity: Critical/High/Medium/Low
- WCAG criterion violated
- Code location
- Specific fix with example
```

**See also:** [Accessibility Guide](../quality-standards/accessibility.md)

---

### SEO Audit Prompt

```
SEO audit for local business website:

URL: [website URL]
Business Type: [e.g., plumber, electrician, lawyer]
Target Location: [city, state]

Audit these elements:

On-Page SEO:
- Title tag: Unique, includes location + service, under 60 chars?
- Meta description: Compelling, includes CTA, 150-160 chars?
- H1: Single, includes primary keyword?
- Headings: Proper hierarchy, keyword-optimized?
- Content: Mentions location/service area?
- Images: All have descriptive alt text with keywords?
- URLs: Clean, descriptive, include keywords?

Technical SEO:
- Mobile-friendly (Google mobile test)?
- HTTPS enabled?
- Sitemap.xml present and submitted?
- Robots.txt configured correctly?
- Page load speed < 3 seconds?
- No broken links?
- Canonical tags set?

Local SEO (for local businesses):
- NAP (Name, Address, Phone) consistent?
- Schema.org LocalBusiness markup?
- Location in title and content?
- Service area clearly stated?
- Google Business Profile mentioned/linked?
- Hours of operation listed?

Social/Open Graph:
- OG title, description, image set?
- Image 1200x630px, relevant?
- Twitter cards configured?

For each missing/poor element:
- Impact: High/Medium/Low
- Quick fix instructions
- Example implementation
```

**See also:** [SEO Guide](../quality-standards/seo.md)

---

## Tailwind-Specific Quality Prompts

### Tailwind Component Prompt

```
Create a [component] using Tailwind CSS with quality standards:

Spacing Requirements:
- Use only: p-2, p-4, p-6, p-8, p-12, p-16 (8pt scale)
- Gap utilities: gap-2, gap-4, gap-6, gap-8
- Margin: m-2, m-4, m-6, m-8, m-12, m-16
- Never use arbitrary values [p-17px] for spacing

Typography:
- Use text-sm, text-base, text-lg, text-xl, text-2xl, text-3xl, text-4xl
- Font weights: font-normal, font-medium, font-semibold, font-bold only
- Line height: leading-tight (headings), leading-normal (body)

Borders & Radius:
- Border radius: rounded (4px), rounded-md (6px), rounded-lg (8px), rounded-full
- Be consistent across similar components

Colors:
- Use theme colors: bg-blue-600, text-gray-900, etc.
- Hover states: hover:bg-blue-700
- Focus: focus:ring-2 focus:ring-blue-500 focus:ring-offset-2

Responsive:
- Mobile first: base styles for mobile
- Then add: sm:, md:, lg:, xl: prefixes
- Test at 375px (mobile), 768px (tablet), 1024px (desktop)

Accessibility:
- Use sr-only for screen reader text
- Focus states on all interactive elements
- Proper semantic HTML

Example:
<button class="px-6 py-3 bg-blue-600 text-white font-semibold rounded-md
  hover:bg-blue-700 focus:ring-2 focus:ring-blue-500 focus:ring-offset-2
  transition-colors duration-200">
  Button Text
</button>
```

**When to use:** Building components with Tailwind (your recommended stack)

**See also:** [Core Technologies - Tailwind](../core-technologies.md)

---

## Copy Quality Prompts

### Hero Section Copy Prompt

```
Write hero section copy for [business type]:

Business Context:
- Service: [specific service]
- Target Audience: [who needs this]
- Location: [if local business]
- Key Differentiator: [what makes them unique]

Requirements:
- Value proposition under 15 words
- Specific (not generic like "transform your business")
- Includes target audience or location (if local)
- Benefit-focused (what customer gets)
- No jargon or buzzwords

Output format:
Headline: [main value prop]
Subheadline: [supporting detail, 20-30 words]
CTA: [action-oriented button text]

Examples of bad vs good:
❌ Bad: "Transform Your Home Today"
✅ Good: "Emergency Plumbing in Austin. 30-Min Response Time"

❌ Bad: "Launch Faster, Build Better"
✅ Good: "Custom WordPress Sites for Law Firms. 2-Week Delivery"
```

**See also:** [Design Consistency - Copy Quality](../quality-standards/design-consistency.md#copy--content-quality)

---

### Testimonial Content Prompt

```
Generate testimonial guidelines for client:

Context: [business type, service provided]

Testimonial Requirements:
For each testimonial, collect:
- Full name (first + last, not "John D.")
- Specific quote (what was the actual benefit?)
- Context (job title, location, or identifying detail)
- Optional: photo (real person, not stock)

Good testimonial example:
"Fixed my water heater in 2 hours on a Sunday. Professional,
fair pricing, and cleaned up after themselves."
— John Martinez, Homeowner, Austin TX

Bad testimonial example:
"Great service! Very professional."
— Sarah P.

If no real testimonials available yet:
Option A: Wait to launch testimonial section until you have them
Option B: Use alternative social proof:
  - "Serving [location] since [year]"
  - "[X] satisfied customers"
  - "Licensed & Insured (#[license])"
  - Industry certifications/affiliations

Never fabricate testimonials or use:
- AI-generated avatars
- Generic stock photos
- Vague quotes without specifics
- Names without full context
```

---

## Prompts for Different Project Types

### Local Business Website Prompt

```
Build a professional website for [business type]:

Business Information:
- Name: [business name]
- Services: [3-6 primary services]
- Location: [city, state]
- Contact: [phone, email, address]
- USP: [unique selling proposition]
- Hours: [business hours]

Technical Stack:
- Astro + Tailwind CSS
- Cloudflare Pages deployment
- Mobile-first responsive
- Semantic HTML

Page Structure:
1. Hero Section:
   - Service + Location in headline
   - Phone number prominent (click-to-call on mobile)
   - Primary CTA (contact/quote)
   - Professional, trust-building imagery

2. Services Section:
   - 3-6 key services
   - Brief description each
   - No generic fluff

3. Trust Signals:
   - Years in business
   - License/insurance info
   - Service area
   - Certifications

4. Contact Section:
   - Working form (name, email, phone, message)
   - Phone (clickable)
   - Hours
   - Location/map

Quality Requirements:
- [paste base quality prompt]
- Local SEO optimized (location in title, schema markup)
- Click-to-call functional
- Google Maps integration
- Fast loading (target: LCP < 2.5s)

Do not include:
- Generic stock photos
- Excessive animations
- Complex navigation
- Auto-playing anything
```

**See also:** [Business Model Guide](../business-model/README.md)

---

### Portfolio Site Prompt

```
Create a portfolio website for [profession]:

Professional Info:
- Name: [name]
- Profession: [title/role]
- Specialties: [key skills]
- Projects to showcase: [number]

Structure:
1. Brief intro (2-3 sentences, professional)
2. Featured work (best 6-8 projects)
3. Skills/services offered
4. Contact (easy to find)

Design Requirements:
- Work showcased first (not lengthy bio)
- Fast loading (lots of images, optimize)
- Clean, minimal design (work is the star)
- Easy navigation between projects
- Mobile-friendly

Each Project Card:
- Optimized thumbnail image
- Project title
- Brief description (1-2 sentences)
- Link to case study/details
- Tech stack or role

Quality Standards:
- [paste base quality prompt]
- Images optimized (WebP, under 200KB)
- Lazy loading below fold
- No auto-playing media
- Contact clearly accessible

Do not include:
- Excessive personal branding
- Auto-playing portfolio pieces
- Walls of text about yourself
- Complex navigation
- Slow-loading image galleries
```

---

## Integration Patterns

### Adding Quality to Feature Development

**Standard feature prompt:**
```
Add a newsletter signup form to the footer
```

**Quality-enhanced prompt:**
```
Add a newsletter signup form to the footer following these standards:

[paste component quality prompt]

Specific requirements:
- Email input only (don't ask for more)
- Submit button with loading state
- Success/error messages
- Privacy note ("We never spam")
- MailChimp integration (provide endpoint)
- Mobile-optimized input sizing
```

**Result:** Professional component instead of basic implementation.

---

### Adding Quality to Debugging

**Standard debug prompt:**
```
This button isn't working, fix it
```

**Quality-enhanced prompt:**
```
Debug this button and ensure it meets quality standards:

[paste button code]

Check:
1. Event handler attached correctly?
2. Loading state shows during async action?
3. Error handling present?
4. Accessible (keyboard + screen reader)?
5. Consistent with other buttons?
6. Works on mobile (touch target size)?

Fix the issue and improve to meet standards.
```

**Result:** Not just fixed, but improved to professional standard.

---

### Adding Quality to Refactoring

**Standard refactor prompt:**
```
Refactor this component
```

**Quality-enhanced prompt:**
```
Refactor this component to meet quality standards:

[paste component code]

Goals:
1. Extract magic numbers to design tokens
2. Ensure consistent spacing (8pt grid)
3. Make responsive if not already
4. Add proper semantic HTML
5. Improve accessibility
6. Add loading/error states if missing
7. Make more maintainable

Provide:
- Refactored code
- Design tokens used
- What was improved and why
```

**Result:** Professional, maintainable code.

---

## Quality Prompt Templates

### Quick Template: Component Creation

```
Create [component type] with:
- 8pt spacing (8, 16, 24, 32, 48px)
- Border radius: [4px/8px/12px]
- Colors: [brand colors]
- Semantic HTML
- Mobile responsive
- Loading states if interactive
- Accessibility compliant
```

---

### Quick Template: Page Creation

```
Build [page type] with:
- Semantic HTML structure
- Mobile-first responsive
- Meta tags (title, description, OG)
- [specific sections needed]
- No placeholder content
- Professional copy
- Lighthouse 90+ target
```

---

### Quick Template: Quality Review

```
Audit for quality:
[paste code/URL]

Check:
- Design consistency
- Functionality
- Mobile responsive
- Content quality
- Technical/SEO

List issues with priority and fixes.
```

---

## Advanced Quality Patterns

### Progressive Enhancement Prompt

```
Build [feature] with progressive enhancement:

Base (Works Everywhere):
- Semantic HTML
- Works without JavaScript
- Accessible to screen readers
- Mobile-friendly

Enhanced (Modern Browsers):
- CSS animations (subtle)
- JavaScript interactivity
- Loading states
- Real-time validation

Fallbacks:
- Forms submit even if JS fails
- Content readable if CSS doesn't load
- Images have alt text
- No critical functionality requires JS

Quality Standards:
- [paste base quality prompt]
- Test with JS disabled
- Test with slow 3G
```

---

### Design System Integration Prompt

```
Create [component] that integrates with our design system:

Design Tokens:
/* Spacing */
--space-2: 8px;
--space-4: 16px;
--space-6: 24px;
--space-8: 32px;

/* Typography */
--text-sm: 0.875rem;
--text-base: 1rem;
--text-lg: 1.125rem;
--text-xl: 1.25rem;

/* Colors */
--color-primary: #2563eb;
--color-secondary: #64748b;
--color-success: #10b981;
--color-error: #ef4444;

/* Radius */
--radius-sm: 4px;
--radius-md: 8px;
--radius-lg: 12px;

/* Shadows */
--shadow-sm: 0 1px 2px rgba(0,0,0,0.05);
--shadow-md: 0 4px 6px rgba(0,0,0,0.1);
--shadow-lg: 0 10px 15px rgba(0,0,0,0.1);

Requirements:
- Use only these tokens (no arbitrary values)
- Match existing component patterns
- Maintain visual consistency
- Document any new patterns needed
```

---

## Common Mistakes to Avoid

### Mistake 1: Too Vague

```
❌ Bad:
"Make it look good"

✅ Good:
"Apply our spacing system (8pt grid), use brand colors (blue-600 primary),
ensure mobile responsive at 375px"
```

### Mistake 2: Missing Context

```
❌ Bad:
"Create a button"

✅ Good:
"Create a primary CTA button matching our design system:
- Padding: var(--space-3) var(--space-6)
- Background: var(--color-primary)
- Hover: increase elevation
- Include loading state for async actions"
```

### Mistake 3: Forgetting Mobile

```
❌ Bad:
"Build a contact form"

✅ Good:
"Build a contact form:
- Mobile-first responsive
- Touch-friendly inputs (min 44px height)
- Proper input types (tel, email)
- Works at 375px width"
```

---

## Tools & Resources

### Prompt Libraries
- Save your quality prompts as snippets in your IDE
- Create templates for common project types
- Build a personal prompt library

### Testing Prompts
- **Lighthouse** - Verify quality scores
- **WAVE** - Check accessibility
- **Mobile test** - Chrome DevTools responsive mode

### Continuous Improvement
- Track which prompts produce best results
- Refine based on common issues
- Build project-specific variations

---

## Key Takeaways

### Quality is Promptable

**Without quality prompts:**
- AI defaults to "make it work"
- Inconsistent output
- Requires extensive cleanup
- Looks rushed

**With quality prompts:**
- AI produces professional output
- Consistent with standards
- Minimal cleanup needed
- Looks intentional

### Be Specific, Get Quality

**Vague prompts = Vague results**
**Specific standards = Professional results**

### Build Your Prompt Library

**After 5-10 projects:**
- You'll have proven prompt templates
- Faster development
- Consistent quality
- Less revision work

### Quality Prompts = Higher Rates

Professional output from the start:
- Justifies [$300-700 pricing](../business-model/pricing-economics.md)
- Reduces revision cycles
- Builds client confidence
- Creates portfolio pieces

---

**Related Documentation:**
- [Quality Standards](../quality-standards/README.md) - What quality means
- [Design Consistency](../quality-standards/design-consistency.md) - Visual standards
- [Quality Gates](../quality-standards/quality-gates.md) - Pre-ship checklist
- [Task-Specific Patterns](./task-specific-patterns.md) - Feature development prompts
- [Template Library](./template-library.md) - Ready-to-use prompt templates

**Back to:** [Main Guide](../../README.md)
