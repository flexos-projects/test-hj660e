---
type: config
subtype: design-patterns
title: Component Patterns
---

This document serves as a recipe book for building consistent, high-quality pages for BMR Homes. It translates the "Quiet Confidence" design system into practical, reusable components and patterns using Astro and Tailwind CSS. The aim is to empower builders to create diverse yet cohesive pages, adhering to the brand's aesthetic without rigid templates.

---

## 1. Section Wrapper

The foundational container for every major content block on a page. It ensures consistent horizontal alignment, maximum width, and vertical rhythm, bringing a premium, spacious feel.

#### Description
This wrapper defines the core layout structure for all sections, providing generous padding and controlling content width for an editorial look. It acts as the canvas upon which all other patterns are placed.

#### Tailwind/CSS Classes
```html
<!-- Default Section Wrapper -->
<section class="py-24 bg-surface-50 lg:py-32">
  <div class="max-w-7xl mx-auto px-6 sm:px-8">
    <!-- Your content goes here -->
  </div>
</section>

<!-- Example for Dark Section Wrapper -->
<section class="py-24 bg-primary-900 text-surface-50 lg:py-32">
  <div class="max-w-7xl mx-auto px-6 sm:px-8">
    <!-- Your content goes here -->
  </div>
</section>
```

#### HTML Structure Sketch
```html
<section class="[section-bg-color] [vertical-padding]">
  <div class="max-w-7xl mx-auto px-6 sm:px-8">
    <!-- CONTENT OF THE SECTION -->
  </div>
</section>
```

#### Responsive Behavior
*   `py-24` (96px) for mobile/tablet, `lg:py-32` (128px) for desktop ensures generous vertical spacing.
*   `px-6` (24px) for mobile, `sm:px-8` (32px) for larger screens provides consistent horizontal margins.
*   `max-w-7xl` (1280px) keeps content readable and cinematic on very large screens.

#### Animation/Interaction Notes
*   Individual elements within the wrapper can utilize scroll-reveal animations. The wrapper itself generally remains static.

#### Variations

##### Variation 1: Light Canvas
This is the default, most common wrapper, providing a bright and airy backdrop.
```html
<section class="py-24 bg-surface-50 text-primary-700 font-body lg:py-32">
  <div class="max-w-7xl mx-auto px-6 sm:px-8">
    <h2 class="text-4xl font-heading font-semibold text-primary-900 mb-8">Section Title</h2>
    <p>This section provides a warm, natural light-filled canvas for your primary content.</p>
  </div>
</section>
```

##### Variation 2: Dark & Grounded
Used to create visual contrast and define distinct narrative moments, often for impact or to frame key messages.
```html
<section class="py-24 bg-primary-900 text-surface-50 font-body lg:py-32">
  <div class="max-w-7xl mx-auto px-6 sm:px-8">
    <h2 class="text-4xl font-heading font-semibold text-surface-50 mb-8">Impactful Statement Here</h2>
    <p>Utilize this dark canvas to draw attention, creating a sophisticated and grounded atmosphere.</p>
  </div>
</section>
```

##### Variation 3: Accent Header
A subtle variation where the section title is aligned to the brand accent color, usually to highlight a particular theme or category within the section.
```html
<section class="py-24 bg-surface-50 text-primary-700 font-body lg:py-32">
  <div class="max-w-7xl mx-auto px-6 sm:px-8">
    <h2 class="text-lg font-heading font-medium text-accent-500 mb-2">Category</h2>
    <h3 class="text-3xl font-heading font-semibold text-primary-900 mb-8">Sub-Section Title</h3>
    <p>This allows for a subtle splash of warmth and emphasis before a deeper dive into content.</p>
  </div>
</section>
```

---

## 2. Hero Variants

Hero sections set the tone for the entire page, communicating the brand's quiet confidence. They are designed to be impactful and aspirational.

#### Responsive Behavior
*   All hero variants prioritize mobile-first, ensuring content remains readable and photography impactful. Stacking and fluid imagery are key.
*   Content within the hero scales with `max-w-md`, `max-w-lg` to prevent text from spanning too wide.

#### Animation/Interaction Notes
*   **Entrance:** Hero content should gently fade-in and slightly slide-up on page load. (`opacity-0 translate-y-4` to `opacity-100 translate-y-0`)
*   **Scroll Indicator:** A subtle indicator (e.g., an arrow or "Scroll Down" text) can fade-in with the content.
*   **Image/Video:** Backgrounds can have subtle `parallax` scrolling (requires JS) or simply full-bleed display.

#### Variations

##### Variation 1: Impact Hero (Full-Viewport)
A bold, immersive experience with full-bleed photography/video and commanding typography. Ideal for homepages and key landing pages.

###### Tailwind/CSS Classes
```html
<section class="relative h-screen flex items-center justify-center text-surface-50 overflow-hidden">
  <!-- Background Image/Video -->
  <div class="absolute inset-0 z-0">
    <img src="/path/to/hero-image.jpg" alt="Aspirational BMR Home" class="w-full h-full object-cover">
    <div class="absolute inset-0 bg-primary-900 opacity-60"></div> <!-- Dark overlay -->
  </div>

  <!-- Content -->
  <div class="relative z-10 text-center max-w-4xl px-6 sm:px-8 animate-fade-in-up">
    <h1 class="font-heading font-bold text-5xl md:text-6xl mb-4 leading-tight">Crafting Spaces, Building Legacies.</h1>
    <p class="font-body text-lg md:text-xl max-w-2xl mx-auto mb-8 opacity-90">Experience the BMR difference: precision, passion, and unparalleled quality in every detail.</p>
    <a href="/projects" class="inline-block bg-accent-500 text-surface-50 font-medium font-heading py-3 px-8 rounded-md hover:bg-accent-600 transition duration-300 ease-in-out active:scale-95 shadow-lg hover:shadow-xl">View Our Projects</a>
  </div>

  <!-- Scroll Indicator -->
  <div class="absolute bottom-8 left-1/2 -translate-x-1/2 z-10 text-surface-50 animate-bounce-subtle hidden md:block">
    <span class="sr-only">Scroll Down</span>
    <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 14l-7 7m0 0l-7-7m7 7V3"></path></svg>
  </div>
</section>
```

##### Variation 2: Split Hero (Image & Content)
Balances strong imagery with clear, concise messaging. Ideal for service pages or about us sections.

###### Tailwind/CSS Classes
```html
<section class="relative bg-surface-50 text-primary-900 py-24 md:py-32">
  <div class="max-w-7xl mx-auto px-6 sm:px-8 grid md:grid-cols-2 gap-12 items-center">
    <!-- Image Column (Left on Desktop, Top on Mobile) -->
    <div class="relative order-2 md:order-1 animate-fade-in-left">
      <img src="/path/to/split-hero-image.jpg" alt="Beautifully designed interior" class="w-full h-auto rounded-none shadow-md">
    </div>

    <!-- Content Column (Right on Desktop, Bottom on Mobile) -->
    <div class="order-1 md:order-2 text-center md:text-left animate-fade-in-right">
      <h1 class="font-heading font-bold text-4xl md:text-5xl mb-4 leading-tight">Masterful Craftsmanship, Tailored to You.</h1>
      <p class="font-body text-lg text-primary-700 mb-8">From concept to completion, we bring your vision to life with meticulous attention to detail and unwavering quality.</p>
      <a href="/contact" class="inline-block bg-accent-500 text-surface-50 font-medium font-heading py-3 px-8 rounded-md hover:bg-accent-600 transition duration-300 ease-in-out active:scale-95 shadow-lg hover:shadow-xl">Start Your Project</a>
    </div>
  </div>
</section>
```

##### Variation 3: Minimal Hero (Text-Centered)
A clean, elegant, text-focused hero on a solid or subtle gradient background. For pages where text is paramount, like a blog index or legal page.

###### Tailwind/CSS Classes
```html
<section class="bg-gradient-to-br from-surface-50 via-surface-100 to-surface-200 text-primary-900 py-24 md:py-32 text-center">
  <div class="max-w-3xl mx-auto px-6 sm:px-8 animate-fade-in-up">
    <h1 class="font-heading font-bold text-4xl md:text-5xl mb-4 leading-tight">Our Story: Built on Integrity.</h1>
    <p class="font-body text-lg text-primary-700 mb-8">For decades, BMR Homes has been synonymous with quality, trust, and a commitment to excellence that stands the test of time.</p>
    <a href="/about" class="inline-block border border-primary-500 text-primary-500 font-medium font-heading py-3 px-8 rounded-md hover:bg-primary-50 hover:text-primary-700 transition duration-300 ease-in-out active:scale-95">Learn More About Us</a>
  </div>
</section>
```

---

## 3. Content Blocks

These are the workhorses of any page, offering versatile ways to present information, features, and calls to action.

### 3.1 Text + Image (Alternating)

#### Description
This pattern alternates the position of text and images to create visual interest and guide the eye through long-form content. It emphasizes the quality of BMR's photography while maintaining readability.

