---
title: Contributing
contributors:
  - DrSlony
tags:
  - 'RawPedia Contributing'
---

- Only RawTherapee developers or experienced users who have good
  communication with a developer will be given access to edit RawPedia.
- If it's not revelatory, it's probably not worth writing. The longer a
  page rambles on, the fewer people will read it, or translate it.
- Avoid unnecessarily frequent article edits. Use the "Show Preview"
  button while writing or translating, then save once it's finished.
- RawPedia uses MediaWiki, which uses markup. Use markup. Do not use
  HTML/CSS unless absolutely necessary, i.e. to un-break things.
  - <https://www.mediawiki.org/wiki/Help:Formatting>
  - <https://www.mediawiki.org/wiki/Help:Images>
- Regarding markup, accomplish what you want to achieve with the minimal
  code required to do so, i.e. don't include unnecessary elements.
- Sooner or later RawPedia will be migrated to some new platform. If you
  use correct markup and keep good structure, the migration will go
  smoothly. If not, it won't go smoothly or at all.
- Information structure is of prime importance. Use section levels and
  sub-levels to organize a page. Use lists where lists should be used.
  Pay special attention that list sub-items appear as children of the
  correct list item.
- If things don't look perfect, don't try to fix them by sacrificing
  information structure or through use of hacks or whitespace. How
  things look depends on several factors: the MediaWiki theme,
  configuration and version. If you've used the right structure and
  markup but things don't look perfect, leave them alone. The problem is
  likely on the server side and it might fix itself in an update, or
  when we edit the CSS file, or when we use a different theme. Trying to
  fix presentation problems through clever markup or HTML only compounds
  the problem.
- Keep one empty line above and below all headings and files, as this
  makes editing documentation easier. e.g.

`Lorem ipsum.`

`==Foo Bar==`

`Dolor sit amet. Consectetur adipiscing elit.`

[`1`](File:foo.png)

`Duis vestibulum sodales est, eu placerat nulla vulputate a.`

- The first time you use an abbreviation on a page, use the full form of
  that abbreviation and include the abbreviation in brackets, e.g.
  "Color Appearance Model (CAM)". You can subsequently use just "CAM".
- Write "RawTherapee" instead of "RT" or "Rawtherapee". Never abbreviate
  "RawTherapee".
- American English is used in both RawTherapee and RawPedia.
- Refer to user interface elements (tool names, frame titles, slider
  names, etc.) using the capitalization used in RawTherapee. That is,
  all tool names and frame titles use title case, while all other
  elements use sentence case. Surround these other user interface
  element names in double-quotes. e.g. There is no need to surround
  "Dynamic Range Compression" in quotes, since every word is capitalized
  and it's clear that this is the name of the tool, while "Restrict LC
  to red and skin-tones" should be quoted so that it is clear in a
  sentence where the name of this checkbox ends and the rest of the
  sentence resumes.
- Only upload work that is either in the public domain, or licensed
  under CC-BY-SA. Specify the licence during upload in the "Licensing"
  drop-down, and in the "Summary" field specify the copyright holder and
  a source (link) to where said owner declared that the work is either
  in the public domain or licensed under CC-BY-SA.
- Avoid JPEG uploads unless necessary. Prefer PNG. Icons or screenshots
  of GUI elements which don't include photos should use PNG. Valid use
  of JPEG is e.g. a photo, or a screenshot of the GUI which includes a
  photo, as this would compress poorly in PNG.
- When uploading icons, use the original filename, and generate a PNG
  for a light background from SVG using:

` ./tools/generatePngIcons rtdata/images/svg/gamut-plus.svg`


Use the PNG icon from the folder named "dark".

- Screenshots should show the relevant part and skip the rest.
- If showing a subtle effect, such as the impact of noise reduction or
  microcontrast, consider scaling the image up by 400%, otherwise only
  people who view the article on a large screen will see the effect, and
  those who print RawPedia, read it via PDF or view it on a device which
  does not allow scaling will not.
- Don't use fancy characters such as „ ‟ « » in the English pages. Use
  plain quotation marks: "foo".
- In most cases, elements in a list should be written using sentence
  case: first character capitalized, period at the end.
- Avoid mentioning keyboard shortcuts on any page other than the
  dedicated Keyboard Shortcuts page. This avoids obsolete info floating
  in multiple places when shortcuts change.
