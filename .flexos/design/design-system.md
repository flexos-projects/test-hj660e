---
type: config
subtype: design-system
title: Design System
---

The design system has TWO parts: TOKENS (exact values, non-negotiable) and CREATIVE DIRECTION (guidelines that inspire, not constrain). This system is designed to bring the BMR Homes brand vibe of **Quiet Confidence** to life.

---

# PART 1: TOKENS (The Builder MUST Use These)

## Colors

The palette is inspired by architectural materials and natural light, creating a sense of calm, sophistication, and trust. It is grounded and premium.

```javascript
// tailwind.config.js
module.exports = {
  theme: {
    extend: {
      colors: {
        primary: { // Slate Blue: Stable, professional, and grounded.
          50: '#F0F4F6',
          100: '#DDE6EA',
          200: '#BCCDD4',
          300: '#9BB3BF',
          400: '#7A9AAD',
          500: '#4A6572',
          600: '#3F5661',
          700: '#354851',
          800: '#2A3A42',
          900: '#1E2B33',
        },
        surface: { // Bone White/Sand: Warm, textural, and light-filled. The canvas for our content.
          50: '#F8F6F2',
          100: '#F1EDE5',
          200: '#E9E2D7',
          300: '#E0D8CA',
          400: '#D0C4B4',
          500: '#C0B19D',
          600: '#AE9D88',
          700: '#90816F',
          800: '#726556',
          900: '#544A3D',
        },
        accent: { // Muted Terracotta: Warm, organic, and human. For purposeful calls-to-action.
          50: '#FDF6F3',
          100: '#FAE9E1',
          200: '#F2D3C4',
          300: '#E9BDA7',
          400: '#E0A789',
          500: '#B85C38',
          600: '#A95432',
          700: '#8F472A',
          800: '#753A22',
          900: '#5C2D1A',
        },
      }
    }
  }
}
```

**Semantic Colors:**

*   **Success:** `#28A745` (A clear, standard green)
*   **Warning:** `#FFC107` (A warm, noticeable amber)
*   **Error:** `#DC3545` (A strong but not overly vibrant red)

**Reasoning:** The `primary` slate blue provides a professional, trustworthy foundation, like a solid blueprint. The `surface` neutrals create a warm, airy canvas, reminiscent of sunlit, high-end interiors. The `accent` terracotta provides a touch of organic warmth for interactive elements, connecting the digital experience to natural building materials.

## Typography

The typography pairs modern structure with classic craftsmanship, reflecting BMR's building philosophy.

*   **Heading Font:** **Poppins** (from Google Fonts). A geometric sans-serif that feels clean, confident, and architectural. Its precision reflects the quality of BMR's work.
*   **Body Font:** **Lora** (from Google Fonts). A contemporary serif with calligraphic roots. It adds a touch of warmth, elegance, and storytelling, making project descriptions and process explanations feel more personal and trustworthy.

**Tailwind Font Size Scale:**

```javascript
// tailwind.config.js
module.exports = {
  theme: {
    fontSize: {
      'xs': ['0.75rem', { lineHeight: '1rem' }],      // 12px
      'sm': ['0.875rem', { lineHeight: '1.25rem' }],   // 14px
      'base': ['1rem', { lineHeight: '1.75rem' }],     // 16px
      'lg': ['1.125rem', { lineHeight: '1.75rem' }],   // 18px
      'xl': ['1.25rem', { lineHeight: '1.75rem' }],   // 20px
      '2xl': ['1.5rem', { lineHeight: '2rem' }],      // 24px
      '3xl': ['1.875rem', { lineHeight: '2.25rem' }],  // 30px
      '4xl': ['2.25rem', { lineHeight: '2.5rem' }],   // 36px
      '5xl': ['3rem', { lineHeight: '1.2' }],         // 48px
      '6xl': ['3.75rem', { lineHeight: '1.2' }],        // 60px
    },
  }
}
```

**Font Weight Usage:**

*   `font-light` (300): Can be used for tertiary text like captions or metadata.
*   `font-normal` (400): The default for all body copy (Lora).
*   `font-medium` (500): For UI elements like navigation links or button text.
*   `font-semibold` (600): The default for all headings (Poppins).
*   `font-bold` (700): For primary, high-impact headlines (`h1`).

## Spacing

Generous spacing is key to the premium, uncluttered, "architectural magazine" feel.

*   **Section Vertical Padding:** Generous. Use `py-24` (96px) or `py-32` (128px) between major content sections.
*   **Content Max-Width:** `1280px` (`max-w-7xl`). This provides an expansive, cinematic canvas for photography.
*   **Container Horizontal Padding:** Start with `px-6` on mobile and expand to `sm:px-8` on larger screens.

## Shapes

Shapes should be clean, precise, and understated.