#### Tailwind/CSS Classes
```html
<section class="py-24 bg-surface-50 text-primary-700 lg:py-32">
  <div class="max-w-7xl mx-auto px-6 sm:px-8 space-y-20 lg:space-y-32">

    <!-- Block 1: Image Left, Text Right -->
    <div class="grid md:grid-cols-2 gap-12 items-center">
      <div class="order-2 md:order-1 animate-fade-in-left">
        <img src="/path/to/project-detail-1.jpg" alt="Luxurious kitchen design" class="w-full h-auto rounded-none shadow-md">
      </div>
      <div class="order-1 md:order-2 animate-fade-in-right">
        <h3 class="font-heading font-semibold text-3xl text-primary-900 mb-4">Precision in Every Detail</h3>
        <p class="font-body text-lg">Our commitment to excellence is evident in every joint, every finish, and every carefully selected material. We believe true luxury lies in the flawless execution of design.</p>
      </div>
    </div>

    <!-- Block 2: Image Right, Text Left -->
    <div class="grid md:grid-cols-2 gap-12 items-center">
      <div class="order-2 md:order-2 animate-fade-in-right">
        <img src="/path/to/project-detail-2.jpg" alt="Spacious living room with natural light" class="w-full h-auto rounded-none shadow-md">
      </div>
      <div class="order-1 md:order-1 animate-fade-in-left">
        <h3 class="font-heading font-semibold text-3xl text-primary-900 mb-4">Thoughtful Design, Timeless Living</h3>
        <p class="font-body text-lg">We create spaces that are not just beautiful, but deeply functional and enduring. Our designs harmonize with their environment and enhance daily life.</p>
      </div>
    </div>

  </div>
</section>
```

#### HTML Structure Sketch
```html
<section class="section-wrapper">
  <div class="grid md:grid-cols-2 gap-x gap-y items-center">
    <div class="order-mobile md:order-desktop"> <!-- Image --> </div>
    <div class="order-mobile md:order-desktop"> <!-- Text --> </div>
  </div>
  <!-- ... repeat for alternating blocks ... -->
</section>
```

#### Responsive Behavior
*   `grid md:grid-cols-2` ensures a single column on mobile, transitioning to two columns on medium screens and above.
*   `order-` classes control the stacking on mobile vs. desktop for alternating patterns.
*   Images are fluid (`w-full h-auto`).

#### Animation/Interaction Notes
*   **Scroll-reveal:** Each image and text block should animate in subtly as it enters the viewport. `animate-fade-in-left` and `animate-fade-in-right` are good choices.

#### Variations

##### Variation 1: Standard (Image Left/Right)
As shown above, alternating image positions.

##### Variation 2: Overlapping Image
A more dynamic, editorial look where the image slightly overlaps the surrounding grid. (Requires careful `z-index` and `margin` adjustments, potentially in a custom component.)
```html
<div class="grid md:grid-cols-2 gap-x-8 items-center relative py-12">
  <div class="relative order-2 md:order-1 col-span-2 md:col-span-1 md:pr-12 animate-fade-in-left">
    <img src="/path/to/project-detail-overlapping.jpg" alt="Modern home interior" class="w-full h-auto rounded-none shadow-lg md:absolute md:top-1/2 md:-translate-y-1/2 md:right-0 md:max-w-[120%]">
  </div>
  <div class="order-1 md:order-2 md:pl-24 z-10 animate-fade-in-right">
    <h3 class="font-heading font-semibold text-3xl text-primary-900 mb-4">Dynamic Visual Storytelling</h3>
    <p class="font-body text-lg">This layout breaks the grid subtly, creating a sophisticated magazine aesthetic that draws the eye.</p>
  </div>
</div>
```
*(Note: The actual implementation of `md:max-w-[120%]` and negative margins for true overlap might require careful custom CSS if Tailwind's utility classes don't directly support the exact aesthetic, or dedicated custom Tailwind classes like `md:clip-left-10` that extend `margin-right`.)*

##### Variation 3: Image with Caption
Adds a small, elegant caption below the image, enhancing the editorial feel.
```html
<div class="grid md:grid-cols-2 gap-12 items-center">
  <div class="order-2 md:order-1 animate-fade-in-left">
    <img src="/path/to/project-detail-caption.jpg" alt="Elegant bathroom fixtures" class="w-full h-auto rounded-none shadow-md mb-2">
    <p class="font-body text-sm text-primary-500 italic">Capturing the refined details of our craftsmanship.</p>
  </div>
  <div class="order-1 md:order-2 animate-fade-in-right">
    <h3 class="font-heading font-semibold text-3xl text-primary-900 mb-4">Attention to Finishes</h3>
    <p class="font-body text-lg">The tactile experience of our spaces is paramount. We select and install materials that delight the senses and endure gracefully.</p>
  </div>
</div>
```

---

### 3.2 Feature Grid (Icon + Heading + Text)

#### Description
A versatile grid layout for showcasing services, benefits, or key aspects of a project. Uses clean icons, clear headings, and concise descriptions.

#### Tailwind/CSS Classes
```html
<section class="py-24 bg-surface-50 text-primary-700 lg:py-32">
  <div class="max-w-7xl mx-auto px-6 sm:px-8">
    <h2 class="font-heading font-bold text-4xl text-center text-primary-900 mb-12">Our Core Strengths</h2>
    <div class="grid sm:grid-cols-2 lg:grid-cols-3 gap-10">

      <!-- Feature Item 1 -->
      <div class="text-center animate-fade-in-up" style="animation-delay: 100ms;">
        <div class="inline-block p-4 rounded-lg bg-primary-100 text-primary-700 mb-6">
          <!-- Icon (replace with actual SVG or icon component) -->
          <svg class="w-10 h-10" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M9 19v-6a2 2 0 00-2-2H5a2 2 0 00-2 2v6a2 2 0 002 2h2a2 2 0 002-2zm0 0V9a2 2 0 012-2h2a2 2 0 012 2v10m-6 0a2 2 0 002 2h2a2 2 0 002-2m0 0V5a2 2 0 012-2h2a2 2 0 012 2v14a2 2 0 01-2 2h-2a2 2 0 01-2-2z"></path></svg>
        </div>
        <h3 class="font-heading font-semibold text-xl text-primary-900 mb-3">Exceptional Design</h3>
        <p class="font-body text-base">We collaborate with leading architects to create homes that are both stunning and highly functional.</p>
      </div>

      <!-- Feature Item 2 (similar structure) -->
      <div class="text-center animate-fade-in-up" style="animation-delay: 200ms;">
        <div class="inline-block p-4 rounded-lg bg-primary-100 text-primary-700 mb-6">
          <svg class="w-10 h-10" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M12 6V4m0 2a2 2 0 100 4m0-4a2 2 0 110 4m-6 8a2 2 0 100-4m0 4a2 2 0 110-4m0 4v2m0-6V4m6 6v10m6-2a2 2 0 100-4m0 4a2 2 0 110-4m0 4v2m0-6V4"></path></svg>
        </div>
        <h3 class="font-heading font-semibold text-xl text-primary-900 mb-3">Meticulous Craftsmanship</h3>
        <p class="font-body text-base">Our skilled tradesmen uphold the highest standards, ensuring every detail is executed with precision.</p>
      </div>

      <!-- Feature Item 3 (similar structure) -->
      <div class="text-center animate-fade-in-up" style="animation-delay: 300ms;">
        <div class="inline-block p-4 rounded-lg bg-primary-100 text-primary-700 mb-6">
          <svg class="w-10 h-10" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M12 8c-1.657 0-3 .895-3 2s1.343 2 3 2 3 .895 3 2-1.343 2-3 2m0-8c1.11 0 2.08.402 2.599 1L21 6h2m-2 2v4m-7 0v8h8a2 2 0 002-2v-8z"></path></svg>
        </div>
        <h3 class="font-heading font-semibold text-xl text-primary-900 mb-3">Seamless Project Management</h3>
        <p class="font-body text-base">We ensure a smooth, transparent process from initial consultation to the final handover.</p>
      </div>

    </div>
  </div>
</section>
```

#### HTML Structure Sketch
```html
<section class="section-wrapper">
  <h2 class="section-title"></h2>
  <div class="grid [responsive-columns] gap-x gap-y">
    <div class="feature-item">
      <div class="icon-wrapper"> <!-- SVG Icon --> </div>
      <h3 class="feature-heading"></h3>
      <p class="feature-description"></p>
    </div>
    <!-- ... more feature items ... -->
  </div>
</section>
```

#### Responsive Behavior
*   `grid sm:grid-cols-2 lg:grid-cols-3` provides a responsive column layout (1 column on xs, 2 on sm, 3 on lg).
*   Text is centered (`text-center`).

#### Animation/Interaction Notes
*   **Scroll-reveal:** Each feature item should animate in with a slight stagger using `animate-fade-in-up` and increasing `animation-delay` for each item.

#### Variations

##### Variation 1: Standard Centered
As shown above, icons and text centered.

##### Variation 2: Left-Aligned
Features aligned to the left, often paired with a section title.
```html
<div class="grid sm:grid-cols-2 lg:grid-cols-3 gap-10">
  <div class="text-left animate-fade-in-up" style="animation-delay: 100ms;">
    <div class="inline-block p-4 rounded-lg bg-primary-100 text-primary-700 mb-6">
      <svg class="w-10 h-10" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M13 10V3L4 14h7v7l9-11h-7z"></path></svg>
    </div>
    <h3 class="font-heading font-semibold text-xl text-primary-900 mb-3">Agile Project Cycles</h3>
    <p class="font-body text-base">Our streamlined process ensures efficient delivery without compromising quality.</p>
  </div>
  <!-- ... other items ... -->
</div>
```

