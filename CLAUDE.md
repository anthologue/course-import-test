# Mini-Course from Slides

## Stack & Conventions

- **Stack**: Plain static site — HTML + CSS + vanilla JS. No build step, no framework, no dependencies.
- **Single page, external CSS/JS allowed**: The entire project (every lesson section and the navigation between them) lives on one `index.html` page — no additional HTML pages. CSS and JS may live in external `styles.css` / `script.js` files (or be inlined) as convenient; external stylesheets and scripts are permitted.
- **Delivery**: Committed as files in this repo (viewable locally, deployable via any static host / GitHub Pages).
- **Folder structure**:
  ```
  /index.html        single page: all lesson sections, nav
  /styles.css         styling (if not inlined)
  /script.js          smooth-scroll nav / active-section highlighting (if needed)
  /CLAUDE.md
  ```
- **One-time build**: This is a fixed build from a specific, known set of 3-5 slides — not a feature for visitors to upload their own content. No upload UI, no backend.
- **Content style**: Each slide becomes a lesson section written as normal prose (explanatory paragraphs), not a slide-by-slide bullet dump. No embedded slide images — slides are source material only.
- **Section shape** (apply to every lesson section built from a slide): intro/explanation prose → "Key Takeaways" bullet box → one short ungraded self-check/reflection question → one graded check-in question (multiple-choice or short-answer) testing that section's key idea, with immediate right/wrong feedback shown inline (never a separate quiz screen) and no gating — the student can move to the next section regardless of the answer.
- **Audience**: Complete beginners. Plain language, define terms as they're introduced, avoid unexplained jargon.
- **Navigation**: One section visible at a time, switched via JavaScript (no separate HTML pages, no full reloads) — an on-page sidebar lists every section for direct jump-to, plus previous/next buttons to move sequentially. Section switch also updates the URL hash so a section can be linked/reloaded directly.
- **Visual style**: "Playful Pastel" direction (chosen from 3 proposed options). Soft pastel palette — peach and teal duo-accent on a warm off-white background, rounded elements. Fonts: `Baloo 2` (rounded, weight 600-800) for headings, `Quicksand` for body text, both via Google Fonts. Avoid a cold/corporate look.
- **Testing approach**: No automated tests (static content site). Verify by opening `index.html` in a browser and checking nav links jump to the right section and content reads well.
- **Naming**: lowercase-hyphenated anchor IDs matching section topics (e.g. `#intro-to-x`), not `#slide-1` etc.

## Feature Plan

### Phase 1 — Content ingestion
- Receive 3-5 slide images from user in-session.
- For each slide, extract the core concept and rewrite as lesson prose (not transcription).
- Data model per section:
  ```
  {
    id: string,          // anchor slug
    title: string,        // lesson section heading
    body: string[],       // prose paragraphs
    takeaways: string[],  // bullet list
    selfCheck: string     // one reflection question
  }
  ```
- Output: ordered list of section objects, one per slide.

### Phase 2 — Page structure [done]
- Built `index.html` (single file): sidebar nav listing every section, one section shown at a time (JS toggles visibility, no page reloads), previous/next controls, URL hash sync for direct linking.
- Playful Pastel theme inlined (peach/teal accents on warm off-white, `Baloo 2`/`Quicksand` fonts, rounded cards for takeaways/quick-check boxes).
- Sections built from the 3 slides shared (Java inheritance example — Member superclass / Student & Staff subclasses), reordered into problem → solution → outcome for a beginner-friendly narrative (slide order as shared was solution → outcome → problem).

### Phase 2.5 — Practice & assessment [done]
- Added a graded check-in question (MC or short-answer) after each lesson's takeaways/self-check, with inline right/wrong feedback; answering never blocks moving to the next section.
- Added a 4th section, "Try It Yourself": an interactive simulator where adding an attribute to the `Member` superclass card live-updates both the `Student` and `Staff` subclass cards, demonstrating inheritance experientially.
- Added a 5th section, a 3-question final quiz recapping all three lessons, graded inline per question with a running score.

### Phase 3 — Review & polish
- Open in browser, verify: nav/sidebar links work, reading flow feels like a course (not a deck), takeaways/self-check/check-in present in every lesson section, simulator and quiz behave correctly, responsive on mobile width.
- Incorporate user feedback on tone/content per section.

### Phase 4 — Finalize
- Confirm final content with user.
- Commit and push to `claude/mini-course-from-slides-rkqnsp`.
