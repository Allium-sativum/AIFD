# Ultimate Poster Generator Specification
*Comprehensive Architectural Blueprint for the Playful Poster Studio*

This document serves as an extremely thorough, exhaustive specification to recreate the fully featured, interactive, and generative "Playful Poster Studio" HTML application.

## 1. Core Architecture & UI Layout
* **Framework**: Single-file HTML/CSS/JS with no external dependencies other than Google Fonts (`Jost`, `League Spartan`, `Syne`) and `html2canvas` for PNG exports.
* **Layout**: A full-height Flexbox layout (`height: 100vh; overflow: hidden`) split into two primary areas:
  1. **Left Canvas Stage** (`flex: 1`): Contains the interactive poster rendering area. It features panning and zooming via a wrapper container (`transform: translate(x, y) scale(z)`), reacting to mouse wheel and drag events.
  2. **Right Control Sidebar** (`width: 440px`): A scrollable panel containing all categorized configuration controls, sliders, selects, and buttons.
* **Theming**: Controlled via CSS variables attached to `:root`. A "Light Mode / Dark Mode" toggle swaps variables for `--ui-bg`, `--ui-panel`, `--ui-panel-border`, `--ui-accent`, etc., by appending a `.light-theme` class to the `body`.

## 2. The Poster Canvas & Layering System
The poster (`.poster-container`) has a base width of `480px` and a dynamic `aspect-ratio` (default `2/3`). Elements are strictly layered using `z-index`:
1. **Solid Background**: CSS background-color or linear-gradient.
2. **Photographic Background Layer**: An absolutely positioned `<img style="object-fit: cover;">`. Can be toggled between "full bleed" and "framed" (inset with a box-shadow). Includes CSS filters for Grayscale, Duotone (multiply blend), or Inverted.
3. **SVG Procedural Geometry (`z-index: 3`)**: A fluid `<svg>` overlay containing the 9x9 or 12-column grid lines, and the main `<path>` vector connector spine.
4. **Generative Typography (`z-index: 4`)**: Two absolutely positioned text blocks (Top and Bottom).
5. **Focal Target Indicator (`z-index: 5`)**: A hidden pulsing ring that appears briefly when the user clicks the canvas to set `(x, y)` focal coordinates.
6. **Surface Glaze (`z-index: 6`)**: A procedural CSS linear-gradient simulating top-down specular light and bottom bounce light.
7. **Finishing FX Layers (`z-index: 10`)**: Absolutely positioned div overlays for Grain, Halftone, Scanlines, Vignette, and Procedural SVG Textures.

## 3. Typographic Engine
* **Structure**: Text is injected as nested `<span>` elements (`div.text-block > div.text-inner > span`). This allows letter-spacing to be perfectly centered by applying a negative right margin to the inner wrapper equal to the tracking value.
* **Dynamic Sizing (`fitTypographyToPoster`)**: A highly specific recursive/looping JavaScript function. It starts the font size at `1.15rem` (or bounded by canvas height), measures the actual pixel width of `.text-inner` using `getBoundingClientRect()`, and incrementally scales the `font-size` down until the text perfectly fits within the poster's available width (`clientWidth` minus paddings).
* **Layout Presets**:
  * `Perimeter`: Top word pinned near the top margin, bottom word pinned near the bottom.
  * `Asymmetric`: Top word flex-starts (left), Bottom word flex-ends (right) with deep side paddings.
  * `Stacked`: Both words forced to the top 20% and 32% of the canvas.
* **Difference Mode**: A toggle that adds `mix-blend-mode: difference; color: white !important;` to the typography.

## 4. Procedural Vector Engine (Connector Spine)
A complex `calculateVectorAnatomy()` function generates an SVG `d` path bridging the top and bottom words.
* **Styles**:
  * `Auto`: Scans the top and bottom words for identical letters or structural stems (I, T, L, H, E, F). It calculates the exact X-coordinate of that DOM element and draws a straight line connecting them.
  * `Center`, `Dual`, `Triple`, `Cross`, `Stepped`, `Zigzag`, `Diagonal`, `Segmented` (dashed lines), `S-Curve` (Bezier curve), `Chevron`, `X-Slash`, `Brackets`.
* **Focal Interactivity**: Based on the user's clicked `(focalX, focalY)`:
  * `Straight`: Ignores the focal point.
  * `Mask`: Line breaks/gaps `11px` above and below the focal Y coordinate.
  * `Bend`: Uses an SVG Quadratic Bezier Curve (`Q`) pulling the line dynamically toward `(focalX, focalY)`.

## 5. Color Palette System
* **Inputs**: Four standard `<input type="color">` for Background, Line/Shape, Dark Text, and Light Text. Plus an optional Gradient End color.
* **Gradient Toggle**: A checkbox that switches the background to a `linear-gradient`, revealing an angle slider (`0-360deg`).
* **Presets Grid**: An array of 8 predefined hexadecimal palettes. JavaScript dynamically injects small clickable CSS swatch buttons that instantly apply the palette.
* **Randomizers**: Utilizes a seeded random generator (Mulberry32 PRNG) so specific integer seeds always yield the exact same layout structural styles. A separate "Randomize Colors" function generates raw random hex codes independent of the structural seed.