##### Variation 3: With Accent Highlight
The feature icon or heading uses the accent color for additional emphasis.
```html
<div class="grid sm:grid-cols-2 lg:grid-cols-3 gap-10">
  <div class="text-center animate-fade-in-up" style="animation-delay: 100ms;">
    <div class="inline-block p-4 rounded-lg bg-accent-100 text-accent-700 mb-6">
      <svg class="w-10 h-10" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M17 20h5v-2a3 3 0 00-5.356-1.857M17 20H2v-2a4 4 0 014-4h12.55M18 12a4 4 0 11-8 0 4 4 0 018 0z"></path></svg>
    </div>
    <h3 class="font-heading font-semibold text-xl text-accent-700 mb-3">Client-Centric Approach</h3>
    <p class="font-body text-base">Your vision is at the heart of everything we do, ensuring a truly personalized experience.</p>
  </div>
  <!-- ... other items ... -->
</div>
```

---

### 3.3 Stats/Numbers Bar

#### Description
A dynamic way to showcase key achievements or figures, designed to animate on scroll, adding a subtle touch of engaging confidence.

#### Tailwind/CSS Classes
```html
<section class="py-24 bg-primary-900 text-surface-50 lg:py-32">
  <div class="max-w-7xl mx-auto px-6 sm:px-8">
    <div class="grid sm:grid-cols-2 lg:grid-cols-4 gap-10 text-center">

      <!-- Stat Item 1 -->
      <div class="animate-fade-in-up" data-animate-count="25" data-count-prefix="+" data-count-suffix=" Years">
        <p class="font-heading font-bold text-5xl text-accent-500 mb-2" id="stat-1">0</p>
        <p class="font-body text-xl font-medium">Experience in Luxury Builds</p>
      </div>

      <!-- Stat Item 2 -->
      <div class="animate-fade-in-up" data-animate-count="150" data-count-prefix="+" data-count-suffix=" Homes">
        <p class="font-heading font-bold text-5xl text-accent-500 mb-2" id="stat-2">0</p>
        <p class="font-body text-xl font-medium">Delivered to Delighted Clients</p>
      </div>

      <!-- Stat Item 3 -->
      <div class="animate-fade-in-up" data-animate-count="98" data-count-prefix="" data-count-suffix="% Satisfaction">
        <p class="font-heading font-bold text-5xl text-accent-500 mb-2" id="stat-3">0</p>
        <p class="font-body text-xl font-medium">Client Satisfaction Rate</p>
      </div>

      <!-- Stat Item 4 -->
      <div class="animate-fade-in-up" data-animate-count="300" data-count-prefix="$" data-count-suffix="M+">
        <p class="font-heading font-bold text-5xl text-accent-500 mb-2" id="stat-4">0</p>
        <p class="font-body text-xl font-medium">Total Project Value</p>
      </div>

    </div>
  </div>
</section>

<!-- Required JS for count-up animation (example) -->
<script>
  function animateCount(targetId, start, end, duration, prefix = '', suffix = '') {
    const obj = document.getElementById(targetId);
    let current = start;
    const range = end - start;
    const increment = end > start ? 1 : -1;
    const stepTime = Math.abs(Math.floor(duration / range));

    const timer = setInterval(() => {
      current += increment;
      obj.textContent = prefix + current + suffix;
      if ((increment > 0 && current >= end) || (increment < 0 && current <= end)) {
        clearInterval(timer);
        obj.textContent = prefix + end + suffix; // Ensure final value is exact
      }
    }, stepTime);
  }

  const observerOptions = {
    root: null,
    rootMargin: '0px',
    threshold: 0.5 // Trigger when 50% of the item is visible
  };

  const statObserver = new IntersectionObserver((entries, observer) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        const item = entry.target;
        const count = parseInt(item.dataset.animateCount);
        const prefix = item.dataset.countPrefix || '';
        const suffix = item.dataset.countSuffix || '';
        const targetId = item.querySelector('p:first-child').id; // Get ID of the P tag

        animateCount(targetId, 0, count, 2000, prefix, suffix); // Animate from 0 to target over 2 seconds
        observer.unobserve(item); // Only animate once
      }
    });
  }, observerOptions);

  document.querySelectorAll('[data-animate-count]').forEach(item => {
    statObserver.observe(item);
  });
</script>
```

#### HTML Structure Sketch
```html
<section class="section-wrapper [bg-color]">
  <div class="grid [responsive-columns] text-center">
    <div class="stat-item" data-animate-count="[number]" data-count-prefix="" data-count-suffix="">
      <p class="number"></p>
      <p class="label"></p>
    </div>
    <!-- ... more stat items ... -->
  </div>
</section>
```

#### Responsive Behavior
*   `grid sm:grid-cols-2 lg:grid-cols-4` provides responsive columns (1 on xs, 2 on sm, 4 on lg).
*   Text is centered (`text-center`).

#### Animation/Interaction Notes
*   **Scroll-reveal:** The numbers animate up (`data-animate-count`) when the section enters the viewport, using JavaScript with an Intersection Observer. Each stat item also fades in (`animate-fade-in-up`).

#### Variations

##### Variation 1: Dark Background (Default)
As shown above, `bg-primary-900` provides a strong contrast for the numbers.

##### Variation 2: Light Background
For sections where a lighter tone is desired, with `primary` text.
```html
<section class="py-24 bg-surface-50 text-primary-900 lg:py-32">
  <div class="max-w-7xl mx-auto px-6 sm:px-8">
    <div class="grid sm:grid-cols-2 lg:grid-cols-4 gap-10 text-center">
      <div class="animate-fade-in-up" data-animate-count="25" data-count-prefix="+" data-count-suffix=" Years">
        <p class="font-heading font-bold text-5xl text-primary-700 mb-2" id="stat-a">0</p>
        <p class="font-body text-xl font-medium">Experience in Luxury Builds</p>
      </div>
      <!-- ... other items ... -->
    </div>
  </div>
</section>
```

---

### 3.4 Testimonial

#### Description
Showcases client feedback with elegance and gravitas, building trust and credibility. The quote takes center stage, followed by clear attribution.

#### Tailwind/CSS Classes
```html
<section class="py-24 bg-surface-100 text-primary-900 lg:py-32">
  <div class="max-w-4xl mx-auto px-6 sm:px-8 text-center animate-fade-in-up">
    <blockquote class="mb-8 relative pb-8 after:content-[''] after:absolute after:bottom-0 after:left-1/2 after:-translate-x-1/2 after:w-20 after:h-0.5 after:bg-primary-300">
      <p class="font-body text-3xl italic text-primary-700 leading-relaxed">
        "BMR Homes delivered beyond our wildest expectations. Their team's dedication to quality and their seamless process made building our dream home a truly enjoyable experience."
      </p>
    </blockquote>
    <p class="font-heading font-medium text-xl text-primary-900 mb-1">- Jane & John Doe</p>
    <p class="font-body text-lg text-primary-500">Satisfied Homeowners, Aspen Grove</p>
  </div>
</section>
```

#### HTML Structure Sketch
```html
<section class="section-wrapper [bg-color]">
  <div class="max-w-md mx-auto text-center">
    <blockquote class="quote-style">
      <p class="quote-text"></p>
    </blockquote>
    <p class="author"></p>
    <p class="title/location"></p>
  </div>
</section>
```

#### Responsive Behavior
*   Content is always centered and constrained by `max-w-4xl`.
*   Font sizes scale appropriately from mobile to desktop.

#### Animation/Interaction Notes
*   **Scroll-reveal:** The entire testimonial block should fade-in and slide up gently (`animate-fade-in-up`).

#### Variations

##### Variation 1: Standard (Default)
As shown above, italic serif quote with clean attribution.

##### Variation 2: With Star Rating
Adds a visual star rating for quick credibility.
```html
<div class="max-w-4xl mx-auto px-6 sm:px-8 text-center animate-fade-in-up">
  <div class="flex justify-center mb-4">
    <!-- Star Icons (replace with actual SVG or icon component) -->
    <svg class="w-6 h-6 text-accent-500 fill-current" viewBox="0 0 20 20"><path d="M10 15.27L16.18 19l-1.64-7.03L20 7.24l-7.19-.61L10 0 7.19 6.63 0 7.24l5.46 4.73L3.82 19z"/></svg>
    <svg class="w-6 h-6 text-accent-500 fill-current" viewBox="0 0 20 20"><path d="M10 15.27L16.18 19l-1.64-7.03L20 7.24l-7.19-.61L10 0 7.19 6.63 0 7.24l5.46 4.73L3.82 19z"/></svg>
    <svg class="w-6 h-6 text-accent-500 fill-current" viewBox="0 0 20 20"><path d="M10 15.27L16.18 19l-1.64-7.03L20 7.24l-7.19-.61L10 0 7.19 6.63 0 7.24l5.46 4.73L3.82 19z"/></svg>
    <svg class="w-6 h-6 text-accent-500 fill-current" viewBox="0 0 20 20"><path d="M10 15.27L16.18 19l-1.64-7.03L20 7.24l-7.19-.61L10 0 7.19 6.63 0 7.24l5.46 4.73L3.82 19z"/></svg>
    <svg class="w-6 h-6 text-accent-500 fill-current" viewBox="0 0 20 20"><path d="M10 15.27L16.18 19l-1.64-7.03L20 7.24l-7.19-.61L10 0 7.19 6.63 0 7.24l5.46 4.73L3.82 19z"/></svg>
  </div>
  <blockquote class="mb-8 relative pb-8 after:content-[''] after:absolute after:bottom-0 after:left-1/2 after:-translate-x-1/2 after:w-20 after:h-0.5 after:bg-primary-300">
    <p class="font-body text-3xl italic text-primary-700 leading-relaxed">
      "Absolutely thrilled with our BMR home. The five-star service and impeccable finish are unmatched."
    </p>
  </blockquote>
  <p class="font-heading font-medium text-xl text-primary-900 mb-1">- Satisfied Client</p>
</div>
```

