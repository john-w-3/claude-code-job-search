# Exporting your resume to a clean, single-page PDF

Job sites want a PDF. This guide turns your `resume.html` into a crisp, one-page
PDF that looks the same everywhere. It covers Mac and Windows, because they
behave differently, and Windows is the fussy one.

## Why HTML to PDF at all

You could write a resume in a word processor, but HTML gives you exact, pixel
level control over layout, and it prints identically on any machine. The catch is
that "print to PDF" has a few settings that, if wrong, give you two pages, ugly
margins, or a URL and date stamped across the top. This guide gets them right.

## The part that lives in the file (already done for you)

Open `resume.html` and look near the top of the `<style>` block. Two rules do the
single-page work:

```css
@page { size: letter; }                 /* US Letter paper */
@media print { body { zoom: 0.69; } }   /* shrink to fit one page */
```

If your resume spills onto a second page, lower that `zoom` value a little (try
`0.66`, then `0.62`) and re-export until it fits on one. If you have lots of
empty space at the bottom, you can nudge it up. That single number is your main
"make it fit" dial. (Outside the US, change `letter` to `A4`.)

---

## Mac

### Safari (this is the clean one)

1. Open `resume.html` in Safari (double-click the file, or drag it onto Safari).
2. **File > Export as PDF...**
3. Save.

That is it. This reliably produced a single-page PDF for me with no fiddling.
Safari's "Export as PDF" respects the page styling in the file, so the `@page`
and `zoom` rules above just work.

### Chrome on Mac (if you prefer Chrome)

1. Open `resume.html` in Chrome.
2. **File > Print** (or Cmd+P).
3. Destination: **Save as PDF**.
4. Click **More settings** and set:
   - Paper size: **Letter**
   - Margins: **Default** (or **None** if you want it edge to edge)
   - Headers and footers: **off** (this removes the date and URL stamps)
   - Background graphics: **on**
5. **Save**.

---

## Windows (the fussy one)

On Windows I could never quite reproduce the effortless Safari workflow. The
saved file kept coming out different, and it took extra steps. Here is what
actually works, and the one trap to avoid.

### Use Chrome or Edge, and "Save as PDF" (not "Microsoft Print to PDF")

1. Open `resume.html` in **Chrome** or **Edge** (right-click the file > Open with).
2. Press **Ctrl+P** to print.
3. For **Destination** / **Printer**, choose **Save as PDF**.
   - **Do not** choose **Microsoft Print to PDF.** That is the trap. It is a
     system "printer" that routes through Windows page setup, often rasterizes
     the page, ignores some of the styling, and is the reason your file kept
     coming out different. Chrome's and Edge's own "Save as PDF" honors the page
     styling the way Safari does.
4. Click **More settings** and set:
   - Paper size: **Letter**
   - Margins: **Default** (or **None**)
   - Scale: **Default** (leave it; the `zoom` in the file is doing the scaling).
     If it still spills, lower the `zoom` value in `resume.html` rather than
     fighting the Scale box.
   - **Headers and footers: off.** This is what removes the `file://...` URL and
     the date that Windows likes to stamp across the top and bottom.
   - **Background graphics: on.**
5. Click **Save**.

### If it still will not behave

A few fallbacks, roughly in order of effort:

- **Tweak the one dial.** Most "it is two pages" problems are solved by lowering
  `zoom` in `resume.html` (0.69 to 0.66 to 0.62) and re-exporting.
- **Try the other browser.** If Edge is being weird, try Chrome, or vice versa.
  They differ slightly.
- **Let Claude render it for you.** You can ask Claude Code to convert the HTML
  to PDF directly, which sidesteps the browser entirely and gives an identical
  result on any operating system. It can install a small renderer and run it for
  you; just ask "convert resume.html to a single-page PDF." This is the most
  reliable cross-platform path if browser printing keeps fighting you.

---

## Quick checklist before you submit

- One page, no awkward second page with a single stray line
- No URL or date stamped in the margins (headers and footers off)
- Letter size (or A4 outside the US)
- Your name and links are selectable text, not a blurry image (a sign you used a
  real "Save as PDF" and not a rasterizing one)
- Opens correctly on a phone, since that is often where a recruiter first sees it