## 6. Image Cropping & Scaling Modal
* **File Input**: Intercepts local image uploads via `FileReader`.
* **Interactive Viewport**: Opens a modal where the image is drawn. Implements custom mouse and touch dragging logic (`mousedown`, `mousemove`, `touchstart`, etc.) to pan the image, plus a zoom slider.
* **Canvas Processing**: Clicking "Apply" draws the pan/zoom state onto an off-screen `<canvas>` context, rendering a perfectly cropped Base64 image.
* **Match Dimensions Toggle**: If "Match canvas size to image dimensions" is checked, it forces the poster container's `aspect-ratio` to equal the uploaded image's `naturalWidth / naturalHeight`, overriding the 2:3 default. The image perfectly scales to `Math.max()` to fill edge-to-edge.

## 7. The "Explore Variants" Grid Modal
* **Functionality**: A dedicated button opens a full-screen modal featuring a 3x3 CSS grid.
* **Generation**: It iterates 9 times, taking the current master seed, offsetting it, picking a random palette from the preset array, and cloning the main poster DOM (`poster.cloneNode(true)`). 
* **Isolated Rendering**: It runs the layout configuration and `fitTypographyToPoster` logic *specifically* on the isolated clones.
* **Selection**: Clicking any of the 9 variant cards ports that specific seed and palette back to the main sidebar UI, updates the main stage, and closes the modal.

## 8. Procedural Effects & SVG Textures
* All FX are CSS-based overlays mapped to opacity sliders (0-100%):
  * **Paper Grain**: SVG `<feTurbulence>` filter applied to a background rectangle.
  * **Halftone**: `radial-gradient` dots with `mix-blend-mode: overlay`.
  * **Scanlines**: `repeating-linear-gradient` horizontal lines.
  * **Vignette**: Heavy internal `box-shadow`.
* **Textures**: Hidden `<svg><defs>` containing complex `<filter>` nodes for `Watercolor`, `Cardboard`, and `Crumpled` paper (utilizing `feDiffuseLighting` and `feColorMatrix`). Applied to the poster via CSS `backdrop-filter: url(#tex-name)`.

## 9. Dynamic Data: Live Weather Engine
* **Inputs**: City name text field + "Apply" button.
* **API Chain**:
  1. Calls Open-Meteo Geocoding (`geocoding-api.open-meteo.com`) to convert city to lat/lon.
  2. Calls Open-Meteo Forecast (`api.open-meteo.com`) for temperature, wind, and WMO `weather_code`.
* **Thematic Mapping**: Based on the `weather_code` and `is_day`, it assigns specific aesthetics:
  * *Clear Day*: Warm yellows/oranges, cross lines.
  * *Clear Night*: Dark blues, dual lines, heavy vignette.
  * *Cloudy/Overcast*: Slate grays, cardboard texture, S-curve lines.
  * *Fog*: Silver tones, watercolor texture, segmented lines.
  * *Rain*: Deep teals, heavy scanlines, straight lines.
  * *Snow*: Frosty whites/indigos, crumpled paper, bracket lines.
  * *Thunderstorm*: Black/Purple/Yellow, zigzag lines.
* Automatically overrides poster text with City Name and Temperature/Conditions. Displays a data badge in the UI. Exposes a specialized "Randomize Layout Style" button that scrambles fonts/spacing but *preserves* the weather colors and FX.

## 10. Dynamic Data: Simulated Stock Tracker
* **Inputs**: Dropdown for "Top Gainers" vs "Top Losers".
* **Logic**: Hardcoded arrays of stock tickers. Simulates fetch latency. Calculates randomized percentage changes.
* **Visual Mapping**:
  * *Gainers*: Forces green palettes, upward `chevron` connector line, positive data formatting.
  * *Losers*: Forces red palettes, volatile `zigzag` connector line, negative data formatting.
* Renders a custom styled UI ticker badge mimicking a financial terminal. Includes a specific randomizer button that locks the line style to preserve the trend indicator while scrambling the rest.

## 11. Batch CSV/JSON Importer
* Opens a textarea modal. Users paste strings like `Word1,Word2,Seed`.
* Parses the input and displays a navigator (`< 1 / 5 >`) in the sidebar.
* Clicking Prev/Next instantly updates the text inputs and seed slider, redrawing the poster dynamically.

## 12. State & Export Management
* **URL Parsing**: Checks `window.location.search` on load for `?top=X&bottom=Y&seed=Z` to restore shareable states.
* **Exporting**:
  * Hides the focal marker temporarily.
  * **PNG**: Uses `html2canvas` multiplied by the user's chosen resolution scale (1x-4x), triggering a standard file download.
  * **Copy**: Renders to a blob and utilizes `navigator.clipboard.write`.
  * **SVG**: Grabs the `outerHTML` of the poster, wraps it in an XML-compliant `<svg>` and `<foreignObject>` wrapper, and downloads it as a `.svg` file.