##### Variation 3: Large, Hero Testimonial (often for a dark section)
A very prominent testimonial, often on a dark background for strong impact, with a larger font size.
```html
<section class="py-24 bg-primary-900 text-surface-50 lg:py-32">
  <div class="max-w-5xl mx-auto px-6 sm:px-8 text-center animate-fade-in-up">
    <blockquote class="mb-10 relative pb-10 after:content-[''] after:absolute after:bottom-0 after:left-1/2 after:-translate-x-1/2 after:w-24 after:h-0.5 after:bg-surface-300">
      <p class="font-body text-4xl italic text-surface-100 leading-relaxed">
        "BMR Homes isn't just building houses; they're building dreams. The precision, the passion, the peace of mind – it's all part of the extraordinary BMR experience."
      </p>
    </blockquote>
    <p class="font-heading font-bold text-2xl text-accent-500 mb-2">- The Williams Family</p>
    <p class="font-body text-xl text-surface-300">Luxury Homeowners, Serenity Ridge</p>
  </div>
</section>
```

---

### 3.5 CTA Banner

#### Description
A standalone, visually distinct section designed to drive a specific action. Uses strong color contrast and clear messaging.

#### Tailwind/CSS Classes
```html
<section class="bg-accent-500 text-surface-50 py-16 lg:py-20 animate-fade-in-up">
  <div class="max-w-4xl mx-auto px-6 sm:px-8 text-center">
    <h2 class="font-heading font-bold text-4xl mb-4">Ready to Build Your Dream Home?</h2>
    <p class="font-body text-lg max-w-2xl mx-auto mb-8">Connect with BMR Homes today to begin your journey towards unparalleled architectural excellence and a home crafted just for you.</p>
    <a href="/contact" class="inline-block bg-primary-700 text-surface-50 font-medium font-heading py-3 px-8 rounded-md hover:bg-primary-800 transition duration-300 ease-in-out active:scale-95 shadow-lg hover:shadow-xl">Request a Consultation</a>
  </div>
</section>
```

#### HTML Structure Sketch
```html
<section class="[bg-accent-color] text-surface-50 [vertical-padding]">
  <div class="max-w-limited mx-auto text-center">
    <h2 class="call-to-action-heading"></h2>
    <p class="call-to-action-description"></p>
    <a class="primary-button" href="#">Action Text</a>
  </div>
</section>
```

#### Responsive Behavior
*   Content is centered and constrained (`max-w-4xl`).
*   Text scales appropriately.

#### Animation/Interaction Notes
*   **Scroll-reveal:** The entire banner fades in and slides up (`animate-fade-in-up`).
*   **Button:** Standard hover/active button animations apply.

#### Variations

##### Variation 1: Accent Background (Default)
As shown above, `bg-accent-500` provides a warm, organic contrast.

##### Variation 2: Primary Dark Background
Uses the dark primary color for a more grounded, sophisticated call to action.
```html
<section class="bg-primary-900 text-surface-50 py-16 lg:py-20 animate-fade-in-up">
  <div class="max-w-4xl mx-auto px-6 sm:px-8 text-center">
    <h2 class="font-heading font-bold text-4xl mb-4">Partner with Industry Leaders</h2>
    <p class="font-body text-lg max-w-2xl mx-auto mb-8">Discover how our expertise can bring your most ambitious architectural visions to life.</p>
    <a href="/about" class="inline-block bg-accent-500 text-surface-50 font-medium font-heading py-3 px-8 rounded-md hover:bg-accent-600 transition duration-300 ease-in-out active:scale-95 shadow-lg hover:shadow-xl">Learn More About BMR</a>
  </div>
</section>
```

---

### 3.6 FAQ Accordion

#### Description
Provides a clean, interactive way to present frequently asked questions or digestible information, with a smooth open/close animation.

#### Tailwind/CSS Classes
```html
<section class="py-24 bg-surface-50 text-primary-700 lg:py-32">
  <div class="max-w-3xl mx-auto px-6 sm:px-8">
    <h2 class="font-heading font-bold text-4xl text-center text-primary-900 mb-12">Frequently Asked Questions</h2>

    <div class="space-y-4">

      <!-- Accordion Item 1 -->
      <div class="border border-primary-200 rounded-lg overflow-hidden shadow-sm animate-fade-in-up">
        <button class="flex justify-between items-center w-full p-6 text-left font-heading font-medium text-lg text-primary-800 focus:outline-none bg-surface-100 hover:bg-surface-200 transition duration-200 ease-in-out" aria-expanded="false" data-accordion-trigger>
          What is the typical timeline for a custom home build?
          <svg class="w-5 h-5 transform transition-transform duration-300 ease-in-out" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7"></path></svg>
        </button>
        <div class="p-6 pt-0 hidden" data-accordion-content>
          <p class="font-body text-base text-primary-700">The timeline for a custom home build can vary significantly based on complexity, size, and material selections. Generally, it ranges from 12 to 24 months, including design, permitting, and construction. We provide a detailed project schedule early in our process.</p>
        </div>
      </div>

      <!-- Accordion Item 2 -->
      <div class="border border-primary-200 rounded-lg overflow-hidden shadow-sm animate-fade-in-up" style="animation-delay: 100ms;">
        <button class="flex justify-between items-center w-full p-6 text-left font-heading font-medium text-lg text-primary-800 focus:outline-none bg-surface-100 hover:bg-surface-200 transition duration-200 ease-in-out" aria-expanded="false" data-accordion-trigger>
          Can BMR Homes assist with architectural design?
          <svg class="w-5 h-5 transform transition-transform duration-300 ease-in-out" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7"></path></svg>
        </button>
        <div class="p-6 pt-0 hidden" data-accordion-content>
          <p class="font-body text-base text-primary-700">Yes, we have strong relationships with acclaimed architectural firms and can guide you through the design process, helping you select the right partner to bring your unique vision to life.</p>
        </div>
      </div>

    </div>
  </div>
</section>

<!-- Required JS for accordion functionality (example) -->
<script>
  document.addEventListener('DOMContentLoaded', () => {
    document.querySelectorAll('[data-accordion-trigger]').forEach(button => {
      button.addEventListener('click', () => {
        const content = button.nextElementSibling;
        const svg = button.querySelector('svg');

        button.setAttribute('aria-expanded', button.getAttribute('aria-expanded') === 'false' ? 'true' : 'false');
        svg.classList.toggle('rotate-180');

        if (content.classList.contains('hidden')) {
          content.style.maxHeight = '0'; // Set initial state for transition
          content.classList.remove('hidden');
          setTimeout(() => {
            content.style.maxHeight = content.scrollHeight + 'px'; // Expand to full height
            content.style.paddingTop = '1.5rem'; // Re-add padding-top (p-6, pt-0)
          }, 10); // Small delay to allow reflow
        } else {
          content.style.maxHeight = '0';
          content.style.paddingTop = '0'; // Remove padding-top during collapse
          content.addEventListener('transitionend', () => {
            if (content.style.maxHeight === '0px') { // Only hide if it's actually collapsed
              content.classList.add('hidden');
            }
          }, { once: true });
        }
        content.style.transition = 'max-height 0.3s ease-in-out, padding-top 0.3s ease-in-out';
      });
    });
  });
</script>
```

#### HTML Structure Sketch
```html
<section class="section-wrapper">
  <h2 class="section-title"></h2>
  <div class="space-y-4">
    <div class="accordion-item">
      <button class="accordion-trigger" aria-expanded="false">
        Question <svg class="arrow-icon"></svg>
      </button>
      <div class="accordion-content hidden">
        <p class="answer-text"></p>
      </div>
    </div>
    <!-- ... more accordion items ... -->
  </div>
</section>
```

#### Responsive Behavior
*   Always full-width within the `max-w-3xl` container.
*   Text sizes remain legible.

#### Animation/Interaction Notes
*   **Open/Close:** Uses `max-height` transition for a smooth expand/collapse effect, paired with a `rotate` transform on the arrow icon (`transition-transform duration-300 ease-in-out`).
*   **Scroll-reveal:** Individual accordion items can fade-in with a slight stagger (`animate-fade-in-up`).

#### Variations

##### Variation 1: Bordered (Default)
As shown above, clean borders separate items.

##### Variation 2: Box Shadow
Subtle shadow to give items more elevation.
```html
<div class="border border-primary-200 rounded-lg overflow-hidden shadow-md animate-fade-in-up">
  <button class="flex justify-between items-center w-full p-6 text-left font-heading font-medium text-lg text-primary-800 focus:outline-none bg-surface-100 hover:bg-surface-200 transition duration-200 ease-in-out" aria-expanded="false" data-accordion-trigger>
    How do I get started with BMR Homes?
    <svg class="w-5 h-5 transform transition-transform duration-300 ease-in-out" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7"></path></svg>
  </button>
  <div class="p-6 pt-0 hidden" data-accordion-content>
    <p class="font-body text-base text-primary-700">Start by contacting us through our website or phone to schedule an initial consultation. We'll discuss your vision, budget, and project requirements to see how we can best assist you.</p>
  </div>
</div>
```

