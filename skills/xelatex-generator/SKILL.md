---
name: xelatex-generator 
description: Create and edit LaTeX documents compiled with XeLaTeX, including Unicode text, OpenType fonts, page layout, and PDF build verification. Use for XeLaTeX reports, articles, manuals, and other typeset documents; preserve required publisher or institutional templates.
---

# Create XeLaTeX Documents

Produce editable UTF-8 LaTeX sources and, when a compiler is available, a verified PDF. Follow the requested content, language, document type, and visual style.

## Establish the document

Inspect existing `.tex` files, document classes, build configuration, bibliography files, and supplied assets before changing an existing project. Preserve its structure and conventions. For a new document, choose a class and layout appropriate to its purpose; do not impose a report structure on a letter or short article.

Infer sensible defaults when the brief is sufficient. Ask only for missing information that materially affects the result, such as a required submission template. Do not invent citations, measurements, institutional branding, or factual claims to fill gaps; mark necessary missing content clearly.

## Write for XeLaTeX

- Use `fontspec` for Unicode and OpenType fonts. Avoid legacy `inputenc` and `fontenc` configuration in new XeLaTeX sources. Adapt an existing template only as needed for engine compatibility.
- Choose fonts available in the environment, checking with `fc-match` or `fc-list` when available. Verify the actual matched family and coverage for the document's scripts; font substitution is not evidence that the requested font exists. Prefer portable TeX-distributed fonts when no font is specified.
- Set the document language with a compatible `babel` or `polyglossia` configuration. Configure script-specific fonts and directionality when the content requires them.
- Use `unicode-math` only when the document benefits from OpenType mathematics. Select a compatible math font and check conflicts with template packages.
- Keep the preamble focused. Use semantic sectioning, automatic numbering, labels, and cross-references instead of manual numbering or repeated spacing commands.
- Choose consistent page dimensions, margins, heading styles, and typography. Use packages such as `geometry`, `booktabs`, `tabularx`, and `hyperref` where their features are needed and compatible with the class. Respect templates that control these settings.
- Escape LaTeX special characters in prose and imported data. Handle code, URLs, and literal text with suitable commands or environments rather than applying prose escaping to them blindly.
- Use relative paths for assets. Include captions and references where useful; size figures and tables to the available text width. Avoid unreadably small text as a fix for oversized tables.
- Preserve the project's bibliography workflow. For a new cited document, choose one coherent workflow, such as `biblatex` with Biber, and retain enough source metadata to verify references.

## Compile and inspect

Check for the required compiler and build tools. Prefer the existing build command if it supports XeLaTeX. Otherwise, from the document directory, use:

```sh
latexmk -xelatex -interaction=nonstopmode -halt-on-error -file-line-error main.tex
```

Replace `main.tex` with the actual entrypoint. If `latexmk` is unavailable, run `xelatex` with the same diagnostic flags, run the bibliography or index processor when required, and rerun XeLaTeX until references settle. Keep build products in the project's established output location, or a dedicated build directory for a new project.

Do not enable shell escape by default. If a package requires external execution, first consider a compatible alternative; use external execution only within the user's authorization and environment permissions. If dependencies are missing, report the specific tools or packages and install only when authorized.

Fix fatal errors first, then unresolved citations and references, missing glyphs, and consequential overflow warnings. Inspect the final log; the existence of a PDF alone does not demonstrate a successful build. Do not rerun indefinitely: if diagnostics stop changing, investigate the cause or report the blocker.

When PDF rendering tools are available, render representative pages and inspect the images for clipped content, table overflow, awkward page breaks, font problems, and heading consistency. Inspect every page of a short document and all affected layouts in a longer one. Otherwise, state that visual verification was unavailable. After changing the source, rebuild before reporting completion.

## Deliver

Provide links to the source entrypoint and final PDF, with a concise build command and any required companion files. Report remaining limitations accurately, including unavailable compilation or unresolved diagnostics. Keep sources portable and editable; do not deliver only a PDF unless the user requests that.
