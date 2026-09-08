# Mini-Course from Slides

## Stack & Conventions

- **Stack**: Plain static site — HTML + CSS + vanilla JS. No build step, no framework, no dependencies.
- **Delivery**: Committed as files in this repo (viewable locally, deployable via any static host / GitHub Pages).
- **Folder structure**:
  ```
  /index.html        single scrolling page, all lesson sections
  /styles.css         all styling
  /script.js          smooth-scroll nav / active-section highlighting (if needed)
  /CLAUDE.md
  ```
- **One-time build**: This is a fixed build from a specific, known set of 3-5 slides — not a feature for visitors to upload their own content. No upload UI, no backend.
- **Content style**: Each slide becomes a lesson section written as normal prose (explanatory paragraphs), not a slide-by-slide bullet dump. No embedded slide images — slides are source material only.
- **Section shape** (apply to every section): intro/explanation prose → "Key Takeaways" bullet box → one short ungraded self-check/reflection question.
- **Audience**: Complete beginners. Plain language, define terms as they're introduced, avoid unexplained jargon.
- **Navigation**: Single scrolling page with an anchor-link table of contents at the top (jump-to-section), not separate pages per lesson.
- **Visual style**: Warm/friendly — rounded elements, approachable colors, light illustrative/emoji touches. Avoid a cold/corporate look.
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

### Phase 2 — Page structure
- Build `index.html`: header/course title, top-of-page TOC (anchor links to each section), sections in slide order, each rendering the section data-model shape above.
- Build `styles.css`: warm/friendly theme (palette, rounded cards for takeaways box, typography for beginner readability).
- Add smooth-scroll / active-link highlighting in `script.js` if TOC needs it (optional — CSS anchor scroll may suffice).

### Phase 3 — Review & polish
- Open in browser, verify: TOC links work, reading flow feels like a course (not a deck), takeaways/self-check present in every section, responsive on mobile width.
- Incorporate user feedback on tone/content per section.

### Phase 4 — Finalize
- Confirm final content with user.
- Commit and push to `claude/mini-course-from-slides-rkqnsp`.