---

## 4. Navigation

The navigation is critical for establishing quiet confidence through seamless usability and polished presentation.

### 4.1 Header (Desktop)

#### Description
The main site header, featuring the logo, primary navigation links, and a call-to-action button. Designed for transparency on hero sections and a subtle solid background on scroll.

#### Tailwind/CSS Classes
```html
<header class="fixed top-0 left-0 w-full z-50 transition-all duration-300 ease-in-out" id="main-header">
  <div class="max-w-7xl mx-auto px-6 sm:px-8 py-6 flex justify-between items-center">
    <!-- Logo -->
    <a href="/" class="flex-shrink-0">
      <img src="/path/to/logo-light.svg" alt="BMR Homes Logo" class="h-8 md:h-10 transition-opacity duration-300" id="header-logo-light">
      <img src="/path/to/logo-dark.svg" alt="BMR Homes Logo" class="h-8 md:h-10 opacity-0 absolute top-6 md:top-6 transition-opacity duration-300" id="header-logo-dark">
    </a>

    <!-- Desktop Navigation -->
    <nav class="hidden md:flex items-center space-x-8 font-heading font-medium text-lg">
      <a href="/projects" class="text-surface-50 hover:text-accent-300 transition-colors duration-200 ease-in-out header-link">Projects</a>
      <a href="/services" class="text-surface-50 hover:text-accent-300 transition-colors duration-200 ease-in-out header-link">Services</a>
      <a href="/about" class="text-surface-50 hover:text-accent-300 transition-colors duration-200 ease-in-out header-link">About Us</a>
      <a href="/contact" class="inline-block bg-accent-500 text-surface-50 py-2.5 px-6 rounded-md hover:bg-accent-600 transition duration-300 ease-in-out active:scale-95 shadow-md hover:shadow-lg">Contact Us</a>
    </nav>

    <!-- Mobile Menu Button (Hamburger) -->
    <button class="md:hidden text-surface-50 header-link" aria-label="Open menu" data-mobile-menu-trigger>
      <svg class="w-8 h-8" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"></path></svg>
    </button>
  </div>
</header>

<!-- Required JS for scroll behavior -->
<script>
  document.addEventListener('DOMContentLoaded', () => {
    const header = document.getElementById('main-header');
    const links = document.querySelectorAll('.header-link');
    const logoLight = document.getElementById('header-logo-light');
    const logoDark = document.getElementById('header-logo-dark');
    const ctaButton = header.querySelector('a[href="/contact"]'); // Targeting the button specifically

    const scrollThreshold = 100; // Pixels to scroll before changing header

    const updateHeader = () => {
      if (window.scrollY > scrollThreshold) {
        header.classList.add('bg-primary-900', 'shadow-md', 'py-4');
        header.classList.remove('py-6');
        links.forEach(link => link.classList.replace('text-surface-50', 'text-surface-100'));
        if (ctaButton) ctaButton.classList.replace('bg-accent-500', 'bg-accent-600'); // Darken accent on scroll
        if (ctaButton) ctaButton.classList.replace('hover:bg-accent-600', 'hover:bg-accent-700');
        logoLight.classList.add('opacity-0');
        logoDark.classList.remove('opacity-0');
      } else {
        header.classList.remove('bg-primary-900', 'shadow-md', 'py-4');
        header.classList.add('py-6');
        links.forEach(link => link.classList.replace('text-surface-100', 'text-surface-50'));
        if (ctaButton) ctaButton.classList.replace('bg-accent-600', 'bg-accent-500'); // Revert accent
        if (ctaButton) ctaButton.classList.replace('hover:bg-accent-700', 'hover:bg-accent-600');
        logoLight.classList.remove('opacity-0');
        logoDark.classList.add('opacity-0');
      }
    };

    window.addEventListener('scroll', updateHeader);
    updateHeader(); // Call on load to set initial state
  });
</script>
```

#### HTML Structure Sketch
```html
<header class="fixed-full-width-top">
  <div class="wrapper flex-between-center">
    <a href="/" class="logo"> <!-- Light/Dark logo variations --> </a>
    <nav class="desktop-links">
      <a href="#" class="nav-link"></a>
      <a href="#" class="nav-link"></a>
      <a href="#" class="cta-button"></a>
    </nav>
    <button class="mobile-menu-trigger"> <!-- Hamburger Icon --> </button>
  </div>
</header>
```

#### Responsive Behavior
*   `hidden md:flex` hides desktop navigation on mobile.
*   `md:hidden` hides mobile trigger on desktop.
*   Logo height adjusts `h-8 md:h-10`.

#### Animation/Interaction Notes
*   **Scroll Behavior:** Header transitions from `transparent` (with light text) to `bg-primary-900` (with slightly lighter text and subtle `shadow-md`) on scroll, also switching logo color. `transition-all duration-300 ease-in-out` for smoothness.
*   **Link Hover:** Simple color shift (`hover:text-accent-300`).
*   **Button:** Standard button hover/active effects.

### 4.2 Mobile Navigation (Drawer/Overlay)

#### Description
A full-screen overlay or side-drawer for mobile navigation, triggered by a hamburger icon. Prioritizes clear readability and intuitive interaction.

#### Tailwind/CSS Classes
```html
<!-- Mobile Navigation Overlay -->
<div class="fixed inset-0 bg-primary-900 text-surface-50 z-50 flex flex-col justify-center items-center transform -translate-x-full transition-transform duration-300 ease-in-out" id="mobile-menu" aria-hidden="true">
  <button class="absolute top-6 right-6 text-surface-50" aria-label="Close menu" data-mobile-menu-close>
    <svg class="w-8 h-8" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path></svg>
  </button>

  <nav class="flex flex-col space-y-8 text-center font-heading font-medium text-3xl">
    <a href="/projects" class="text-surface-50 hover:text-accent-300 transition-colors duration-200 ease-in-out">Projects</a>
    <a href="/services" class="text-surface-50 hover:text-accent-300 transition-colors duration-200 ease-in-out">Services</a>
    <a href="/about" class="text-surface-50 hover:text-accent-300 transition-colors duration-200 ease-in-out">About Us</a>
    <a href="/contact" class="inline-block bg-accent-500 text-surface-50 py-3 px-8 rounded-md hover:bg-accent-600 transition duration-300 ease-in-out active:scale-95 shadow-lg">Contact Us</a>
  </nav>
</div>

<!-- Required JS for mobile menu toggle -->
<script>
  document.addEventListener('DOMContentLoaded', () => {
    const mobileMenuTrigger = document.querySelector('[data-mobile-menu-trigger]');
    const mobileMenuClose = document.querySelector('[data-mobile-menu-close]');
    const mobileMenu = document.getElementById('mobile-menu');

    mobileMenuTrigger.addEventListener('click', () => {
      mobileMenu.classList.remove('-translate-x-full');
      mobileMenu.setAttribute('aria-hidden', 'false');
      document.body.classList.add('overflow-hidden'); // Prevent scrolling
    });

    mobileMenuClose.addEventListener('click', () => {
      mobileMenu.classList.add('-translate-x-full');
      mobileMenu.setAttribute('aria-hidden', 'true');
      document.body.classList.remove('overflow-hidden'); // Re-enable scrolling
    });

    mobileMenu.querySelectorAll('a').forEach(link => {
      link.addEventListener('click', () => {
        // Close menu when a link is clicked
        mobileMenu.classList.add('-translate-x-full');
        mobileMenu.setAttribute('aria-hidden', 'true');
        document.body.classList.remove('overflow-hidden');
      });
    });
  });
</script>
```

#### HTML Structure Sketch
```html
<div class="mobile-overlay-wrapper">
  <button class="close-button"> <!-- X Icon --> </button>
  <nav class="mobile-links-container">
    <a href="#" class="mobile-nav-link"></a>
    <a href="#" class="mobile-nav-link"></a>
    <a href="#" class="mobile-cta-button"></a>
  </nav>
</div>
```

#### Animation/Interaction Notes
*   **Menu Open/Close:** The overlay slides in/out from the left using `transform -translate-x-full` and `transition-transform duration-300 ease-in-out`.
*   Hamburger icon transforms into an 'X' (often via CSS-animated SVG or icon component).

### 4.3 Footer

#### Description
The site footer, providing key navigation, social links, and legal information. Structured with a multi-column layout on desktop and stacked on mobile.

