# RawPedia
RawTherapee Documentation

## Dependencies

To build RawPedia, you'll need the following software:

- `hugo`, the extended version, a recent release
- `git`
- `pnpm` or similar npm package manager

## Getting a local Hugo live preview

1. Clone the repository: `git clone --recurse-submodules https://github.com/RawTherapee/RawPedia.git`
2. Install the npm dependencies: `cd RawPedia/themes/hugo-bootstrap-bare/assets && pnpm install && cd ../../../`
3. Run the hugo server: `hugo server --disableFastRender`
4. Navigate to `http://localhost:1313` in a web browser.

You can now edit the content in the `content` folder and the hugo server will rebuild the content with each change.

## Notes from the mediawiki conversion to hugo

In early 2025, RawPedia moved from medaiwiki to markdown and hugo for it's documentation. The following are some notes from that conversion.

### Find all links in content

This is useful for seeing what links are present in the content

```
cd content/
grep -Eori "\[.*?\]\(.*?\)"
```

### Rename translated files

This is useful for finding all the tranlated files, then rename them to the hugo-comptaible naming convention.

To rename all the Japanese files, orginally named `ja.md`:

`find . -name jp.md -exec rename jp.md index.jp.md '{}' \;`

### Fix markdown links

The script that converted media wiki into markdown files didn't produce working links. The original links looked like `[Link Texst](Link to my Page.md)`.

Running the sed command `sed -Ei 's/\[([^]]+)\]\(([^)]+)\.md\)/[\1](\L\2)/g' **/*.md` finds most of the markdown links, removes the `.md` from the end, converts the link to lowercase, and replaces spaces with underscores.