*   **Border Radius:** Use sparingly to convey precision.
    *   `rounded-none`: For large containers and image frames to maintain a sharp, architectural look.
    *   `rounded-md` (6px): For buttons and input fields to give them a finished, tactile feel.
    *   `rounded-lg` (8px): For content cards (e.g., project portfolio items) to slightly soften them.
*   **Shadow Style:** Subtle and realistic. Use shadows to indicate elevation or interactivity, not for decoration.
    *   `shadow-md`: For static cards to provide subtle depth.
    *   `shadow-xl`: On hover states to create a clear "lift" effect.
    *   Avoid hard, dark, or colored shadows.

---

# PART 2: CREATIVE DIRECTION (Inspire the Builder)

## Visual Personality
**Sophisticated, Calm, Trustworthy, Premium**

Every component, layout, and interaction should feel considered and intentional. The site should instill a sense of calm confidence in the visitor, assuring them they are in the hands of experts.

## Animation & Motion Language

Motion should be **smooth, subtle, and elegant**, reinforcing the brand's quiet confidence. It should feel like a well-engineered drawer closing softly, not a slamming door.

*   **Page transitions**: A simple, quick cross-fade (`opacity`).
*   **Scroll animations**: Gentle fade-up and slide-in for new sections and images as they enter the viewport. Staggered animations for lists or galleries can add a touch of editorial flair.
*   **Hover effects**: A subtle "lift" using a larger shadow (`hover:shadow-xl`) and a gentle scale (`hover:scale-[1.02]`). Links can have a simple color shift to the accent color.
*   **Micro-interactions**: Form fields should subtly glow with the primary color on focus. Button presses should have a gentle `scale(0.98)` transform.
*   **Speed**: **Smooth** (300-400ms).
*   **Easing**: **`ease-in-out`** for an elegant, graceful feel.

**CSS/Tailwind Examples:**
1.  **Card Hover Lift:** `transition duration-300 ease-in-out hover:shadow-xl hover:-translate-y-1`
2.  **Fade-in on Scroll (requires JS intersection observer):** An element starts with `opacity-0 translate-y-4` and transitions to `opacity-100 translate-y-0` when it becomes visible.
3.  **CTA Button:** `transition-transform duration-200 ease-in-out active:scale-95`

## Layout Philosophy

The layout is **editorial and spacious**, treating content like a feature in a high-end design magazine.

*   **Whitespace:** Extremely generous. It's the most important tool for creating a premium feel. Use it to frame photography and give text room to breathe.
*   **Grid Rhythm:** Based on a structured 12-column grid for alignment and order, but feel free to break from it for asymmetrical layouts that create visual interest and guide the eye. Overlap images and text blocks where appropriate.
*   **Image Treatment:** Photography is the hero. Use full-bleed sections, large-format images, and dynamic grids. Avoid trapping photos in small boxes.
*   **Section Rhythm:** Alternate between light (`bg-surface-50`) and dark (`bg-primary-900`) sections to create contrast and define distinct narrative moments on a page.
*   **Mobile Approach:** A simplified single column that maintains the generous spacing and strong typographic hierarchy. The premium feel must not be lost.

## Photography & Image Style

The visual language is built on **aspirational and authentic** project photography.

*   **Style:** Exclusively high-resolution, professional photography of BMR's completed projects. No stock photos. Ever.
*   **Color Treatment:** Bright, airy, and focused on natural light. Colors should be true-to-life and vibrant.
*   **Subject Matter:** A mix of wide, environmental shots that show the transformation of a space, and tight, detailed shots that highlight material quality and craftsmanship (e.g., tile work, joinery, fixtures).

## Inspiration References

1.  **Studio McGee (`studiomcgee.com`):** Borrow their editorial storytelling approach. Note how they mix large hero images with smaller detail shots and elegant typography to create compelling project case studies.
2.  **Olson Kundig (`olsonkundig.com`):** Emulate their bold, confident use of full-screen photography and minimalist UI. Their site feels like an art gallery, positioning them as masters of their craft.
3.  **Sonos (`sonos.com`):** Learn from their masterful use of whitespace, product photography, and subtle, polished micro-interactions. They sell a premium product with a calm, confident, and clean digital experience.

## Do's and Don'ts

**DO:**
*   **Do** make professional project photography the hero of every page.
*   **Do** use generous whitespace as a primary design tool to create a premium feel.
*   **Do** lean on the typographic pairing (Poppins + Lora) to balance modern precision with storytelling warmth.
*   **Do** create visual rhythm by alternating between light and dark background sections.
*   **Do** tell a story of transformation, using before-and-after galleries where possible.

**DON'T:**
*   **Don't** use any stock photography or generic icons. Authenticity is paramount.
*   **Don't** clutter layouts. When in doubt, remove an element.
*   **Don't** use loud, distracting animations or overly bright, saturated colors.
*   **Don't** use heavy drop shadows, thick borders, or gradients.
*   **Don't** be afraid of asymmetry in layouts to create a more dynamic, editorial feel.