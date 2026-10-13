---
name: html-report
description: Use ONLY when creating or revising an HTML report or report webpage. Trigger on precise requests involving HTML reports, HTML-format reports, report webpages, or turning source material into a webpage report. Do not trigger for general technical articles, documentation, standalone SVG work, or formula formatting without an HTML report.
---

# HTML Report

Create HTML reports as readable, calm technical documents rather than dashboard-style pages. Prefer a self-contained file that can be opened directly in a browser without a build step.

## Visual Language

- Use a restrained deep-blue and blue-gray palette: dark navy for titles, deep blue for section markers, gray-blue for borders and metadata.
- Keep backgrounds mostly white or very light gray-blue.
- Use fine borders, modest spacing, and square or lightly rounded containers. Avoid oversized cards, heavy shadows, gradients, and decorative UI chrome.
- Use a title block with a strong bottom rule. Put the document label on the left and a generated timestamp on the right.
- Use section headings with a left vertical rule and optional English subtitle.
- Use callouts sparingly for conclusions, key ideas, warnings, and notes.

## Required Structure

- Use semantic HTML: `header`, `nav`, `main`, `section`, `figure`, `figcaption`, `table`, and `footer` where appropriate.
- Add a jumpable table of contents near the top. Each entry must link to a unique section `id`.
- Keep the report content in the HTML rather than relying on a runtime framework.
- Add responsive behavior for narrow screens, especially for two-column grids and wide tables.

## Diagrams And Formulas

- Prefer inline SVG for diagrams that belong to the report. It keeps the report portable and avoids missing relative assets.
- If an SVG is kept as a separate asset, reference it with a stable relative path and meaningful `alt` text.
- Set SVG `viewBox`, dimensions, colors, labels, and arrows explicitly. Use the same restrained palette as the report.
- Use lightweight formulas with semantic HTML, such as `<sub>`, `<sup>`, Unicode symbols, or a simple centered `.formula` block. Do not add MathJax or another large dependency unless the user explicitly needs complex notation.
- Long formulas and compact vector expressions must wrap across lines at readable delimiters; do not put formulas in horizontal-scroll containers. Use `white-space: pre-wrap`, `overflow-wrap: anywhere`, or explicit line breaks where needed.
- Every figure should have a concise `figcaption` explaining what the reader should notice.

## Timestamp

- Treat the timestamp as report generation metadata, not page-load time.
- Before writing the final HTML, read the system clock and write a literal timestamp such as `时间：2026-10-13 09:48:00 CST` into the title block.
- Do not use JavaScript to replace it on page load, because that would report viewing time rather than generation time.
- Keep the timestamp on the right side of the title metadata row and allow it to wrap or remain readable on small screens.

## Browser Behavior

- Do not add a dedicated PDF export workflow, `@page` rules, page counters, or `@media print` rules unless the user specifically asks for print optimization.
- The browser's native print action should still work with ordinary flow layout.
- Check that all local SVG references resolve, heading anchors are unique, and the HTML remains usable with JavaScript disabled.

## Checklist

- Clean deep-blue technical-document visual language.
- Jumpable table of contents.
- Inline or resolvable SVG diagrams with captions.
- Lightweight readable formulas.
- Literal system-generated timestamp in the header's right side.
- Responsive layout without dashboard-like excess.
- No dedicated PDF export CSS unless explicitly requested.
