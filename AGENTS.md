# AGENTS.md

## What this is

A flat static HTML/CSS collection of classroom exercises (《高级网页设计》课堂实践). No framework, no package manager, no build/lint/test tooling exists — do not add or invent commands like `npm install`; there is nothing to run. To verify a change, open the page in a browser (double-click the file, or serve the folder with any static server such as `npx serve`).

All page content is in Chinese.

## Layout

- `index.html` — the entry point. A gallery page linking to every exercise. All styling is inline in its `<style>` block.
- `N-M name.html` — one file per lesson exercise (e.g. `6-1 flex.html`). Each page is self-contained: styles live in an inline `<style>` block, not in shared CSS.
- `css.css` — a shared stylesheet, but it is referenced **only** by `5-1  层叠与继承.html` (note: that filename has two spaces). Do not refactor other pages to use it; it exists to demonstrate external-stylesheet behavior.
- `img/` — shared images (`1.jpg`, `2.jpg`, `3.jpg`, `a1.jpg`–`a3.jpg`).

## Gotchas that will break things

- **Filenames contain spaces and Chinese characters.** `href`s must be URL-encoded exactly as `index.html` already does (`3-1%20form.html`, `5-1%20%20%E5%B1%82...`). When linking to any exercise page, copy the encoding pattern from `index.html`; a raw filename with a space or Chinese character may fail depending on the browser/server.
- **Do not rename or "fix" existing files.** Links in `index.html` encode exact names, including the typo in `9-1 transiton.html` and the double space in `5-1  层叠与继承.html`. Renaming breaks links unless you update every reference.
- **`index.html` card list is hand-maintained.** It currently omits the `10-1`–`10-4` animation exercise pages. When you add a new page, add a matching `<a class="work-card" href="...">` card to `index.html`; nothing auto-generates it.
- **`index.html` must keep the `THE BRIEF` blockquote** in its `prompt-box` section — its own generation prompt requires the page to quote it verbatim ("页面中包括本提示词").
- **`index.html` must stay native code with no CDN** (per that same prompt). Legacy pages may differ — e.g. `1.html` loads Google Fonts — leave them as-is, but all new pages must follow the Coding Rules below (native only, no third-party libs or CDN).

## Conventions

- New pages: `<html lang="zh-CN">`, UTF-8 charset, viewport meta, inline `<style>` for all CSS, no JS frameworks and no external dependencies.
- Lesson-numbered filenames follow `N-M 中文名.html`; pick a name consistent with the existing sequence and URL-encode it when linking.
- Older exercise pages have placeholder `<title>Document</title>` and `lang="en"` — leave them as-is unless the task is to clean them up.

## Coding Rules

- **Author comment required.** Every HTML page must include a comment near the top of `<body>` (or inside `<head>`) in this format: `<!-- 姓名：袁磊，日期：yyyy-mm-dd，功能名称：<该页功能> -->`. Fill in the date and the page's function name; 姓名：袁磊 stays fixed.
- **Native implementation only.** Use plain HTML, CSS, and JavaScript — no frameworks, no third-party libraries, no CDN links of any kind.
- **Icons from local iconfont only.** Icons must come from the `font/` directory (iconfont font icons / `iconfont.js` SVG symbols). Never use icon libraries from npm or CDN.
- **Data fetching via `fetch`.** When a page needs server-side data, use the native `fetch` API (no axios/jQuery or other wrappers).

## Naming Conventions

- All variable names, CSS class names, and ID names must start with `yl_`.
- Existing pages use the older `yuan_` prefix — do not rename them; the `yl_` rule applies to all new code.

## Prompt Logging

- All prompts must be written to `yuan_prompt.md` before execution, in append mode (do not overwrite previous content).
- Each entry must include: timestamp (format: `yyyy-mm-dd-hh-mm`), model used, and the prompt content.
