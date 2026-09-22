==================================================
CURRENT HOMEPAGE STYLE HANDOFF
Build the site as a single-page class homepage that functions as an index of assignment links. Use ROG Zephyrus G16 as inspiration for scroll transitions, fade effects, section reveals, responsiveness, and premium interaction design. Use Monolith NYC as inspiration for the initial page-entry experience, including a brief opening animation that transitions naturally into the homepage. Use the reference sites only as inspiration for pacing, interaction quality, transitions, responsiveness, and premium presentation. Do not reproduce either reference site exactly. Keep the design minimalist, restrained, modern, and uncluttered. Keep the homepage contained in a single portable HTML file. Name the final file: index.html Do not require external CSS, JavaScript, fonts, videos, libraries, or assets whenever practical. The only external asset allowed is the hero image file:
hero.png
HERO IMAGE SOURCE REQUIREMENTS
The hero image must always use the external file: hero.png The hero image must never be embedded directly into the HTML. Do not use: data:image/png;base64,… Do not:
* Embed the hero image as Base64.
* Convert hero.png into a data URI.
* Encode hero.png into the HTML.
* Generate a replacement hero image.
* Replace hero.png with placeholder artwork.
* Preserve embedded Base64 hero images from an existing homepage.
* Create a synthetic or AI-generated replacement for hero.png.
* Substitute another image for hero.png.
* Rename the hero reference without specific instructions. Always load the hero image using: background-image: url("hero.png"); The final HTML must contain a direct reference to: url("hero.png") The final HTML must not contain: data:image/png;base64 anywhere in the file. If an existing homepage contains: background-image: url('data:image/png;base64,…'); remove the embedded hero image entirely and replace it with: background-image: url("hero.png"); When rebuilding or editing an existing homepage:
* Do not preserve embedded Base64 hero images.
* Remove all embedded hero image data.
* Replace the embedded image with a direct hero.png reference.
* Do not generate a substitute image.
* Do not add placeholder hero artwork.
* Do not add a fallback image that could replace hero.png. Before providing the final homepage, verify that:
* hero.png is referenced directly.
* The reference is exactly url("hero.png").
* No Base64 image data exists.
* No embedded hero image exists.
* No placeholder hero image exists.
* No generated replacement hero image exists.
- The hero loads only from hero.png.
COLOR SYSTEM
Primary page background:
000000
Primary text:
FFFFFF
Accent:
D4AF37
Moving background secondary color:
A52A2A
Use the gold accent color for:
* Links
* Borders
* Hover underlines
* Focus states
* Section dividers
* Active UI indicators
* Subtle glow effects Keep the overall page visually dark. Maintain strong contrast throughout the site. The page must remain primarily black. Use #A52A2A only as the secondary color inside the animated moving background. Do not replace the primary black background with a solid brown background. Do not use dark grey as the moving background’s secondary color.
Do not introduce additional major accent colors.
SITE STRUCTURE
The site structure must appear in this exact order:
1. Hero
2. Introduction
3. Work / Assignment Links
4. Footer Do not change the order of these sections. The footer must contain the email address. Place the email only at the bottom of the page. Do not display the email address in:
* The hero
* The introduction
* The Work section
* An additional contact section
- A floating control
HERO
Place the hero section at the very top of the page. Do not place page content, margins, controls, or decorative elements above the hero. The hero image must span the full viewport width. Use: background-image: url("hero.png"); background-size: cover; background-position: center; background-repeat: no-repeat; Hero height: Desktop: 60vh Tablet: 55vh Mobile: 45vh Minimum height: 360px Add a subtle dark overlay over the hero image for readability. Use an overlay approximately equivalent to: rgba(0,0,0,.30) to rgba(0,0,0,.40) The overlay must not be so dark that the hero artwork becomes difficult to see. Position the hero content in the center of the hero section. Place the name directly on top of the hero image. Keep the hero text treatment minimal. Use a restrained text shadow only when needed for readability. Do not place additional decorative elements inside the hero. Do not add:
* Decorative icons
* Navigation controls
* Theme toggles
* Pixel artwork
* Stars
* Moons
* Clouds
* Butterflies
* Flowers
* Bees
* Fireflies
* Video
* Additional background graphics The hero image must remain the main visual element. The hero image may be cropped by background-size: cover.
Do not stretch or distort the hero image.
TYPOGRAPHY
Use the following heading font stack: system-ui -apple-system Segoe UI Arial sans-serif Use the following body font stack: Ink Free Segoe Print Bradley Hand cursive Do not load external web fonts. Do not link to Google Fonts or another font-hosting service. Use approximately: Hero title: 4rem to 6rem fluid scale Section headings: 1.4rem Subheadings: 1.1rem Body: 1rem Small text: 0.875rem Use a fluid CSS scale for the hero title. Keep section headings visually small relative to the overall page. Use a body line-height of approximately: 1.6 Preserve readable line lengths on desktop and mobile screens. Avoid extremely thin font weights.
Maintain strong text contrast.
LAYOUT
Use a centered content container. Maximum content width: 1200px Horizontal padding: Desktop: 32px Mobile: 20px Responsive breakpoints: Mobile: 0 to 767px Tablet and laptop: 768 to 1199px Desktop: 1200px and above Vertical spacing between major sections: Desktop: Approximately 80px Mobile: Approximately 48px Maintain consistent alignment and spacing throughout the page. Do not allow content panels or assignment buttons to touch the edge of the viewport. Prevent horizontal page scrolling.
Keep the content centered within the viewport.
PANELS
Place the introduction content inside a dark translucent panel. Place the Work content inside a separate dark translucent panel. Use the following panel background: rgba(0,0,0,.82) Use a panel corner radius of approximately: 24px Use thin gold borders on major content panels. Use a border approximately equivalent to: 1px solid #D4AF37 A partially transparent version of #D4AF37 may be used for restraint. Add subtle shadows to separate panels from the moving background. Panel shadows must remain restrained. Do not use oversized or excessively bright glow effects. Panels must remain readable when the brown portion of the moving background passes behind them. Use backdrop blur only as a progressive enhancement.
The panels must remain readable if backdrop-filter is unsupported.
ASSIGNMENT LINKS
Keep every existing Work item and every existing assignment link already present in the supplied homepage. Do not remove assignments. Do not rename assignments unless specifically instructed. Do not replace working URLs. Do not invent destination URLs. Do not convert an existing working URL into a placeholder. If an existing assignment uses: href="#" preserve: href="#" unless a replacement URL is specifically provided. Display assignment links inside a responsive grid. Grid layout: Desktop and laptop: 2 columns Mobile: 1 column Assignment links must appear as filled buttons. Assignment button background:
000000
Assignment button text:
FFFFFF
Assignment button border: 1px solid #D4AF37 Assignment button corner radius: Approximately 18px to 24px Assignment button minimum height: 64px Assignment button padding: 20px top and bottom 24px left and right Center button content vertically and horizontally. Assignment buttons must remain touch friendly. Buttons must not overlap or extend outside the content container. On hover:
* Underline the assignment title in gold.
* Lift the button by approximately 2px.
* Slightly increase the shadow depth.
* Keep the button background black.
* Keep the interaction restrained.
* Do not create distracting movement. On active or click:
* Slightly depress the button.
* Reduce the shadow.
* Provide immediate visual feedback. Provide keyboard accessibility for every assignment link. Provide a visible gold focus outline. Use: :focus-visible where supported. Do not remove browser focus indicators without providing an accessible replacement.
Do not disable assignment links solely because the URL is currently a placeholder.
MOVING BACKGROUND
Create a moving background using only CSS and/or JavaScript inside the HTML file. Do not use video. Do not use a background image for the moving background. Do not use hero.png as part of the moving background. The hero image and moving background are separate visual systems. Build the moving background from large animated CSS gradients. Moving background colors:
000000
A52A2A
The animated background must transition smoothly between black and brown. Do not use dark grey as the secondary moving-background color. The primary visual state should remain black. Use #A52A2A as a restrained secondary gradient color. The brown color should appear as an atmospheric shift rather than as a bright, solid background. Use partially transparent brown gradients where necessary to maintain the dark appearance. Motion characteristics:
* Smooth
* Continuous
* Subtle
* Medium speed
* No flashing
* No strobing
* No abrupt color changes
* No rapid movement
* No distracting direction changes Loop duration: Approximately 18 to 24 seconds Use approximately: 22 seconds as the preferred default duration. The animation must loop continuously. Animate a combination of:
* Gradient position
* Layer position
* Scale
* Subtle opacity changes The color movement must remain visible. Do not make the animation so subtle that the background appears completely static. Do not make the animation so strong that it distracts from the page content. Text must remain readable at all times. White text must maintain strong contrast when the brown gradient moves behind the content. Panels must remain dark enough to preserve readability. A very low-opacity CSS texture layer may be added only if additional depth is needed. Do not use an image to create the texture.
The moving background must not affect the hero image itself.
MOVING BACKGROUND STACKING REQUIREMENTS
The moving gradient must appear above the body’s solid black paint layer but behind all visible page content. Do not place the moving background at: z-index: -1 or: z-index: -2 when the body or HTML element has an opaque black background. A negatively stacked moving background can be hidden behind the body background and appear not to work. Use a dedicated moving background element with approximately: position: fixed; inset: -20vmax to -25vmax; z-index: 0; pointer-events: none; The moving background element should cover an area larger than the viewport so movement does not reveal empty edges. Place the principal page content above the moving background. The following elements must use a higher stacking level:
* Hero
* Main content
* Introduction panel
* Work panel
* Footer Use approximately: position: relative; z-index: 1; for the hero, main content, and footer. The entry animation may use a higher stacking level, such as: z-index: 100; The stacking order must be:
1. Body’s solid black fallback background
2. Animated black-to-brown gradient at z-index: 0
3. Hero, main content, and footer at z-index: 1
4. Temporary entry animation above the page content The moving background must use: pointer-events: none; so it never blocks assignment links, email links, scrolling, text selection, or keyboard interaction. Do not use an opaque page-sized layer above the moving background. If a dark overlay is applied to the moving background, keep it light enough that #A52A2A remains visible. Use approximately: rgba(0,0,0,.10) to rgba(0,0,0,.20) for a moving-background dimming overlay. Do not use an excessively dark overlay such as a nearly opaque black layer. The panel backgrounds may remain: rgba(0,0,0,.82) because the moving color should primarily remain visible around and between the panels. Before providing the final homepage, verify that:
* The animated gradient is visible around the content panels.
* The brown color becomes visibly stronger during part of the animation.
* The background does not remain completely black throughout the animation.
* The moving layer is not hidden behind the body background.
* The moving layer does not cover the content.
* The moving layer does not block pointer interaction.
* The hero image remains separate and unaffected.
- The page content remains readable.
SCROLL REVEALS
Use ASUS-inspired reveal animations for content sections. Before entering the viewport, reveal-enabled sections should have:
* Slight transparency
* Slight blur
* Slight downward offset
* Slight scale reduction When entering the viewport, sections should transition to:
* Full opacity
* No blur
* Full scale
* Natural position Use: IntersectionObserver Use an intersection threshold of approximately: 0.18 Allow reveal animations to replay when sections leave and re-enter the viewport. Use animation durations between: 600ms and 900ms Preferred duration: Approximately 760ms Use premium smooth easing. Use an easing curve similar to: cubic-bezier(.22,1,.36,1) Keep the movement restrained. Do not use:
* Bouncing
* Spinning
* Excessive rotation
* Exaggerated scaling
* Rapid movement Reveal animations must not interfere with links, keyboard navigation, or reading. Content must remain visible if JavaScript does not run. Use progressive enhancement so JavaScript adds the hidden reveal starting state only after JavaScript is confirmed to be available.
If IntersectionObserver is unavailable, display all content immediately.
ENTRY ANIMATION
Include a Monolith-inspired entry animation during initial page load. The entry experience must be:
* Brief
* Minimal
* Elegant
* Restrained
* Naturally connected to the homepage Do not delay access to the content for more than: 1.5 seconds Preferred total duration: Approximately 1.25 seconds Avoid excessive animation complexity. The entry animation should transition naturally into the hero section. Do not use:
* An external video
* An external animation file
* An external script
* A loading spinner that waits unnecessarily
* A long artificial delay Do not permanently cover the content. The entry layer must become hidden or non-interactive after the animation completes. Use: pointer-events: none; on the entry layer so it does not trap interaction. The entry animation must not trap keyboard focus. The entry animation may use a high stacking level such as: z-index: 100;
Reduced-motion users must see the content immediately.
REDUCED MOTION
Respect the user’s reduced-motion preference. Use: @media (prefers-reduced-motion: reduce) When reduced motion is enabled:
* Disable the moving background animation.
* Disable scroll reveal motion.
* Disable blur-based reveal effects.
* Disable scale-based reveal effects.
* Disable the entry animation.
* Disable nonessential transitions.
* Display all content immediately.
* Keep all content visible.
* Preserve full keyboard accessibility. Do not hide reveal-enabled content when JavaScript is unavailable. The homepage must remain usable if IntersectionObserver is unavailable.
The static background shown under reduced motion may preserve the black and brown color system, but it must not move.
RESPONSIVENESS
The homepage must be fully usable on:
* Desktop
* Laptop
* Tablet
* Mobile Maintain consistent spacing and alignment. Preserve readability across all devices. The hero image must remain full width at every screen size. The hero image may be cropped by: background-size: cover; but it must not be stretched or distorted. Use: Desktop hero height: 60vh Tablet hero height: 55vh Mobile hero height: 45vh Maintain a minimum hero height of: 360px Use a two-column assignment grid on laptop and desktop layouts. Use a one-column assignment grid on mobile layouts. Ensure that all assignment links remain touch friendly. Prevent horizontal page scrolling. Do not allow typography to overflow the viewport. Ensure the moving background covers the entire viewport on all screen sizes.
The moving background’s oversized inset must prevent blank edges during animation.
ACCESSIBILITY
Use semantic HTML elements where appropriate. Use:
* header
* main
* section
* nav
* footer Use a logical heading structure. Use sufficient text contrast. Provide visible keyboard focus states. Ensure assignment links are accessible using a keyboard. Do not convey important information through color alone. Respect reduced-motion preferences. Use descriptive accessible labels only when necessary. Decorative layers must not interfere with assistive technologies. Use: aria-hidden="true" only for purely decorative elements. Apply aria-hidden="true" to:
* The moving background layer
* Decorative entry animation content
* Decorative section dividers Do not apply aria-hidden="true" to meaningful content. The page must remain usable if animation does not run. The moving background must use: pointer-events: none;
so it does not block mouse, touch, or keyboard interaction.
AESTHETIC RULES
Use gold accent details sparingly and intentionally. Maintain a minimalist aesthetic. Avoid clutter. Avoid decorative elements that distract from content. Do not preserve unrelated decorative elements from an older homepage when those elements conflict with this handoff. Remove unnecessary:
* Pixel landscapes
* Stars
* Moons
* Clouds
* Flowers
* Butterflies
* Bees
* Fireflies
* Theme toggles
* Light-mode controls
* Decorative animation layers Keep the visual emphasis on:
* The hero image
* The student name
* The introduction
* The assignment links
* The moving black-to-brown background Do not imitate the reference websites exactly.
Use the reference websites only as inspiration for pacing, interaction quality, transitions, and responsiveness.
EXTERNAL ASSET RESTRICTIONS
The only external asset permitted is: hero.png Do not load:
* External CSS
* External JavaScript
* External fonts
* External videos
* External icons
* External images
* External tracking scripts
* External analytics
* External UI libraries
* External animation libraries Do not include Google Fonts links. Do not include CDN links. Do not include preconnect links for external services. All CSS must be contained inside index.html.
All JavaScript must be contained inside index.html.
WORK CONTENT PRESERVATION
Before rebuilding the homepage, inspect the supplied index.html. Extract and preserve:
* Every Work item
* Every assignment title
* Every assignment number
* Every assignment URL
* The footer email address
* Existing course information that remains relevant Do not invent missing URLs. If an assignment uses href="#", preserve that value unless the user supplies a replacement. If an assignment has a working URL, preserve the exact URL. Do not replace a working URL with href="#". Do not add assignments that were not present unless specifically instructed. Do not remove assignments unless specifically instructed.
Do not silently rewrite assignment names.
FINAL VERIFICATION
Before providing the completed homepage, verify all of the following:
* The final file is named index.html.
* The final page is a single HTML file.
* All CSS is inside index.html.
* All JavaScript is inside index.html.
* hero.png remains an external file.
* The HTML contains url("hero.png").
* The HTML does not contain data:image/png;base64.
* No hero image is embedded as Base64.
* No replacement hero image was generated.
* No placeholder hero image was added.
* No external font is loaded.
* No external CSS is loaded.
* No external JavaScript is loaded.
* No external video is loaded.
* No external CDN is used.
* No preconnect link is used.
* The moving background uses CSS and/or JavaScript gradients.
* The moving background uses #000000 and #A52A2A.
* Dark grey is not used as the secondary moving-background color.
* The moving gradient layer uses z-index: 0.
* The moving gradient layer uses pointer-events: none.
* The moving gradient layer is not hidden behind the body background.
* The hero, main content, and footer use a higher stacking level than the moving background.
* The hero, main content, and footer use approximately z-index: 1.
* The brown gradient is visibly present during part of the animation.
* The moving background does not cover the page content.
* The moving background does not block links or scrolling.
* The hero image remains separate from the moving background.
* The email appears only in the footer.
* Every existing assignment is preserved.
* Every existing assignment URL is preserved.
* No assignment URL was invented.
* The assignment grid uses two columns on laptop and desktop.
* The assignment grid uses one column on mobile.
* Keyboard focus states are visible.
* Reduced-motion preferences are respected.
* The site remains readable on phones and laptops.
* Content remains visible without JavaScript.
* Content remains visible without IntersectionObserver.
- The complete source code is not displayed in chat.
FINAL OUTPUT REQUIREMENTS
The final deliverable must be:
* A downloadable file
* Named index.html
* A single HTML file
* CSS inside the file
* JavaScript inside the file Do not display the complete source code in chat.
Always provide the finished homepage as a downloadable HTML file.
PERMANENT STYLE PRESERVATION
Every future build or edit must preserve:
* Single-page homepage structure
* Hero image at the top
* External hero.png hero image
* Direct url("hero.png") reference
* No Base64 image data
* No embedded hero image
* Name placed on the hero image
* Ink Free body typography
* System font heading typography
* Small heading style
* Black primary background
* White text
* Gold accent system
* Black assignment buttons
* Gold assignment button borders
* Gold hover underline
* Rounded content panels
* Rounded assignment buttons
* Two-column desktop and laptop assignment layout
* One-column mobile assignment layout
* Medium-speed black-to-brown moving gradient background
* #A52A2A as the moving background secondary color
* No dark grey as the moving background secondary color
* Animated background at z-index: 0
* Hero, main content, and footer above the animated background
* Hero, main content, and footer at approximately z-index: 1
* Animated background with pointer-events: none
* Animated background visible above the body’s solid black fallback
* No opaque layer hiding the animated brown gradient
* ASUS-inspired scroll transitions
* Monolith-inspired entry animation
* Responsive behavior
* Accessibility support
* Reduced-motion support
* Email only in the footer
* Minimalist presentation
* One portable index.html file
* No external assets except hero.png Always provide the fully updated homepage as a downloadable HTML file rather than displaying the complete source code in chat.