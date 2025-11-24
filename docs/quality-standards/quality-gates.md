# Quality Gates: Pre-Ship Checklist

The fast checklist to run before shipping any client project. These gates ensure professional quality without slowing down your workflow.

## Why Quality Gates Matter

**For Your Business:**
- Prevents embarrassing mistakes
- Reduces revision requests
- Maintains professional reputation
- Justifies your [pricing](../business-model/pricing-economics.md)

**For Your Workflow:**
- 5-10 minute check before handoff
- Catches 95% of common issues
- Systematic approach prevents forgotten items
- Builds client trust

**The Rule:** No project ships without passing the Critical 7. Project-specific gates depend on type.

---

## The Critical 7 (Non-Negotiable)

Fix these or don't ship. These are deal-breakers.

### 1. All Interactive Elements Work ✅

**What to test:**
```
✓ All buttons trigger actions
✓ All forms submit successfully
✓ All links go to correct destinations
✓ All social media icons link correctly (or are removed)
✓ Modals open AND close
✓ Accordions/dropdowns expand AND collapse
✓ Navigation menu works on mobile
✓ Search works (if present)
✓ Contact form delivers messages
```

**How to test:**
- Click every button
- Fill and submit every form
- Open every modal/dropdown
- Try every link

**Common failures:**
- Social icons linking to "#" or example.com
- Contact forms with no backend
- Broken navigation on mobile
- Modals that won't close

