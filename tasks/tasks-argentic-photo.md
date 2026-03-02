## Relevant Files

- `index.html` - Single-file web application containing all HTML, CSS, and JavaScript for the Argentic photo lab.

### Notes

- This is a single HTML file project with no build step or dependencies, so no package manager or test runner is needed.
- Open `index.html` directly in a browser to test.

## Instructions for Completing Tasks

**IMPORTANT:** As you complete each task, you must check it off in this markdown file by changing `- [ ]` to `- [x]`. This helps track progress and ensures you don't skip any steps.

Example:
- `- [ ] 1.1 Read file` → `- [x] 1.1 Read file` (after completing)

Update the file after completing each sub-task, not just after completing an entire parent task.

## Tasks

- [ ] 0.0 Create feature branch
  - [ ] 0.1 Initialize a git repository (`git init`) and create a branch (`git checkout -b feature/argentic-photo`)

- [ ] 1.0 Build the page structure and dark UI shell
  - [ ] 1.1 Create `index.html` with HTML5 boilerplate, meta viewport, and page title "Argentic — Film Photo Lab"
  - [ ] 1.2 Add a `<header>` with the app name and tagline
  - [ ] 1.3 Add the `<style>` block with CSS variables for the dark "darkroom" theme (`--bg`, `--surface`, `--border`, `--accent`, etc.)
  - [ ] 1.4 Style the body, header, and base typography (font-family, colors, letter-spacing)
  - [ ] 1.5 Add responsive media queries so the layout works on desktop and tablet (single-column below 900px)

- [ ] 2.0 Implement multi-file upload system
  - [ ] 2.1 Add a `#drop-zone` div with instructions text and a hidden `<input type="file" multiple accept="image/*">`
  - [ ] 2.2 Style the drop zone with a dashed border, hover/drag-over highlight using the accent color
  - [ ] 2.3 Add `dragover`, `dragleave`, and `drop` event listeners on the drop zone to handle drag & drop
  - [ ] 2.4 Add a `change` event listener on the file input to handle the file picker
  - [ ] 2.5 Create a `handleFiles()` function that filters for image types and calls `addPhoto()` for each valid file
  - [ ] 2.6 Make the drop zone clickable so it triggers the file input

- [ ] 3.0 Build per-photo card layout with controls panel
  - [ ] 3.1 Create a `#gallery` container with flexbox column layout and gap between cards
  - [ ] 3.2 Create the `.photo-card` component with a two-column CSS grid: image area (left) + controls panel (right)
  - [ ] 3.3 Build the image area (`.img-area`) with a `<canvas>` element, a remove button, and overlay elements for the comparison view
  - [ ] 3.4 Build the controls panel with sections: Preset grid, Mode toggle (B&W / Colour), 5 sliders, and action buttons
  - [ ] 3.5 Style the preset buttons as a 2-column grid with `.active` state highlighting
  - [ ] 3.6 Style the mode toggle as two flex buttons with `.active` state
  - [ ] 3.7 Style the slider rows (label + range input + value display) with accent color
  - [ ] 3.8 Style the action buttons row (Before/After + Download) at the bottom of the controls panel

- [ ] 4.0 Implement Canvas-based image processing engine
  - [ ] 4.1 Create a `render()` function that debounces processing via `requestAnimationFrame`
  - [ ] 4.2 Create `applyEffect()` — draw the original image onto the canvas, then get its `ImageData`
  - [ ] 4.3 Implement contrast adjustment: compute a factor from the 0–100 slider value and apply per-pixel
  - [ ] 4.4 Implement B&W conversion: compute luminance (0.299R + 0.587G + 0.114B) and set R=G=B when enabled
  - [ ] 4.5 Implement sepia toning: blend original pixel with sepia-matrix values based on the sepia amount
  - [ ] 4.6 Implement fade (lifted blacks): mix pixel values toward a lifted floor based on fade amount
  - [ ] 4.7 Implement grain: add random noise scaled by grain amount to each pixel
  - [ ] 4.8 Put the processed `ImageData` back on the canvas
  - [ ] 4.9 Implement vignette: draw a radial gradient overlay from transparent center to dark edges based on vignette amount
  - [ ] 4.10 Create a `clamp()` helper to keep pixel values within 0–255

- [ ] 5.0 Create the 6 film presets with distinct parameter values
  - [ ] 5.1 Define a `PRESETS` object with keys: `leicaM6`, `leicaM3`, `triX400`, `hp5`, `portra400`, `superia`
  - [ ] 5.2 Set Leica M6 values: B&W, grain 55, vignette 65, contrast 75, sepia 0, fade 5
  - [ ] 5.3 Set Leica M3 values: B&W, grain 30, vignette 35, contrast 50, sepia 0, fade 10
  - [ ] 5.4 Set Tri-X 400 values: B&W, grain 80, vignette 25, contrast 70, sepia 0, fade 15
  - [ ] 5.5 Set Ilford HP5 values: B&W, grain 50, vignette 30, contrast 55, sepia 0, fade 8
  - [ ] 5.6 Set Kodak Portra 400 values: Colour, grain 20, vignette 25, contrast 45, sepia 15, fade 5
  - [ ] 5.7 Set Fuji Superia values: Colour, grain 45, vignette 35, contrast 50, sepia 0, fade 10
  - [ ] 5.8 Create `setPreset()` — apply a preset's values to the card state, refresh controls, and re-render

- [ ] 6.0 Implement before/after comparison view and per-photo JPEG download
  - [ ] 6.1 Create `toggleCompare()` — show/hide the original image overlay with a vertical split (clip-path 50%)
  - [ ] 6.2 Show a divider line and "Before" / "After" labels when comparison is active
  - [ ] 6.3 Create `download()` — export the canvas as JPEG (`canvas.toDataURL('image/jpeg', 0.92)`) and trigger a download
  - [ ] 6.4 Create `removeCard()` — remove the card DOM element, revoke the object URL, and delete the state