#### Tailwind/CSS Classes
```html
<footer class="bg-primary-900 text-surface-300 py-16 md:py-20 font-body">
  <div class="max-w-7xl mx-auto px-6 sm:px-8">
    <div class="grid grid-cols-1 md:grid-cols-4 gap-12 mb-16">

      <!-- Column 1: Logo & Tagline -->
      <div class="md:col-span-2">
        <img src="/path/to/logo-light.svg" alt="BMR Homes Logo" class="h-10 mb-6">
        <p class="text-surface-400 text-lg max-w-sm">Crafting spaces that inspire, built with quiet confidence and timeless precision.</p>
        <div class="flex space-x-4 mt-6">
          <a href="#" aria-label="Facebook" class="text-surface-400 hover:text-accent-500 transition-colors duration-200"><svg class="w-6 h-6" fill="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path d="M14 13.5h2.213l.307-2.213h-2.52v-1.44c0-.622.316-1.222 1.258-1.222h1.246v-2.02c-.22-.03-.967-.093-1.848-.093-1.83 0-3.076 1.12-3.076 3.167v1.737h-2v2.213h2v6.596c-.604.148-1.22.257-1.86.329v-6.925h-2.149V13.5H9v-2.213h2V9.587c0-1.83 1.12-3.076 3.167-3.076h1.737V4h-1.737c-2.454 0-4.041 1.708-4.041 4.546v.883H9z"/></svg></a>
          <a href="#" aria-label="Instagram" class="text-surface-400 hover:text-accent-500 transition-colors duration-200"><svg class="w-6 h-6" fill="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path d="M7.5 2C4.463 2 2 4.463 2 7.5v9C2 19.537 4.463 22 7.5 22h9c3.037 0 5.5-2.463 5.5-5.5v-9C22 4.463 19.537 2 16.5 2h-9zm0 2h9c2.023 0 3.5 1.477 3.5 3.5v9c0 2.023-1.477 3.5-3.5 3.5h-9c-2.023 0-3.5-1.477-3.5-3.5v-9C4 5.477 5.477 4 7.5 4zm4.5 3.5c-2.206 0-4 1.794-4 4s1.794 4 4 4 4-1.794 4-4-1.794-4-4-4zm0 2c1.103 0 2 .897 2 2s-.897 2-2 2-2-.897-2-2 .897-2 2-2zm4.5-5c-.829 0-1.5.671-1.5 1.5s.671 1.5 1.5 1.5 1.5-.671 1.5-1.5-.671-1.5-1.5-1.5z"/></svg></a>
          <a href="#" aria-label="LinkedIn" class="text-surface-400 hover:text-accent-500 transition-colors duration-200"><svg class="w-6 h-6" fill="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path d="M16 8h-4v4h4V8zm-2 10v-6h-4v6h4zM2 6h4v12H2V6zM22 6c0-2.21-1.79-4-4-4H6C3.79 2 2 3.79 2 6v12c0 2.21 1.79 4 4 4h12c2.21 0 4-1.79 4-4V6zm-2 0v12c0 1.1-.9 2-2 2H6c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2h12c1.1 0 2 .9 2 2z"/></svg></a>
        </div>
      </div>

      <!-- Column 2: Quick Links -->
      <div>
        <h4 class="font-heading font-semibold text-xl text-surface-50 mb-6">Quick Links</h4>
        <ul class="space-y-3">
          <li><a href="/projects" class="hover:text-accent-500 transition-colors duration-200">Projects</a></li>
          <li><a href="/services" class="hover:text-accent-500 transition-colors duration-200">Services</a></li>
          <li><a href="/about" class="hover:text-accent-500 transition-colors duration-200">About Us</a></li>
          <li><a href="/blog" class="hover:text-accent-500 transition-colors duration-200">Blog</a></li>
        </ul>
      </div>

      <!-- Column 3: Resources -->
      <div>
        <h4 class="font-heading font-semibold text-xl text-surface-50 mb-6">Resources</h4>
        <ul class="space-y-3">
          <li><a href="/faq" class="hover:text-accent-500 transition-colors duration-200">FAQ</a></li>
          <li><a href="/process" class="hover:text-accent-500 transition-colors duration-200">Our Process</a></li>
          <li><a href="/testimonials" class="hover:text-accent-500 transition-colors duration-200">Testimonials</a></li>
          <li><a href="/careers" class="hover:text-accent-500 transition-colors duration-200">Careers</a></li>
        </ul>
      </div>

      <!-- Column 4: Contact & Newsletter -->
      <div>
        <h4 class="font-heading font-semibold text-xl text-surface-50 mb-6">Connect</h4>
        <p class="mb-4">
          <a href="mailto:info@bmrhomes.com" class="hover:text-accent-500 transition-colors duration-200">info@bmrhomes.com</a>
        </p>
        <p class="mb-6">
          <a href="tel:+1-555-123-4567" class="hover:text-accent-500 transition-colors duration-200">+1 (555) 123-4567</a>
        </p>
        <h4 class="font-heading font-semibold text-xl text-surface-50 mb-4">Newsletter</h4>
        <form class="flex">
          <input type="email" placeholder="Your email" class="flex-grow p-3 rounded-l-md border border-primary-700 bg-primary-800 text-surface-50 placeholder-surface-400 focus:ring-accent-500 focus:border-accent-500 focus:outline-none">
          <button type="submit" class="bg-accent-500 text-surface-50 px-4 rounded-r-md hover:bg-accent-600 transition duration-200 active:scale-95">Subscribe</button>
        </form>
      </div>

    </div>

    <div class="border-t border-primary-700 pt-8 text-center text-sm text-surface-400">
      <p>&copy; 2023 BMR Homes. All rights reserved. | <a href="/privacy" class="hover:text-accent-500 transition-colors duration-200">Privacy Policy</a> | <a href="/terms" class="hover:text-accent-500 transition-colors duration-200">Terms of Service</a></p>
    </div>
  </div>
</footer>
```

#### HTML Structure Sketch
```html
<footer class="bg-primary-dark text-light-gray padding">
  <div class="wrapper">
    <div class="grid-columns-responsive">
      <!-- Col 1: Logo, Tagline, Social Links -->
      <div> ... </div>
      <!-- Col 2: Nav Links -->
      <div> ... </div>
      <!-- Col 3: Resource Links -->
      <div> ... </div>
      <!-- Col 4: Contact Info, Newsletter Signup -->
      <div> ... </div>
    </div>
    <div class="bottom-bar">
      <p class="copyright-legal"></p>
    </div>
  </div>
</footer>
```

#### Responsive Behavior
*   `grid grid-cols-1 md:grid-cols-4` stacks columns on mobile, then arranges into 4 columns on medium screens.
*   The first column spans 2 (`md:col-span-2`) on larger screens to give space for the logo and tagline.

#### Animation/Interaction Notes
*   **Link Hover:** Simple color shift (`hover:text-accent-500`).
*   **Newsletter Button:** Standard button hover/active effects.

---

## 5. Cards

Cards are a highly reusable pattern for presenting concise, digestible pieces of information, often in a grid. Used for projects, services, team members, blog posts, etc.

#### Description
Clean, precise cards with subtle shadows to indicate elevation. Designed to highlight imagery and provide clear content hierarchy.

#### Tailwind/CSS Classes
```html
<!-- Base Card Styles -->
<div class="bg-surface-50 rounded-lg shadow-md overflow-hidden transition duration-300 ease-in-out hover:shadow-xl hover:-translate-y-1">
  <!-- Content -->
</div>
```

#### HTML Structure Sketch
```html
<div class="base-card-styles">
  <div class="card-image-wrapper">
    <img src="..." alt="..." class="card-image">
  </div>
  <div class="card-content-padding">
    <h3 class="card-heading"></h3>
    <p class="card-text"></p>
    <a href="#" class="card-link"></a>
  </div>
</div>
```

#### Responsive Behavior
*   Cards are typically placed within a responsive grid (`grid sm:grid-cols-2 lg:grid-cols-3`).
*   Image within card is always fluid (`w-full h-auto`).

#### Animation/Interaction Notes
*   **Hover Interaction:** A subtle "lift" effect using `hover:shadow-xl` and `hover:-translate-y-1`, combined with `transition duration-300 ease-in-out`.

#### Variations

##### Variation 1: Project Card (Image Top)
Highlights a large project image, followed by a title and brief description.

###### Tailwind/CSS Classes
```html
<a href="/projects/example" class="block bg-surface-50 rounded-lg shadow-md overflow-hidden transition duration-300 ease-in-out hover:shadow-xl hover:-translate-y-1 group">
  <div class="relative w-full h-60 overflow-hidden">
    <img src="/path/to/project-thumb.jpg" alt="Modern home exterior" class="w-full h-full object-cover group-hover:scale-[1.03] transition-transform duration-300 ease-in-out">
  </div>
  <div class="p-6">
    <h3 class="font-heading font-semibold text-xl text-primary-900 mb-2 group-hover:text-accent-500 transition-colors duration-200">The Riverside Estate</h3>
    <p class="font-body text-base text-primary-700">A stunning blend of modern design and natural elements.</p>
  </div>
</a>
```

##### Variation 2: Service Card (Icon & Text)
Focuses on an icon and text, suitable for listing services or features without large images.

###### Tailwind/CSS Classes
```html
<div class="bg-surface-50 rounded-lg shadow-md p-6 text-center transition duration-300 ease-in-out hover:shadow-xl hover:-translate-y-1 group">
  <div class="inline-block p-4 rounded-lg bg-primary-100 text-primary-700 mb-6 group-hover:bg-accent-100 group-hover:text-accent-700 transition-all duration-200">
    <svg class="w-10 h-10" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M21 12a9 9 0 01-9 9m9-9a9 9 0 00-9-9m9 9H3m9 0a9 9 0 01-9-9m9 9a9 9 0 00-9 9m-1-9a9 9 0 01-9-9"></path></svg>
  </div>
  <h3 class="font-heading font-semibold text-xl text-primary-900 mb-3 group-hover:text-accent-500 transition-colors duration-200">Custom Home Building</h3>
  <p class="font-body text-base text-primary-700">Bringing your unique architectural visions to life with unparalleled precision.</p>
  <a href="/services/custom-build" class="text-accent-500 font-medium mt-4 inline-block group-hover:underline transition-colors duration-200">Learn More &rarr;</a>
</div>
```

##### Variation 3: Team Member Card (Image Left)
Features a smaller image to the side, ideal for profiles.

