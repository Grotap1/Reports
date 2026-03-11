# Grotap Reports Publisher

This project publishes HTML reports to GitHub Pages for team sharing.

## Live Site
- **Homepage:** https://grotap1.github.io/Reports/ (Team Communication page)
- **Repo:** https://github.com/Grotap1/Reports
- **Branch:** main (GitHub Pages deploys from main, legacy mode)

## Key Pages
- `index.html` — "Grotap Team Communication" landing page. Lists ALL reports, newest first. Title: "Grotap Operational Report". Reports are NEVER deleted from this page.
- Individual report files (e.g., `app-report.html`) — full detail pages linked from index.

## Publishing Workflow (EVERY new report must follow this)

1. Create the report HTML file (self-contained, dark theme, kebab-case filename)
2. **Update `index.html`** — this is CRITICAL, every report must be added:
   a. Add new report entry at the TOP of the timeline (below the month-divider)
   b. Give it `class="report-entry latest-entry"` and badge `class="entry-badge new"`
   c. Remove `latest-entry` class and change badge from `new` to empty on the previous top entry
   d. Add a new `month-divider` if it's a new month
   e. Update the `report-count` number in the header
   f. NEVER remove or modify any existing report entries
3. `git add index.html <new-report>.html`
4. `git commit -m "Add <report name>"`
5. `git push origin main`
6. Site auto-deploys in ~60 seconds

## index.html Structure

```html
<!-- Inside .timeline, newest report on top -->
<div class="month-divider">Month Year</div>

<a href="filename.html" class="report-entry latest-entry">
  <div class="entry-top">
    <span class="entry-date">Month Day, Year</span>
    <span class="entry-badge new">Latest</span>
  </div>
  <div class="entry-title">Report Title</div>
  <div class="entry-summary">2-3 sentence summary of what the report covers.</div>
  <div class="entry-footer">
    <div class="entry-tags">
      <span class="tag">Tag1</span>
      <span class="tag">Tag2</span>
    </div>
    <span class="view-link">View full report <span class="arrow">&rarr;</span></span>
  </div>
</a>
```

## File Conventions
- Reports are self-contained HTML files (inline CSS, no external dependencies)
- Use kebab-case for filenames: `app-report.html`, `q1-review.html`
- Keep all reports in the repo root

## Report Style Guide
- Dark theme using CSS custom properties
- Responsive design with max-width container
- Font stack: Inter, system fonts fallback
- Color palette:
  - Background: `#0f1117`, Cards: `#1a1d27`, Border: `#2a2d3a`
  - Accent: `#6366f1` / `#818cf8`, Green: `#22c55e`, Cyan: `#06b6d4`
  - Text: `#e2e8f0`, Muted: `#94a3b8`

## Rules
- Reports are NEVER deleted. The index page is an ever-growing timeline.
- Newest report always appears at the top with the "Latest" badge.
- Every report gets a date, title, summary, tags, and a link to its detail page.
