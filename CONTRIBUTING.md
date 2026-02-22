# Contributing

## Writing

New pages should be contained within their own folders.
Inside the folder will be an `index.md` file for the content.

If there are translations, they should be of the form `index.LANG.md`
where `LANG` is a two-letter language code (ie: `index.fr.md` for francais, `index.de.md` for german).

The folder can also contain any images that need to be referenced on the page (see `Images` below).


### Markdown

#### Images
In general, images _should_ be contained within the same folder as its corresponding `index.md` file.

If it is, then to link an image in markdown:

```markdown
![Alt Text](image_name.jpg "Title text")
```