###### Tailwind/CSS Classes
```html
<div class="flex items-center bg-surface-50 rounded-lg shadow-md p-6 transition duration-300 ease-in-out hover:shadow-xl hover:-translate-y-1">
  <div class="flex-shrink-0 w-24 h-24 rounded-full overflow-hidden mr-6">
    <img src="/path/to/team-member.jpg" alt="John Smith" class="w-full h-full object-cover">
  </div>
  <div>
    <h3 class="font-heading font-semibold text-xl text-primary-900">John Smith</h3>
    <p class="font-body text-base text-primary-700 mb-2">Lead Architect</p>
    <a href="#" class="text-accent-500 text-sm hover:underline">View Profile</a>
  </div>
</div>
```

---

## 6. Forms

Forms are designed for clarity and ease of use, reflecting the brand's precision and trustworthiness.

#### Description
Clean input fields with subtle borders and clear focus states. Buttons follow a hierarchical styling.

#### HTML Structure Sketch
```html
<form class="form-layout">
  <div class="form-group">
    <label for="input-id" class="label-style"></label>
    <input type="text" id="input-id" class="input-style">
    <p class="validation-message"></p>
  </div>
  <button type="submit" class="primary-button-style"></button>
</form>
```

#### Responsive Behavior
*   Forms are primarily single-column on mobile.
*   Two-column layouts collapse to single column on `md` breakpoint.
*   Input fields expand to full width within their container.

#### Animation/Interaction Notes
*   **Focus Ring:** `focus:ring-primary-300` for a subtle glow.
*   **Button:** Standard hover/active states.

### 6.1 Input Styling

#### Tailwind/CSS Classes
```html
<div class="mb-6">
  <label for="name" class="block text-sm font-body font-medium text-primary-700 mb-2">Your Name</label>
  <input type="text" id="name" name="name" placeholder="John Doe"
         class="w-full px-4 py-3 border border-primary-200 rounded-md bg-surface-50 text-primary-900 placeholder-primary-400
                focus:outline-none focus:ring-2 focus:ring-primary-300 focus:border-primary-500
                transition-all duration-200 ease-in-out">
</div>

<div class="mb-6">
  <label for="email" class="block text-sm font-body font-medium text-primary-700 mb-2">Your Email</label>
  <input type="email" id="email" name="email" placeholder="john.doe@example.com"
         class="w-full px-4 py-3 border border-primary-200 rounded-md bg-surface-50 text-primary-900 placeholder-primary-400
                focus:outline-none focus:ring-2 focus:ring-primary-300 focus:border-primary-500
                transition-all duration-200 ease-in-out">
</div>

<div class="mb-6">
  <label for="message" class="block text-sm font-body font-medium text-primary-700 mb-2">Your Message</label>
  <textarea id="message" name="message" rows="5" placeholder="Tell us about your project..."
            class="w-full px-4 py-3 border border-primary-200 rounded-md bg-surface-50 text-primary-900 placeholder-primary-400
                   focus:outline-none focus:ring-2 focus:ring-primary-300 focus:border-primary-500
                   transition-all duration-200 ease-in-out"></textarea>
</div>
```

### 6.2 Button Hierarchy

#### Tailwind/CSS Classes
```html
<!-- Primary CTA Button -->
<button type="submit" class="bg-accent-500 text-surface-50 font-heading font-medium py-3 px-8 rounded-md
                       hover:bg-accent-600 transition duration-300 ease-in-out active:scale-95 shadow-md hover:shadow-lg">
  Submit Inquiry
</button>

<!-- Secondary Button -->
<button type="button" class="bg-primary-500 text-surface-50 font-heading font-medium py-3 px-8 rounded-md
                       hover:bg-primary-600 transition duration-300 ease-in-out active:scale-95 shadow-md">
  Learn More
</button>

<!-- Ghost/Outline Button -->
<button type="button" class="border border-primary-500 text-primary-500 font-heading font-medium py-3 px-8 rounded-md
                       hover:bg-primary-50 transition duration-300 ease-in-out active:scale-95">
  View All
</button>

<!-- Button with Dark Background Context -->
<button type="button" class="border border-surface-50 text-surface-50 font-heading font-medium py-3 px-8 rounded-md
                       hover:bg-surface-50 hover:text-primary-900 transition duration-300 ease-in-out active:scale-95">
  Browse Projects
</button>
```

### 6.3 Form Layout

#### Tailwind/CSS Classes
```html
<section class="py-24 bg-surface-50 lg:py-32">
  <div class="max-w-3xl mx-auto px-6 sm:px-8">
    <h2 class="font-heading font-bold text-4xl text-center text-primary-900 mb-12">Get in Touch</h2>

    <form class="space-y-6">
      <!-- Single Column Layout -->
      <div>
        <label for="form-name" class="block text-sm font-body font-medium text-primary-700 mb-2">Name</label>
        <input type="text" id="form-name" name="name" class="w-full px-4 py-3 border border-primary-200 rounded-md bg-surface-50 text-primary-900 focus:ring-2 focus:ring-primary-300 focus:border-primary-500 transition">
      </div>
      <div>
        <label for="form-email" class="block text-sm font-body font-medium text-primary-700 mb-2">Email</label>
        <input type="email" id="form-email" name="email" class="w-full px-4 py-3 border border-primary-200 rounded-md bg-surface-50 text-primary-900 focus:ring-2 focus:ring-primary-300 focus:border-primary-500 transition">
      </div>

      <!-- Responsive Two-Column Layout -->
      <div class="grid md:grid-cols-2 gap-6">
        <div>
          <label for="form-phone" class="block text-sm font-body font-medium text-primary-700 mb-2">Phone</label>
          <input type="tel" id="form-phone" name="phone" class="w-full px-4 py-3 border border-primary-200 rounded-md bg-surface-50 text-primary-900 focus:ring-2 focus:ring-primary-300 focus:border-primary-500 transition">
        </div>
        <div>
          <label for="form-budget" class="block text-sm font-body font-medium text-primary-700 mb-2">Estimated Budget</label>
          <select id="form-budget" name="budget" class="w-full px-4 py-3 border border-primary-200 rounded-md bg-surface-50 text-primary-900 focus:ring-2 focus:ring-primary-300 focus:border-primary-500 transition">
            <option value="">Select an option</option>
            <option value="under-500k">Under $500k</option>
            <option value="500k-1m">$500k - $1M</option>
            <option value="1m-2m">$1M - $2M</option>
            <option value="2m-plus">$2M+</option>
          </select>
        </div>
      </div>

      <div>
        <label for="form-message" class="block text-sm font-body font-medium text-primary-700 mb-2">Message</label>
        <textarea id="form-message" name="message" rows="6" class="w-full px-4 py-3 border border-primary-200 rounded-md bg-surface-50 text-primary-900 focus:ring-2 focus:ring-primary-300 focus:border-primary-500 transition"></textarea>
      </div>

      <div class="flex justify-center md:justify-start">
        <button type="submit" class="bg-accent-500 text-surface-50 font-heading font-medium py-3 px-8 rounded-md
                               hover:bg-accent-600 transition duration-300 ease-in-out active:scale-95 shadow-md hover:shadow-lg">
          Send Message
        </button>
      </div>
    </form>
  </div>
</section>
```

### 6.4 Validation States

#### Tailwind/CSS Classes
```html
<div class="mb-6">
  <label for="validation-name" class="block text-sm font-body font-medium text-primary-700 mb-2">Your Name</label>
  <input type="text" id="validation-name" name="name"
         class="w-full px-4 py-3 border border-error rounded-md bg-surface-50 text-primary-900
                focus:outline-none focus:ring-2 focus:ring-error focus:border-error transition-all duration-200 ease-in-out">
  <p class="mt-2 text-sm text-error">Name is required.</p>
</div>

<div class="mb-6">
  <label for="validation-email-success" class="block text-sm font-body font-medium text-primary-700 mb-2">Your Email</label>
  <input type="email" id="validation-email-success" name="email" value="valid@example.com"
         class="w-full px-4 py-3 border border-success rounded-md bg-surface-50 text-primary-900
                focus:outline-none focus:ring-2 focus:ring-success focus:border-success transition-all duration-200 ease-in-out">
  <p class="mt-2 text-sm text-success">Email looks good!</p>
</div>
```

---

## 7. Utility Patterns

These are not full components but rather reusable classes and wrappers that enhance the overall look and feel, adhering to the brand's motion language and spacious aesthetic.

### 7.1 Page Transition Wrapper

#### Description
A wrapper that enables smooth cross-fade page transitions, avoiding jarring hard navigations. Requires JavaScript for implementation.

#### Tailwind/CSS Classes
```html
<!-- In your Astro layout (e.g., src/layouts/BaseLayout.astro) -->
<body class="font-body text-primary-700 bg-surface-50">
  <div id="page-transition-wrapper" class="transition-opacity duration-300 ease-in-out opacity-100">
    <slot /> <!-- This is where your page content goes -->
  </div>
</body>

<!-- Script for basic page transitions (needs to be carefully integrated with Astro's view transitions if enabled, or client-side routing) -->
<script>
  // This is a conceptual script. For Astro, consider using View Transitions for native support.
  // If not using View Transitions, this would require a client-side router or more complex setup.
  const wrapper = document.getElementById('page-transition-wrapper');

  // Example for SPA-like behavior (e.g., if you're fetching new content via JS)
  function transitionToNewContent(newContentHtml) {
    wrapper.classList.remove('opacity-100');
    wrapper.classList.add('opacity-0');

    setTimeout(() => {
      // Replace content (in a real scenario, this would be handled by your routing logic)
      // wrapper.innerHTML = newContentHtml;
      // For a multi-page app, this would be a full page load after opacity change.
      wrapper.classList.remove('opacity-0');
      wrapper.classList.add('opacity-100');
    }, 300); // Match transition duration
  }

  // If using native links, you'd need to intercept them and handle transitions.
  // For Astro, consider `view-transitions` for a more integrated solution.
</script>
```

