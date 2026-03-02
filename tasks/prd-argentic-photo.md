# PRD: Argentic / Leica Photo Effect Web Interface

## Introduction / Overview

A client-side web application that lets users upload one or more iPhone photos and transform them into argentic-style (analog film) images inspired by Leica cameras. Users can choose from curated film presets, toggle between black & white and colour modes, and fine-tune parameters like grain, vignette, contrast, and sepia. Processed photos can be downloaded individually or compared side-by-side with their originals.

## Goals

1. Provide a simple, single-page web interface (no build step, no server) that runs entirely in the browser.
2. Support batch upload of multiple photos with per-photo preset and parameter editing.
3. Offer realistic film-look presets (Leica M6, Leica M3, Tri-X 400, Ilford HP5) for both B&W and colour.
4. Allow before/after comparison for each photo.
5. Enable one-click download of each processed photo.

## User Stories

- **US-1:** As a user, I can drag-and-drop or browse to upload multiple iPhone photos at once.
- **US-2:** As a user, I can select a film preset from a dropdown/card list and see it applied live.
- **US-3:** As a user, I can switch between Black & White mode and Colour mode per photo.
- **US-4:** As a user, I can adjust grain intensity, vignette strength, contrast, and sepia tone with sliders.
- **US-5:** As a user, I can toggle a before/after comparison view for any photo.
- **US-6:** As a user, I can download the processed version of any photo individually.

## Functional Requirements

1. The app must be a single HTML file (+ optional linked CSS/JS) with zero server dependencies.
2. All image processing must happen client-side using the Canvas API.
3. The upload area must accept multiple image files (JPEG, PNG, HEIC where supported) via drag-and-drop or file picker.
4. Each uploaded photo must appear in a gallery/grid with its own controls.
5. The following presets must be available:
   - **Leica M6** — high contrast B&W, moderate grain, strong vignette
   - **Leica M3** — softer contrast B&W, fine grain, subtle vignette
   - **Tri-X 400** — punchy B&W, heavy grain, slight fade
   - **Ilford HP5** — classic tonal range B&W, medium grain
   - **Kodak Portra 400** — warm colour, fine grain, soft contrast
   - **Fuji Superia** — cool-shifted colour, visible grain, slight vignette
6. Users must be able to toggle B&W ↔ Colour independently of the preset.
7. Adjustable sliders: Grain (0–100), Vignette (0–100), Contrast (0–100), Sepia (0–100), Fade (0–100).
8. A before/after toggle or slider must let users compare the original and processed image.
9. A download button per photo must save the processed image as JPEG.

## Non-Goals (Out of Scope)

- Server-side processing or cloud storage.
- User accounts / authentication.
- Social sharing features.
- Video processing.
- AI-based style transfer.

## Design Considerations

- Modern, minimal dark UI reminiscent of a photo darkroom.
- Responsive layout (works on desktop and tablet).
- Smooth transitions when switching presets.

## Technical Considerations

- Single HTML file approach (inline CSS + JS) for maximum simplicity.
- Use `<canvas>` for pixel manipulation (grain, contrast, vignette, desaturation, sepia).
- Use `URL.createObjectURL` for fast in-memory image previews.
- HEIC support depends on the browser; gracefully fall back with an error message if unsupported.

## Success Metrics

- User can upload → apply preset → download a processed photo in under 10 seconds on a modern device.
- All 6 presets produce visually distinct, recognisable film looks.

## Open Questions

- None at this stage.
