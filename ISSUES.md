# Known limitations — line-tools

## Limitations

1. **Date order**: `x/y/YYYY` is always read as day/month/year. In a month/day/year export only lines whose day is above 12
   are recognised as impossible and reported; the others are read as a different date. There is no switch for this.
2. **A date line is a line that is only a date**, optionally followed by a weekday (`(Tue)`, `（二）`, `Tuesday`,
   `星期二`, `火曜日`) — only real weekday names. Anything else after the date (`2024/03/01 day off`,
   `2024/03/01 Monsoon`) makes it a message. But if a message is
   exactly a date on its own line (one line of a multi-line message), it is still treated as a date line.
3. **Days carry over by file-name order**: if the file-name order differs from the time order, the result is wrong.
4. **Years**: only 1990–2100 are accepted.
5. **.docx**: only the text in `word/document.xml` is read — not headers, footers, footnotes or special objects.
6. **zip**: no encryption, no ZIP64, no compression other than deflate; an entry whose CRC does not match is rejected. Names inside a zip are always read as UTF-8
   (old non-UTF-8 Chinese names may look garbled; the content is unaffected). Output zips hold at most 5,000 files.
7. **Memory**: all files are read into memory at once; the 200 MB limit keeps the browser tab from crashing.
8. **Cut points by length** fall between lines whenever a line fits, otherwise on character boundaries. With `Intl.Segmenter` (all current major browsers) a
   user-perceived character such as a flag or a ZWJ emoji sequence is never split; without it, surrogate pairs are still
   kept together.
9. **No anonymisation**: the original workflow paired these tools with a separate anonymiser, which is not part of this
   package. The interface and docs make no anonymisation claims.

## Test coverage

- `tests/core.test.html`: 47 tests, passing in a Chromium-based browser.
- `tests/ui.test.html`: 8 tests, passing in the same browser (including “a new choice still being read blocks the export
  of the previous one”).
- **Safari and Firefox: not tested.** By the API tables, `DecompressionStream('deflate-raw')` needs Safari 16.4+ / Firefox 113+.
- Real LINE exports: **not tested** (only fictional data is used). Export formats may differ between LINE versions and languages.
- Performance with large files (close to the 50 MB / 200 MB limits): **not tested**.
