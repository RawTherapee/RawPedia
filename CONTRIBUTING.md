# Contributing

## Writing

New pages should be contained within their own folders.
Inside the folder will be an `index.md` file for the content.

If there are translations, they should be of the form `index.LANG.md`
where `LANG` is a two-letter language code (ie: `index.fr.md` for francais, `index.de.md` for german).

The folder can also contain any images that need to be referenced on the page (see `Images` below).

For example, here is the contents of the `/content/file_browser/` directory:

```bash
file_browser
├── filterclear.png
├── index.es.md
├── index.md
├── panel-to-left.png
├── panel-to-right.png
├── rt_setm_fb.jpg
├── rt_setm_fb.png
├── trash-hide-deleted.png
├── trash.png
└── trash-show-full.png
```


### Markdown

#### Images
In general, images _should_ be contained within the same folder as its corresponding `index.md` file.

To link an image in markdown:

```markdown
![Alt Text](image_name.jpg "Optional title text")
```

 - IF the image is part of the page bundle (ie: in the same folder as `index.md`), then the _that_ image will be used.
 - IF the image is NOT part of the page bundle, hugo will look for the image in the `assets/images/` directory (as part of a 'global resource').  If it find the image there, then _that_ image will be used.
 - IF the image is not found in any of those two locations, then no image will be shown and NO ERROR will be reported when building.

While a normal HTML `<img>` tag _could_ be used if needed, please try to avoid them.
Internal logic in Hugo allows multilingual sites to find image links easily.

If you do use the `<img>` tag manually, you will _not_ benefit from the automatic searching for the file and must make sure you have the correct file path in your `src=` paramter.
