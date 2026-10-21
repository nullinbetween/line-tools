# Asset register — line-tools

Last updated: 2026-10-21

## Third-party code

None. All three tools are single HTML files with plain JavaScript. Zip reading and writing, CRC32 and `.docx` text
extraction are this project's own code and use only built-in browser APIs (`TextDecoder`, `DecompressionStream`,
`Intl.Segmenter`, `Blob`, …). No CDN, external library or web font is loaded.

## Data

| # | Material | Used for | Source | Licence | Commercial use | Credit needed |
|---|---|---|---|---|---|---|
| 1 | `examples/*.txt` sample chats | trying the tools, tests | written for this project (fictional; speakers are “Demo User A/B”) | MIT (this project) | ✅ | no\* |

\* No credit line is needed to use these, but copies you redistribute must keep this project's MIT copyright and licence notice (`LICENSE`).

This package contains **no real chat history**.

## Fonts

None bundled or loaded. Only system fonts named in CSS `font-family` lists are used.

## Trademarks

| # | Name | Use | Note |
|---|---|---|---|
| 1 | LINE | describes the input format in the docs | trademark of LY Corporation; the README states that this project is not affiliated with it. No logo or icon is used |

## Audit log

| Date | Checked | Result |
|---|---|---|
| 2026-10-21 | external references in the HTML (`src=`, `href=`, `fetch`, `import`) | none apart from the author link in `index.html` |