#### HTML Structure Sketch
```html
<body class="global-font-styles">
  <div id="page-transition-wrapper" class="opacity-100 transition-opacity-duration">
    <!-- Your Astro page content -->
    <slot />
  </div>
</body>
```

#### Responsive Behavior
N/A (visual effect).

#### Animation/Interaction Notes
*   A subtle `opacity` transition (`duration-300 ease-in-out`) gives a smooth cross-fade when navigating between pages.

### 7.2 Scroll-Reveal Animation Classes

#### Description
Reusable utility classes for gentle fade-up and slide-in animations as elements enter the viewport. Requires an Intersection Observer to trigger.

#### Tailwind/CSS Classes
```css
/* Add to your global CSS (e.g., src/styles/global.css) */
.animate-fade-in-up {
  opacity: 0;
  transform: translateY(1rem); /* 16px */
  transition: opacity 0.6s ease-out, transform 0.6s ease-out; /* Slightly longer for elegance */
  transition-delay: var(--animation-delay, 0s); /* Custom property for stagger */
}

.animate-fade-in-left {
  opacity: 0;
  transform: translateX(-1rem);
  transition: opacity 0.6s ease-out, transform 0.6s ease-out;
  transition-delay: var(--animation-delay, 0s);
}

.animate-fade-in-right {
  opacity: 0;
  transform: translateX(1rem);
  transition: opacity 0.6s ease-out, transform 0.6s ease-out;
  transition-delay: var(--animation-delay, 0s);
}

/* Class added by JS when element is visible */
.is-visible {
  opacity: 1;
  transform: translateY(0);
  transform: translateX(0);
}
```

```html
<!-- Example Usage in HTML -->
<section class="py-24">
  <div class="max-w-7xl mx-auto px-6 sm:px-8">
    <h2 class="font-heading font-bold text-4xl text-center text-primary-900 mb-12 animate-fade-in-up">Our Approach</h2>
    <p class="font-body text-lg text-center max-w-2xl mx-auto mb-16 animate-fade-in-up" style="--animation-delay: 100ms;">
      Every BMR project begins with a deep understanding of your aspirations.
    </p>

    <div class="grid md:grid-cols-2 gap-12 items-center">
      <div class="animate-fade-in-left">
        <img src="/path/to/process-image.jpg" alt="Design process" class="w-full h-auto rounded-none shadow-md">
      </div>
      <div class="animate-fade-in-right">
        <h3 class="font-heading font-semibold text-3xl text-primary-900 mb-4">Initial Consultation</h3>
        <p class="font-body text-lg">We listen, we learn, and we begin to visualize the future of your space.</p>
      </div>
    </div>
  </div>
</section>

<!-- Required JS for Intersection Observer (in a client-side script or Astro component script) -->
<script>
  document.addEventListener('DOMContentLoaded', () => {
    const observerOptions = {
      root: null,
      rootMargin: '0px',
      threshold: 0.1 // Trigger when 10% of the item is visible
    };

    const observer = new IntersectionObserver((entries, observer) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          entry.target.classList.add('is-visible');
          observer.unobserve(entry.target); // Only animate once
        }
      });
    }, observerOptions);

    document.querySelectorAll('.animate-fade-in-up, .animate-fade-in-left, .animate-fade-in-right').forEach(el => {
      observer.observe(el);
    });
  });
</script>
```

#### Responsive Behavior
N/A (visual effect).

#### Animation/Interaction Notes
*   Elements start `opacity-0` and `translateY(1rem)`/`translateX(1rem)` (or `-1rem`).
*   When visible, JavaScript adds `is-visible` class, transitioning to `opacity-100` and `translateY(0)`/`translateX(0)`.
*   `transition-delay` CSS custom property allows for staggered animations in grids or lists.

### 7.3 Responsive Image/Video Container

#### Description
Ensures images and videos maintain their aspect ratio and scale fluidly across all devices, crucial for BMR's hero photography.

#### Tailwind/CSS Classes
```html
<!-- 16:9 Aspect Ratio (default for many videos) -->
<div class="relative w-full overflow-hidden" style="padding-top: 56.25%;"> <!-- 16:9 ratio -->
  <img src="/path/to/hero-video-poster.jpg" alt="Video poster" class="absolute inset-0 w-full h-full object-cover z-0">
  <video src="/path/to/hero-video.mp4" autoplay loop muted playsinline
         class="absolute inset-0 w-full h-full object-cover z-10"></video>
</div>

<!-- 4:3 Aspect Ratio (for some photography) -->
<div class="relative w-full overflow-hidden" style="padding-top: 75%;"> <!-- 4:3 ratio -->
  <img src="/path/to/project-image-4x3.jpg" alt="Detail shot" class="absolute inset-0 w-full h-full object-cover">
</div>

<!-- Generic responsive image, scales to container -->
<img src="/path/to/standard-image.jpg" alt="Standard image" class="w-full h-auto object-cover rounded-none">
```
*(Note: Tailwind 3.0+ offers `aspect-w-16 aspect-h-9` utilities, which are preferred. If using older Tailwind or for custom ratios, the `padding-top` trick is reliable.)*

#### HTML Structure Sketch
```html
<div class="relative w-full overflow-hidden" style="padding-top: [percentage];">
  <img src="..." alt="..." class="absolute inset-0 w-full h-full object-cover">
  <!-- or -->
  <video src="..." autoplay loop muted playsinline class="absolute inset-0 w-full h-full object-cover"></video>
</div>
```

#### Responsive Behavior
*   The `padding-top` trick or Tailwind's aspect ratio utilities ensure the container always has the correct aspect ratio.
*   The `object-cover` class ensures the media fills the container without distortion, cropping as necessary.

#### Animation/Interaction Notes
N/A (structural utility).

### 7.4 Gradient Overlay Mixin

#### Description
A subtle, linear gradient overlay (often dark or primary-toned) used over images to improve text readability or add a premium, depth effect. Avoids heavy gradients as per design direction.

#### Tailwind/CSS Classes
```css
/* Add to your global CSS or create a custom Tailwind utility */
.gradient-overlay-dark::before {
  content: '';
  position: absolute;
  inset: 0;
  background: linear-gradient(to top, rgba(30, 43, 51, 0.7), rgba(30, 43, 51, 0) 50%); /* primary-900 @ 70% to 0% */
  z-index: 1; /* Ensure it's above image, below text */
}

.gradient-overlay-subtle::before {
  content: '';
  position: absolute;
  inset: 0;
  background: linear-gradient(to top, rgba(74, 101, 114, 0.4), rgba(74, 101, 114, 0) 60%); /* primary-500 @ 40% to 0% */
  z-index: 1;
}
```
```html
<!-- Example Usage on a Hero Section -->
<section class="relative h-screen flex items-center justify-center text-surface-50 overflow-hidden">
  <div class="absolute inset-0 z-0">
    <img src="/path/to/hero-image.jpg" alt="Aspirational BMR Home" class="w-full h-full object-cover">
    <div class="absolute inset-0 bg-primary-900 opacity-60"></div> <!-- Solid overlay -->
    <!-- OR, using the gradient mixin for a more subtle effect -->
    <div class="absolute inset-0 gradient-overlay-dark"></div>
  </div>
  <div class="relative z-10 text-center">
    <h1 class="text-5xl font-heading font-bold">Your Vision, Built.</h1>
  </div>
</section>
```

#### HTML Structure Sketch
```html
<div class="relative image-container">
  <img src="...">
  <div class="gradient-overlay-class"></div> <!-- Or directly apply via pseudo-element -->
  <div class="relative z-content-above-overlay"> <!-- Content over image --> </div>
</div>
```

#### Responsive Behavior
N/A (visual effect).

#### Animation/Interaction Notes
N/A (static visual utility).

### 7.5 Badge/Tag/Chip Style

#### Description
Small, informative tags for categories, statuses, or keywords. Used sparingly to maintain a clean aesthetic.

#### Tailwind/CSS Classes
```html
<!-- Primary/Default Badge -->
<span class="inline-flex items-center px-3 py-1 rounded-full text-sm font-medium bg-primary-100 text-primary-700">
  New Project
</span>

<!-- Accent Badge -->
<span class="inline-flex items-center px-3 py-1 rounded-full text-sm font-medium bg-accent-100 text-accent-700">
  Featured
</span>

<!-- Success Badge -->
<span class="inline-flex items-center px-3 py-1 rounded-full text-sm font-medium bg-green-100 text-success">
  Completed
</span>

<!-- Dark Context Badge (e.g., on a dark background section) -->
<span class="inline-flex items-center px-3 py-1 rounded-full text-sm font-medium bg-surface-100 text-primary-900">
  Residential
</span>
```

#### HTML Structure Sketch
```html
<span class="inline-flex items-center px-pad py-pad rounded-full text-sm font-medium bg-color text-color">
  Tag Text
</span>
```

#### Responsive Behavior
N/A (inline element).

#### Animation/Interaction Notes
N/A (static utility).