**See also:** [Design Consistency - Functional Elements](./design-consistency.md#functional-interactive-elements)

---

### 2. Mobile Responsive (375px minimum) ✅

**What to test:**
```
✓ No horizontal scrolling
✓ Text readable without zooming
✓ Buttons clickable (not too small)
✓ Images scale properly
✓ Navigation works (hamburger menu functional)
✓ Forms usable on mobile
✓ Content doesn't overflow containers
```

**How to test:**
```
1. Chrome DevTools (F12)
2. Toggle device toolbar (Ctrl+Shift+M)
3. Set to 375px width (iPhone SE)
4. Scroll through entire page
5. Test all interactions
```

**Quick mobile check:**
- Hero section fits without scrolling
- Navigation accessible
- CTA buttons visible and clickable
- Contact info easy to tap
- Forms have proper input types (tel, email)

**Common failures:**
- Fixed-width containers
- Text too small
- Buttons too close together
- Forms with tiny inputs
- Unoptimized images causing slow load

**See also:** [Performance - Mobile Optimization](./performance.md)

---

### 3. Meta Tags Present ✅

**Required tags:**
```html
<!-- Page title (unique, 50-60 chars) -->
<title>Business Name - Service in Location</title>

<!-- Meta description (150-160 chars) -->
<meta name="description" content="Specific description with value proposition">

<!-- Viewport (mobile support) -->
<meta name="viewport" content="width=device-width, initial-scale=1">

<!-- Open Graph (social sharing) -->
<meta property="og:title" content="Business Name - Service">
<meta property="og:description" content="Brief description">
<meta property="og:image" content="https://example.com/og-image.jpg">
<meta property="og:url" content="https://example.com">

<!-- Favicon -->
<link rel="icon" type="image/png" href="/favicon.png">
```

**How to verify:**
```
1. View page source (Ctrl+U)
2. Check <head> section
3. Verify all tags present
4. Test OG image (paste URL in Facebook/LinkedIn preview)
```

**Quick verification:**
- Title shows in browser tab (not "Home" or blank)
- Favicon appears (not default browser icon)
- Share link on social media - correct image/text shows

**See also:** [SEO Guide - Meta Tags](./seo.md)

---

### 4. No Placeholder Content ✅

**What to search for:**
```
Search entire codebase for:
✓ "lorem ipsum"
✓ "test"
✓ "sample"
✓ "TODO"
✓ "placeholder"
✓ "[" (bracket indicates placeholder)
✓ "example.com"
✓ "your-business-name"
```

**How to search:**
```bash
# Search HTML files
grep -r "lorem\|TODO\|test\|sample" .

# Or use your IDE's search (Ctrl+Shift+F)
```

**Common placeholders to remove:**
- Lorem ipsum text
- "Test Heading" or "Sample Section"
- example@example.com
- (555) 555-5555
- "Your business name here"
- TODO comments in production code
- Test images (image-placeholder.jpg)

**Checklist:**
- [ ] All text is real content
- [ ] All contact info accurate
- [ ] All images are real (no placeholders)
- [ ] All business names/addresses correct
- [ ] No developer comments visible

---

### 5. Loading States on Async Actions ✅

**What needs loading states:**
```
✓ Form submissions
✓ "Contact us" buttons
✓ Newsletter signups
✓ Login/authentication
✓ Search functionality
✓ "Load more" buttons
✓ Any API calls
```

**Minimum implementation:**
```javascript
// Button becomes disabled + shows "Loading..."
button.disabled = true;
button.textContent = 'Sending...';

// After action completes
button.disabled = false;
button.textContent = 'Submit';
```

**How to test:**
- Submit forms (watch button state)
- Trigger any async action
- Verify visual feedback appears immediately

**Common failures:**
- Form submission with no feedback
- Button stays clickable during submit
- No indication of progress
- User clicks multiple times (double-submit)

**See also:** [Design Consistency - Loading States](./design-consistency.md#loading-states)

---

### 6. Consistent Spacing & Alignment ✅

**Visual scan checklist:**
```
✓ Sections have even padding top/bottom
✓ Cards in grid align properly
✓ Text blocks aligned consistently
✓ Buttons same size (unless intentional)
✓ Images same aspect ratio in galleries
✓ No elements visually "floating"
✓ Headers/footers consistent across pages
```

**How to check:**
```
1. Zoom out to 50% (Ctrl + -)
2. Scan for visual rhythm
3. Check sections have breathing room
4. Verify grids align
5. Look for spacing inconsistencies
```

**Common issues:**
- Random padding values
- Misaligned grid items
- Sections cramped together
- Inconsistent margins

**Quick fix:**
Use design tokens from your system ([Design Consistency - Spacing](./design-consistency.md#spacing--rhythm-systems))

---

### 7. Real or Zero Testimonials ✅

**Options:**

**Option A - Real testimonials:**
```
✓ Real person name (first and last)
✓ Specific quote (not generic)
✓ Context (job title, location, or identifier)
✓ Real photo (optional but preferred)
```

**Option B - No testimonials section:**
```
✓ Remove section entirely
✓ Replace with other trust signals:
  - Years in business
  - Customer count
  - Certifications/licenses
  - Industry affiliations
```

**How to verify:**
- Read each testimonial - is it specific?
- Check names - full names, not "John D."
- Verify photos - real people or stock?
- Google quote - does it appear on other sites?

**Red flags (remove these):**
- "Great service!" with no context
- AI-generated faces
- Generic names ("Sarah P.")
- Same testimonial on multiple sites
- Stock photo testimonials

**Rule:** One real testimonial > Three fake ones > No testimonials

**See also:** [Design Consistency - Fake Testimonials](./design-consistency.md#fake-or-generic-testimonials)

---

## Project-Type Specific Gates

### Local Business Website

**Context:** Most common project type ([Business Model Guide](../business-model/README.md))

**Additional checks:**

#### Contact Information ✅
- [ ] Phone number correct (test call/text)
- [ ] Click-to-call works on mobile (`tel:` link)
- [ ] Email address correct (send test email)
- [ ] Business hours listed
- [ ] Physical address accurate
- [ ] Google Maps embedded (if applicable)

#### Local SEO ✅
- [ ] Location in page title ("Service in City, State")
- [ ] Service area mentioned in content
- [ ] Schema.org LocalBusiness markup added
- [ ] NAP (Name, Address, Phone) consistent

#### Trust Signals ✅
- [ ] License number displayed (if required)
- [ ] Insurance mentioned (if applicable)
- [ ] Years in business (if established)
- [ ] Service area clearly stated
- [ ] Emergency availability noted (if 24/7)

**Template verification:**
```
Hero Section:
✓ Service clearly stated
✓ Location mentioned
✓ Phone visible (clickable on mobile)
✓ Primary CTA obvious

Services Section:
✓ 3-6 key services listed
✓ Each service described briefly
✓ No generic descriptions

Contact Section:
✓ Form works (test submission)
✓ Phone number clickable
✓ Hours visible
✓ Location/map present
```

**See also:** [Design Consistency - Local Business Standards](./design-consistency.md#local-business-website)

---

### Landing Page / SaaS

**Additional checks:**

#### Value Proposition ✅
- [ ] Clear benefit stated above fold
- [ ] Not generic ("transform your business")
- [ ] Specific to actual product
- [ ] Under 15 words

#### Conversion Elements ✅
- [ ] Primary CTA obvious (one main action)
- [ ] CTA above fold (visible without scrolling)
- [ ] CTA repeated at bottom
- [ ] No competing CTAs confusing user
- [ ] Form fields minimal (name + email only for signup)

#### Social Proof ✅
- [ ] Real testimonials OR removed
- [ ] Customer logos (if applicable)
- [ ] Metrics specific (not "thousands of users")
- [ ] Case studies link to real customers

**Template verification:**
```
Hero:
✓ Value proposition clear
✓ Primary CTA visible
✓ Benefit-focused (not feature-focused)

Features:
✓ 3-4 key features (not 10+)
✓ Each has clear benefit
✓ Visual hierarchy guides eye

Pricing:
✓ Prices clearly stated
✓ CTA on each tier
✓ Differences between tiers obvious
```

---

### Portfolio / Personal Site

**Additional checks:**

#### Work Showcase ✅
- [ ] Projects load quickly (optimized images)
- [ ] Project thumbnails consistent size
- [ ] Each project has title + brief description
- [ ] Best work featured first
- [ ] Case studies link to details

#### Contact Accessibility ✅
- [ ] Email address visible
- [ ] Contact link in header
- [ ] Social profiles linked (if professional)
- [ ] Response time mentioned (optional)

#### Professional Presentation ✅
- [ ] No auto-playing media
- [ ] Resume/CV downloadable (if applicable)
- [ ] Skills listed clearly
- [ ] No excessive personal branding

---

## Performance Gates

Quick performance checks before shipping.

### Lighthouse Quick Audit ✅

**How to run:**
```
1. Chrome DevTools (F12)
2. Lighthouse tab
3. Select: Performance, Accessibility, SEO, Best Practices
4. Device: Mobile
5. Click "Analyze page load"
```

**Minimum scores:**
```
✓ Performance: 85+
✓ Accessibility: 90+
✓ Best Practices: 90+
✓ SEO: 95+
```

**If scores below target:**
- Check [Performance Guide](./performance.md) for optimization
- Common quick fixes: optimize images, remove unused CSS/JS

### Image Optimization ✅

**Quick checks:**
```
✓ All images under 500KB (preferably under 200KB)
✓ Images use modern formats (WebP, AVIF)
✓ Images have width/height attributes (prevents layout shift)
✓ Images have alt text
✓ Hero image loads first (priority)
✓ Below-fold images lazy load
```

**How to verify:**
```
1. Network tab in DevTools
2. Reload page
3. Check image sizes
4. Note load order
```

**Quick optimization:**
```bash
# Convert to WebP (if using Cloudflare Pages, automatic)
# Otherwise use https://squoosh.app/
```

**See also:** [Performance - Image Optimization](./performance.md)

### Core Web Vitals ✅

**Check these metrics:**
```
✓ LCP (Largest Contentful Paint): < 2.5s
✓ FID/INP (First Input Delay): < 100ms
✓ CLS (Cumulative Layout Shift): < 0.1
```

**How to check:**
- Lighthouse report (shows all three)
- Chrome DevTools Performance tab
- [PageSpeed Insights](https://pagespeed.web.dev/)

**Common CLS fixes:**
- Add width/height to images
- Reserve space for dynamic content
- Don't inject content above existing content

**See also:** [Performance - Core Web Vitals](./performance.md)

---

## Accessibility Quick Gates

### Keyboard Navigation ✅

**Test:**
```
1. Click in address bar
2. Press Tab repeatedly
3. Navigate entire page using Tab only
4. Press Enter on buttons/links
```

**Requirements:**
```
✓ Focus indicator visible
✓ Logical tab order
✓ All interactive elements reachable
✓ No keyboard traps (can exit modals)
✓ Skip to content link (optional but good)
```

### Screen Reader Basics ✅

**Quick checks (don't need actual screen reader):**
```html
✓ All images have alt text
✓ Form inputs have labels
✓ Buttons have descriptive text (not just icons)
✓ Links have descriptive text (not "click here")
✓ Heading hierarchy logical (h1 → h2 → h3)
```

**How to verify:**
- Inspect each image: has alt attribute?
- Inspect each form input: has label?
- Check headings: proper hierarchy?

**See also:** [Accessibility Guide](./accessibility.md)

### Color Contrast ✅

**Minimum ratios:**
```
✓ Normal text: 4.5:1
✓ Large text (18pt+): 3:1
✓ UI components: 3:1
```

**How to check:**
```
1. Chrome DevTools
2. Inspect element
3. Color picker shows contrast ratio
```

**Or use:** [WebAIM Contrast Checker](https://webaim.org/resources/contrastchecker/)

---

## SEO Quick Gates

### Page Titles ✅

**Requirements:**
```
✓ Unique per page
✓ 50-60 characters
✓ Includes primary keyword
✓ Format: "Primary Keyword - Brand Name"
```

**Examples:**
```
✅ Good: "Emergency Plumbing Austin TX - Johnson Plumbing"
❌ Bad: "Home - Welcome to Our Website"
```

### Structured Data ✅

**For local businesses:**
```json
{
  "@context": "https://schema.org",
  "@type": "LocalBusiness",
  "name": "Business Name",
  "telephone": "+1-512-555-0123",
  "address": {
    "@type": "PostalAddress",
    "streetAddress": "123 Main St",
    "addressLocality": "Austin",
    "addressRegion": "TX",
    "postalCode": "78701"
  }
}
```

**How to verify:**
- [Google Rich Results Test](https://search.google.com/test/rich-results)
- Paste your URL, check for errors

**See also:** [SEO Guide - Structured Data](./seo.md)

### Sitemap & Robots ✅

**For Astro projects:**
```javascript
// astro.config.mjs
export default defineConfig({
  site: 'https://yourdomain.com',
  integrations: [
    sitemap(), // Auto-generates sitemap.xml
  ],
});
```

**Verify:**
- Visit `https://yourdomain.com/sitemap.xml`
- Should list all pages

**Robots.txt:**
```
User-agent: *
Allow: /

Sitemap: https://yourdomain.com/sitemap.xml
```

---

## Copy Quality Gates

### Hero Copy ✅

**Requirements:**
```
✓ Clear value proposition (not vague)
✓ Specific to business/product
✓ Under 15 words
✓ Mentions target audience or location
```

**Examples:**
```
✅ Good: "Emergency Plumbing in Austin. 30-Min Response, 24/7 Service"
❌ Bad: "Transform Your World Today"
```

**Test:** Could this headline work for a different business?
- If yes → too generic, rewrite

### Footer Text ✅

**Checklist:**
```
✓ Copyright symbol (©) correct
✓ Year current (2024, or auto-update)
✓ Business name spelled correctly
✓ No typos ("All rights reserved" not "All right reversed")
✓ Links work (Privacy Policy, Terms, etc.)
```

**Example:**
```html
<footer>
  <p>&copy; 2024 Johnson Plumbing LLC. All rights reserved.</p>
  <p>Licensed & Insured | License #TX-12345</p>
</footer>
```

---

## Technical Deployment Gates

### Pre-Deploy Checklist ✅

**Environment:**
```
✓ Environment variables set (API keys, etc.)
✓ Production build succeeds (no errors)
✓ No console errors in production build
✓ Analytics configured (Google Analytics, etc.)
✓ Search Console verified
```

**Cloudflare Pages specific:**
```
✓ Custom domain configured
✓ HTTPS automatic (Cloudflare handles this)
✓ Build command correct
✓ Output directory correct
```

**See also:** [Deployment Guide](../workflow/phase-4-deployment.md)

### Post-Deploy Verification ✅

**After deploying:**
```
✓ Site loads at production URL
✓ All pages accessible (no 404s)
✓ Forms submit correctly
✓ Analytics tracking (check real-time)
✓ Images load properly
✓ No mixed content warnings (HTTP on HTTPS)
```

**Quick test:**
```
1. Visit production URL
2. Navigate through all pages
3. Submit contact form (test email)
4. Check mobile view
5. Verify Google Analytics receives data
```

---

## Using This Checklist

### For Each Project Type

**Local Business (most common):**
1. Run Critical 7
2. Run Local Business gates
3. Run Performance gates
4. Ship

**Landing Page:**
1. Run Critical 7
2. Run Landing Page gates
3. Run SEO gates
4. Ship

**Portfolio:**
1. Run Critical 7
2. Run Portfolio gates
3. Run Performance gates (image-heavy)
4. Ship

### Timing

**When to run:**
- Before client review
- Before final deployment
- After any major changes

**How long:**
- Critical 7: 5 minutes
- Project-specific: 5 minutes
- Full checklist: 15-20 minutes

### Automate What You Can

**Automated checks:**
- Lighthouse CI (runs on every deploy)
- Broken link checker
- Image size validator
- Meta tag validator

**See also:** [Testing & Debugging](../workflow/phase-3-testing-debugging.md)

---

## Common Gate Failures

### Top 10 Issues Caught by Gates

1. **Social links to "#"** (Gate 1: Interactive elements)
2. **Mobile horizontal scroll** (Gate 2: Responsive)
3. **Missing meta description** (Gate 3: Meta tags)
4. **Lorem ipsum in footer** (Gate 4: Placeholder text)
5. **No form loading state** (Gate 5: Loading states)
6. **Misaligned grid items** (Gate 6: Spacing)
7. **Generic testimonials** (Gate 7: Testimonials)
8. **Wrong phone number** (Local Business: Contact info)
9. **Generic hero copy** (Copy gates: Hero)
10. **Huge unoptimized images** (Performance: Images)

**Prevention:** Build quality in from the start using [Design Consistency](./design-consistency.md) patterns.

---

## Quick Reference

### 5-Minute Bare Minimum

Can't run full checklist? Hit these:

1. ✅ Click every button and link
2. ✅ Test on mobile (375px width)
3. ✅ Search for "lorem" and "TODO"
4. ✅ Verify contact info correct
5. ✅ Run Lighthouse audit

### Before Client Handoff

**Send this to yourself:**
```
✓ Critical 7 complete
✓ Project-specific gates passed
✓ Lighthouse scores meet targets
✓ Real device testing done
✓ Client's contact info verified
✓ Deployment successful
✓ Post-deploy checks passed
```

---

## Tools for Quality Gates

### Browser Tools
- **Chrome DevTools** - Lighthouse, responsive testing, network analysis
- **WAVE Extension** - Accessibility quick check
- **axe DevTools** - Accessibility audit

### Online Tools
- [PageSpeed Insights](https://pagespeed.web.dev/) - Performance
- [Google Rich Results Test](https://search.google.com/test/rich-results) - Structured data
- [WebAIM Contrast Checker](https://webaim.org/resources/contrastchecker/) - Color contrast
- [Broken Link Checker](https://www.deadlinkchecker.com/) - Find broken links

### Command Line
```bash
# Search for placeholder text
grep -r "lorem\|TODO\|test" .

# Check image sizes (Unix/Mac)
find . -name "*.jpg" -o -name "*.png" | xargs ls -lh

# Find large files
find . -type f -size +500k
```

---

## Key Takeaways

### Gates Prevent Embarrassment

**Without gates:**
- Ship with lorem ipsum
- Broken contact forms
- Wrong phone numbers
- Non-functional buttons
- Unprofessional appearance

**With gates:**
- Consistent quality
- Professional delivery
- Client confidence
- Fewer revisions

### 5 Minutes Saves Hours

**Time investment:**
- 5-10 min: Run gates before ship
- 2-4 hours: Fix issues client finds after delivery

**The math:** Gates are 20x more efficient than post-delivery fixes.

### Build Habits, Not Checklists

**After 5-10 projects:**
- Gates become automatic
- You catch issues while building
- Checklist becomes faster
- Quality becomes default

**Goal:** Internalize the Critical 7 so you never ship without them.

---

**Related Documentation:**
- [Design Consistency Guide](./design-consistency.md) - Prevent issues during development
- [Quality Standards Overview](./README.md) - All quality dimensions
- [Testing & Debugging](../workflow/phase-3-testing-debugging.md) - Deeper testing strategies
- [Quality-Focused Prompts](../prompting/quality-focused-prompts.md) - AI assistance for quality

**Back to:** [Main Guide](../../README.md)
