---
title: Coding Rawpedia pages
contributors:
  - XavAL
---

What follows are a set of coding rules needed to write Rawpedia pages,
while using the customized Pivot skin. This page is not intended to be
translated, just to help those who write documentation pages.

## Standard MediaWiki coding markup

**To add standard features to the text** (as bold or italic letters),
you will have to code it like this:

- *italic* : `''italic''`
- **bold** : `'''bold'''`
- ***bold and italic*** : `'''''bold and italic'''''`
- RawPedia first level section heading: `==First level==`
- RawPedia second level section heading: `===Second level===`
- RawPedia third level section heading: `====Third level====`
- RawPedia fourth level section heading: `=====Fourth level=====`
- indented text (one tab from the left): `: indented text`
- indented text (two tabs from the left): `:: indented text`

**To add standard lists** you will have to code like this:

    * Start each line with an asterisk (*)
    * to get a bulleted list
    ** More asterisks give deeper
    *** and deeper levels
    * Line breaks <br />don't break levels
    But any other start ends the list

    # Start each line with a number sign (#)
    # to get a numbered list
    ## More number signs give deeper
    ### and deeper levels
    # Line breaks <br />don't break levels
    # So the numbering keeps increasing
    But any other start ends the list
    # And the next number sign starts a new numbered list

to get this results:

<div class="code-result">

- Start each line with an asterisk (\*)
- to get a bulleted list
  - More asterisks give deeper
    - and deeper levels
- Line breaks
  don't break levels

But any other start ends the list

1.  Start each line with a number sign (#)
2.  to get a numbered list
    1.  More number signs give deeper
        1.  and deeper levels
3.  Line breaks
    don't break levels
4.  So the numbering keeps increasing

But any other start ends the list

1.  And the next number sign starts a new numbered list

</div>

**Combine lists** like this:

    # one
    # two
    #* two point one
    #* two point two
    # three
    ## three sub 1
    ##* three sub 1 sub 1
    ## three sub 2

and you will get:

<div class="code-result">

1.  one
2.  two
    - two point one
    - two point two
3.  three
    1.  three sub 1
        - three sub 1 sub 1
    2.  three sub 2

</div>

**To add links**. They can either be internal (referring to a page
inside RawPedia) or external (to a webpage in the Internet):

- internal links:
  - linking to another page inside RawPedia: the code must be surrounded
    by double brackets as in
    `[[Getting_Started|the Getting Started page]]`. The text after the
    pipe `|` will be the text shown in the page. It will look like this:
    [the Getting Started page](getting_started)
  - linking to a section inside another RawPedia page: the code will
    start with the page name, followed by a `#`, all of it surrounded by
    double brackets as in
    `[[Getting_Started#Start_RawTherapee|starting RawTherapee]]`. It
    will look like this: [starting RawTherapee](getting_started#start_rawtherapee)
  - linking to a section inside the current page: you just have to add
    the link to the proper section, starting the code with a `#` and
    surrounded by double brackets as in
    `[[#Standard_MediaWiki_coding_markup|standard MediaWiki markup]]`.
    It will show as: [standard MediaWiki markup](#standard_mediawiki_coding_markup)
- external links: they will be surrounded by single brackets and the
  full url is added straight away, followed by a custom text. This time
  the url and the text shown is separated by just an empty space:
  `[https://en.wikipedia.org/wiki/Links_(web_browser) web links]`. And
  it will show as: [web links](https://en.wikipedia.org/wiki/Links_(web_browser))

## Page titles and subtitles

At the very top of each page you should add this code:

    <div class="pagetitle">Page Title</div>

If you wish to add a subtitle as a companion to your page title, add
this code below the title:

    <div class="headline">Text used as a subtitle</div>

so the top of your page will look as in this page. Just copy/paste both
codes, and edit the page title and subtitle.

## Table of Contents

Even though MediaWiki automatically adds a table of contents (ToC)
whenever there are 3 or more sections in the page, if you want to force
the ToC appearing no matter what, add this code:

    __TOC__

If on the other hand, you don't want a table of contents in your page,
add this code:

    __NOTOC__

According to the MediaWiki documentation, those codes can be added
anywhere in the page code, but it would make more sense if you add them
just below the page title, so anybody looking at the page code will
immediately know what you wish to happen with the ToC.

## Anchors

Each section appearing in the text automatically becomes an
[anchor](https://en.wikipedia.org/wiki/HTML_element#Anchor), but no HTML
anchor tag (<a>) is allowed in MediaWiki.

The workaround to fix a specific point in the page as an anchor is using
an `id` in any allowed tag, such as in
`<div id="this_will_be_an_anchor">`.

From then on you will only have to point to it with a regular link
expression:
`[[pagetolinkto#this_will_be_an_anchor|pagetolinkto#this_will_be_an_anchor]]</div>`.

## Empty lines

No matter what your subconscious mind tells you to do, **do not add
unnecessary empty lines** just for the shake of formatting content: the
appropriate empty space needed between paragraphs, lists, images..., is
handled with CSS rules, and by adding extra empty lines you will most
probably only generate odd behaviours.

## Lists

Lists are written as explained in the first section of this page.

On the other hand, the way the stylesheet is coded you may or may not
add an empty line between the preceding paragraph and the list (it won't
matter if there's an empty line): the css rules will take care of the
correct spacing between each element of the list and between them and
the preceding paragraph.

However, in spite you can code the list with empty lines between the
list elements, it is not advised as that will lead to odd line spacing,
separating the elements too much and losing the impression of a list.

So this code:

    Lorem ipsum dolor sit amet, consetetur sadipscing elitr:
    * At vero eos et accusam et justo duo dolores et ea rebum.
    * Stet clita kasd gubergren, no sea takimata sanctus est.
    *# Duis autem vel eum iriure dolor in hendrerit in vulputate velit esse molestie consequat.
    *# Vel illum dolore eu feugiat nulla facilisis at vero eros et accumsan et iusto odio.
    *# Dignissim qui blandit praesent luptatum zzril delenit augue duis dolore te feugait nulla facilisi.
    *#* Consectetuer adipiscing elit
    *#* Sed diam nonummy nibh euismod tincidunt.
    * Ut laoreet dolore magna aliquam erat volutpat.
    ** Ut wisi enim ad minim veniam.
    ** Quis nostrud exerci tation.

will show as:

<div class="code-result">

**Lorem ipsum dolor sit amet, consetetur sadipscing elitr:**

- **At vero eos et accusam et justo duo dolores et ea rebum.**
- **Stet clita kasd gubergren, no sea takimata sanctus est.**
  1.  **Duis autem vel eum iriure dolor in hendrerit in vulputate velit
      esse molestie consequat.**
  2.  **Vel illum dolore eu feugiat nulla facilisis at vero eros et
      accumsan et iusto odio.**
  3.  **Dignissim qui blandit praesent luptatum zzril delenit augue duis
      dolore te feugait nulla facilisi.**
      - **Consectetuer adipiscing elit**
      - **Sed diam nonummy nibh euismod tincidunt.**
- **Ut laoreet dolore magna aliquam erat volutpat.**
  - **Ut wisi enim ad minim veniam.**
  - **Quis nostrud exerci tation.**

</div>

## Keyboard keys

Whenever you need to name a combination of keyboard keys to be pressed
so something happens, instead of figuring out how to highlight the names
of the keys, you will use a template: `{{k|ctrl}}` to get the image of
the key ( ). The first part `{{k|` is mandatory and is followed by the
description of the desired key. Then you close the template with `}}`.

The most usual keys to be included in the documents are:



Mac option key: `{{k|option key}}`

Mac alternate key: `{{k|alternate key}}`

Mac command key: `{{k|command key}}`

Super or Windows key: `{{k|winkey}}`

Shift key: `{{k|shift key}}`

Ctrl key: `{{k|ctrl key}}`

Ctrl (alternative version): `{{k|ctrl}}`

Up key: `{{k|up key}}`

Up (alternative version): `{{k|up}}`

Down key: `{{k|down key}}`

Down (alternative version): `{{k|down}}`

Left key: `{{k|left key}}`

Left (alternative version): `{{k|left}}`

Right key: `{{k|right key}}`

Right (alternative version): `{{k|right}}`

Home key: `{{k|home key}}`

End key: `{{k|end key}}`

Page up key: `{{k|page up key}}`

Page down key: `{{k|page down key}}`

There are many more, but you most probably won't use any other else than
the ones previously listed. Anyway, if you ever need to put any text
into a key, just write it into the template like this `{{k|My own key}}`
to get

To add a combination of keys write them like this `{{k|ctrl|9}}` , or
like this `{{k|ctrl}} + {{k|9}}`  +

And if you are writing documentation in a language other than English,
you may face the fact that localized keyboards have some keys not
previously shown which you may wish to use. In such cases there are
alternatives:

### German keyboards



Ctrl: `{{k|de ctrl key}}`

Shift: `{{k|de shift key}}`

Insert: `{{k|de insert key}}`

Del: `{{k|de del key}}`

Home: `{{k|de home key}}`

End: `{{k|de end key}}`

PgUp: `{{k|de pageup key}}`

PgDwn: `{{k|de pagedown key}}`

### Spanish keyboards



Ctrl: `{{k|es ctrl key}}`

Shift: `{{k|es shift key}}`

Insert: `{{k|es insert key}}`

Del: `{{k|es del key}}`

Home: `{{k|es home key}}`

End: `{{k|es end key}}`

PgUp: `{{k|es pageup key}}`

PgDwn: `{{k|es pagedown key}}`

### French keyboards



Shift: `{{k|fr shift key}}`

Insert: `{{k|fr insert key}}`

Del: `{{k|fr del key}}`

Home: `{{k|fr home key}}`

End: `{{k|fr end key}}`

PgUp: `{{k|fr pageup key}}`

PgDwn: `{{k|fr pagedown key}}`

### Italian keyboards



Insert: `{{k|it insert key}}`

Del: `{{k|it del key}}`

Home: `{{k|it home key}}`

End: `{{k|it end key}}`

PgUp: `{{k|it pageup key}}`

PgDwn: `{{k|it pagedown key}}`

## Literal text (from terminal or source code)

When you need to add some text that comes from a shell (terminal), from
source code, or from a configuration file, you could either:

- add it inline if there are only a few words in a single line: enclose
  the words between `<code></code>` tags, and you will get
  `an inline excerpt of code`
- add it inside a box when the text is too long or contain multiple
  lines of text. Code it like:

<!-- -->

    <pre class="coding-pre">
    Lorem ipsum dolor sit amet, consectetur adipiscing elit.

    Atqui reperies, inquit, in hoc quidem pertinacem. Quo modo autem philosophus loquitur. Aliter enim nosmet ipsos nosse non possumus.

    Ita credo.

    Conferam tecum, quam cuique verso rem subicias

</pre>


and it will show as

<div class="code-result">

    Lorem ipsum dolor sit amet, consectetur adipiscing elit.

    Atqui reperies, inquit, in hoc quidem pertinacem. Quo modo autem philosophus loquitur. Aliter enim nosmet ipsos nosse non possumus.

    Ita credo.

    Conferam tecum, quam cuique verso rem subicias

</div>

## Images

There are mainly 2 kinds of images: on the one hand we have those small
images that follow text (which are positioned inline), and on the other
there are images that are blocks, with their own meaning, and somehow
isolated from the text.

### Inline images

Here you can consider the size of the images, even though they will
always be relatively small to fit in a sentence: there are images that
can be thought of as individual *letters* (as are icons), as opposed to
images that fit inside a line of text, but are larger.

#### Icons

- You can add icons to a sentence like this:

<div class="code-result-inline">

**Lorem ipsum dolor sit amet,
![<File:profile-filled.png>](profile-filled.png "File:profile-filled.png")
nullam mauris est, pharetra a fringilla vitae.**

</div>


And you will code it like this:

<!-- -->

    Lorem ipsum dolor sit amet, [[File:Profile-filled.png|File:Profile-filled.png]] nullam mauris est, pharetra a fringilla vitae.

- If you also wish to add some text that will show as a tooltip while
  hovering the icon *(hover the icon in the next example)* :

<div class="code-result-inline">

**Pellentesque tempor turpis vel orci. ![Ornare dapibus](preferences.png "Ornare dapibus") sit amet rutrum sapien.**

</div>


You just have to add the tooltip text after a pipe symbol. And the code
will look like:

<!-- -->

    Pellentesque tempor turpis vel orci. [[File:preferences.png|Ornare dapibus]] sit amet rutrum sapien.

- There's a chance that sometimes the image is just too big to look fine
  next to the text surrounding it. In such situations you can set a
  width to shrink appropriately the image:

<div class="code-result-inline">

**Pellentesque tempor turpis vel orci. ![Ornare dapibus](preferences.png "Ornare dapibus") sit amet rutrum sapien.**

</div>


You will add another pipe symbol, and then the desired image width:

<!-- -->

    Pellentesque tempor turpis vel orci. [[File:preferences.png|Ornare dapibus]] sit amet rutrum sapien.


However, bear in mind that more often than not it will be better to
scale down the image in an editor and reupload the smaller image.

#### Images inside tables

The way to code them follows the same principles than with inline
images, in spite that usually they will be larger images.

#### Larger images that lead or end sentences

You will code them the same as inline images, only adding an extra
***class*** option, but it's advisable that you state on which side of
the text it should be placed. Usually they will be placed at the left
side of the text.

When those images are leading a plain paragraph (above it), you will
code them like:

    [[File:wavelet_contrast_shadow.png|class=image-inline-par]]
    <br clear="all">
    Praesent efficitur enim in felis elementum, congue blandit augue hendrerit. Donec bibendum nec nisi eget dapibus. Sed augue augue, porttitor nec volutpat at, porttitor pellentesque tellus. Nulla tempus vestibulum fringilla. Vivamus in orci risus. Donec vel nulla at libero fermentum tincidunt.

To get:

<div class="code-result">

![](240px-wavelet_contrast_shadow.png "240px-wavelet_contrast_shadow.png")
**Praesent efficitur enim in felis elementum, congue blandit augue
hendrerit. Donec bibendum nec nisi eget dapibus. Sed augue augue,
porttitor nec volutpat at, porttitor pellentesque tellus. Nulla tempus
vestibulum fringilla. Vivamus in orci risus. Donec vel nulla at libero
fermentum tincidunt.**

</div>

On the other hand, when placing the image at the end of a list item:

    * In hac habitasse platea dictumst. Praesent quis tellus scelerisque<br/>[[File:wavelet_contrast_shadow.png|class=image-inline-list]]
    <br/>

<div class="code-result">

- **In hac habitasse platea dictumst. Praesent quis tellus
  scelerisque**
  ![](240px-wavelet_contrast_shadow.png "240px-wavelet_contrast_shadow.png")



</div>

In either case don't forget to add the `<br/>` tag in the appropriate
place.

### Framed images

Those are big images, usually shown downscaled, so if you wish to see
them full size, you will have to click them.

They are usually styled with a frame around the image, that also
encompasses the optional image caption.

#### Image styled **as a thumbnail**

This is the default way of coding these images, and will render them
within a frame, 300px wide (plus the width of the border line, plus the
space around the image and inside the frame), and placed to the right.

In this example there are also an image caption and a link that will
lead you to the specified url when you click the image:

<div class="image-sample">

![](600px-wavelet_daubechies20.png "600px-wavelet_daubechies20.png") **Pellentesque
sodales non odio in venenatis. Suspendisse imperdiet laoreet dictum.
Phasellus at tortor vel ante interdum pellentesque non at justo. Nam
luctus, risus quis ullamcorper ultrices, justo justo commodo massa, ut
ultrices ex ante porta metus. Cras vestibulum turpis vel enim
condimentum gravida. Suspendisse potenti. Curabitur euismod nunc
placerat pharetra elementum. Pellentesque sodales non odio in venenatis.
Suspendisse imperdiet laoreet dictum. Phasellus at tortor vel ante
interdum pellentesque non at justo. Nam luctus, risus quis ullamcorper
ultrices, justo justo commodo massa, ut ultrices ex ante porta metus.
Cras vestibulum turpis vel enim condimentum gravida. Suspendisse
potenti. Curabitur euismod nunc placerat pharetra elementum.
Pellentesque sodales non odio in venenatis. Suspendisse imperdiet
laoreet dictum. Phasellus at tortor vel ante interdum pellentesque non
at justo. Nam luctus, risus quis ullamcorper ultrices.**

</div>

It's coded as:

    [[File:Wavelet_daubechies20.png|thumb]]

#### Image styled **as a custom width thumbnail**

It's the same as a standard thumbnail, but with a custom width
***smaller*** than the original image size. If you set a size bigger
than the image, it will render the image at 100%, but no bigger.

This time a left positioning is added, too:

<div class="image-sample">

![](300px-wavelet_contrast_buttons.png "300px-wavelet_contrast_buttons.png") '''Nunc
et semper magna. Fusce vel dolor orci. Suspendisse eget velit
pellentesque turpis sodales pretium at finibus velit. Aenean dolor nibh,
tempus nec sapien eu, rhoncus posuere tortor. Sed scelerisque lacus id
risus convallis euismod. Praesent in ante non purus varius eleifend.
Nulla tempor, arcu suscipit posuere ultricies, diam elit euismod sem,
quis dignissim est arcu id quam. Nullam gravida posuere aliquam. Nunc et
semper magna. Fusce vel dolor orci. Suspendisse eget velit pellentesque
turpis sodales pretium at finibus velit. Aenean dolor nibh, tempus nec
sapien eu, rhoncus posuere tortor. Sed scelerisque lacus id risus
convallis euismod. Praesent in ante non purus varius eleifend. Nulla
tempor, arcu suscipit posuere ultricies, diam elit euismod sem, quis
dignissim est arcu id quam. Nullam gravida posuere aliquam. Nunc et
semper magna. Fusce vel dolor orci. Suspendisse eget velit pellentesque
turpis sodales pretium at finibus velit. Aenean dolor nibh.

</div>

    [[File:wavelet_contrast_buttons.png|thumb]]

#### Image **with a frame (but not a thumbnail)** and it's original size

<div class="image-sample">

![](450px-wavelet_detail_size.png "450px-wavelet_detail_size.png") **Mauris dui
erat, viverra ac magna eu, egestas consequat mi. Integer tristique,
justo quis dignissim vehicula, leo quam tincidunt mi, nec porttitor nunc
augue quis enim. Nunc id sapien ipsum. Fusce diam mauris, placerat eu
arcu vitae, fringilla pulvinar magna. Orci varius natoque penatibus et
magnis dis parturient montes, nascetur ridiculus mus. Nam eget hendrerit
ex. Donec posuere dictum nunc eu placerat. Curabitur sed turpis
vestibulum, euismod purus et, laoreet tellus. Mauris eget ex nisl.
Mauris ultrices consequat felis sit amet euismod. Mauris dui erat,
viverra ac magna eu, egestas consequat mi. Integer tristique, justo quis
dignissim vehicula, leo quam tincidunt mi, nec porttitor nunc augue quis
enim. Nunc id sapien ipsum. Fusce diam mauris, placerat eu arcu vitae,
fringilla pulvinar magna. Orci varius natoque penatibus et magnis dis
parturient montes, nascetur ridiculus mus. Nam eget hendrerit ex.
Curabitur sed turpis vestibulum, euismod purus et, laoreet tellus.
Mauris eget ex nisl. Mauris ultrices consequat felis sit amet euismod.
Mauris dui erat, viverra ac magna eu, egestas consequat mi. Integer
tristique, justo quis dignissim vehicula, leo quam tincidunt mi, nec
porttitor nunc augue quis enim. Nunc id sapien ipsum. Sed diam nonumy
eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam
voluptua. Vel illum dolore eu feugiat nulla facilisis at vero accumsan
et iusto odio dignissim qui blandit. Praesent luptatum zzril delenit
augue duis dolore te feugait nulla facilisi. Nam liber tempor cum soluta
nobis eleifend option congue nihil imperdiet doming id quod. Lorem ipsum
dolor sit amet, consetetur sadipscing elitr. At vero eos et accusam et
justo duo dolores et ea rebum. Stet clita kasd gubergren, no sea
takimata sanctus est Lorem ipsum dolor sit amet. Duis autem vel eum
iriure dolor in hendrerit in vulputate velit esse molestie consequat.
Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Ut wisi enim
ad minim veniam, quis nostrud exerci tation ullamcorper. Nam liber
tempor cum soluta nobis eleifend option congue nihil imperdiet doming
id. Lorem ipsum dolor sit amet, consetetur sadipscing elitr.**

</div>

Take into account that it won't matter if you set a custom width, as it
will always be rendered with its original size:

    [[File:Wavelet_detail_size.png|right]]

#### **Full width images**

*Full width* means that the image will be rendered as wider as possible,
until it fills the available space.

There are two variations of the same concept: images big enough to fill
the whole space, and images that at 100% size won't fill the whole
space.

##### Heroed images

These are images that almost fill the width of the screen (except for
the sidebar). The concept is similar as in *Hero images*, thus the name
*heroed*.

With the next example we are displaying a big image (bigger than the
viewport size), full width, and removing the possibility to click on it
(`link=`) :

![rt_55_trains.png](/images/rt_55_trains.png "rt_55_trains.png")

Please note that you need to add the `none` option to prevent the image
to overflow the screen.

Note also that you have to add the `frame` option to render the frame
around the image. With the option `class=heroed` the image is given its
full width:

    [[[File:Rt_55_trains.png|none]]

##### Centered images

In this case the images won't fill the full width, because they aren't
big enough. But we want them to be prominent, so we use the same
formatting as before, but getting some important side effects:

**Nullam neque purus, tincidunt sit amet commodo nec, imperdiet vel leo.
Integer nec mollis elit, in auctor leo. Proin et neque quis tellus
laoreet faucibus. Suspendisse efficitur ligula velit, eget consequat
ante mollis id.**
![](rt57_histogram_wide_labeled.png "rt57_histogram_wide_labeled.png")
**Praesent sollicitudin bibendum purus, eget viverra lectus luctus
tincidunt. Orci varius natoque penatibus et magnis dis parturient
montes, nascetur ridiculus mus. Etiam justo neque, volutpat ultricies
lacinia ut, blandit eget ex.**

As seen, the image is centered and the text doesn't wrap around the
image: that's because we have set the `none` option.

    [[File:Rt57_histogram_wide_labeled.png|none]]

However, if you forget to set the `none` option, or you set the
`left/right` options, on larger screens the text following the image
will wrap around it, **but on smaller screens the image will overflow
the screen**:

**Vivamus maximus nunc suscipit luctus iaculis. Pellentesque rutrum ante
sit amet leo consectetur imperdiet. Nullam elementum nisl sed volutpat
ultrices.**
![](rt_filmstrip_21_toolbar-visible.jpg "rt_filmstrip_21_toolbar-visible.jpg")
**Vestibulum ante ipsum primis in faucibus orci luctus et ultrices
posuere cubilia Curae; Suspendisse blandit enim eget nulla mattis
accumsan. Mauris ut lobortis massa. In hac habitasse platea dictumst.
Donec condimentum, nulla ut sagittis porttitor, est lacus laoreet mi,
vitae gravida purus dui non odio.**

This is the incorrect code that leads to the previous image:

    ...sed volutpat ultrices.
    [[File:Rt_filmstrip_21_toolbar-visible.jpg|frame]]
    Vestibulum ante ipsum ...

#### Indented Captions

When you want in the caption some text to be indented, you will need to
enclose it in a `<div>` and add the `captions_indent` class.

This will be useful when you add a list inside a caption, as MediaWiki
doesn't create the list nor gives it any special styling when inside a
caption.

So let's say you have an image with different areas that need some
explanation: while the full explanation will be given in the article
text, it would be really useful having a short description of each area
in the caption itself. Thus, you will code: 8- (you will typically use
this to apply some processing profile to all selected files).

    [[File:Rt_setm_fb.png|thumb|1280px|none|RawTherapee in '''Single Editor Tab Mode, Vertical Tabs''', showing:<br/>
    <div class="captions_indent">
    '''1- Main sections:''' File Browser (currently opened), Queue, Editor, Progress Bar, ICC Profile Creator, Help and Preferences.<br/>
    '''2- Panels''' used for navigating to files and folders.<br/>
    '''3- Thumbnails''' of the currently opened folder.<br/>
    '''4- Filters''' to limit the thumbnails shown to only those which match some metadata or state.<br/>
    '''5- Thumbnail zooming and info'''.<br/>
    '''6- Quick image operations'''.<br/>
    '''7- Sub-tabs of the File Browser:''' '''''Filter''''' (currently opened), '''''Inspect''''' (to see a full-sized embedded JPEG preview), '''''Batch Edit''''' (to apply some setting to all selected images) y '''''Fast Export''''' (low quality and bypasses some tools but fast saving - don't use this for typical saving!).<br/>
    '''8- Right-click context menu''' (you will typically use this to apply some processing profile to all selected files)</div>]]

To get:

\[\[<File:Rt_setm_fb.png%7Cthumb%7C1280px%7Cnone%7CRawTherapee> in
**Single Editor Tab Mode, Vertical Tabs**, showing:

<div class="captions_indent">

**1- Main sections:** File Browser (currently opened), Queue, Editor,
Progress Bar, ICC Profile Creator, Help and Preferences.
**2- Panels** used for navigating to files and folders.
**3- Thumbnails** of the currently opened folder.
**4- Filters** to limit the thumbnails shown to only those which match
some metadata or state.
**5- Thumbnail zooming and info**.
**6- Quick image operations**.
**7- Sub-tabs of the File Browser:** ***Filter*** (currently opened),
***Inspect*** (to see a full-sized embedded JPEG preview), ***Batch
Edit*** (to apply some setting to all selected images) y ***Fast
Export*** (low quality and bypasses some tools but fast saving - don't
use this for typical saving!).
**8- Right-click context menu** (you will typically use this to apply
some processing profile to all selected files)

</div>

\]\]

### Framed images within lists

If you wish to place a framed image aligned with the content of a list,
you will need to enclose it inside an extra `div`, or it won't be
aligned with text.

So if you code as usual:

    [[File:wavelet_contrast_buttons.png|thumb]]
    * At vero eos et accusam et justo duo dolores et ea rebum. Sed diam nonummy nibh euismod tincidunt. Quis nostrud exerci tation. Stet clita kasd gubergren, no sea takimata sanctus est. Duis autem vel eum iriure dolor in hendrerit in vulputate velit esse molestie consequat.
    * Vel illum dolore eu feugiat nulla facilisis at vero eros et accumsan et iusto odio. Dignissim qui blandit praesent luptatum zzril delenit augue duis dolore te feugait nulla facilisi. Consectetuer adipiscing elit. Sed diam nonummy nibh euismod tincidunt.
    * Ut laoreet dolore magna aliquam erat volutpat. Ut wisi enim ad minim veniam. Quis nostrud exerci tation.
    * Vel illum dolore eu feugiat nulla facilisis at vero eros et accumsan et iusto odio. Dignissim qui blandit praesent luptatum zzril delenit augue duis dolore te feugait nulla facilisi. Consectetuer adipiscing elit. Sed diam nonummy nibh euismod tincidunt.

You will get an image positioned lower than it should be:

<div class="image-sample">

![300px-wavelet_contrast_buttons.png](/images/300px-wavelet_contrast_buttons.png "300px-wavelet_contrast_buttons.png")

- At vero eos et accusam et justo duo dolores et ea rebum. Sed diam
  nonummy nibh euismod tincidunt. Quis nostrud exerci tation. Stet clita
  kasd gubergren, no sea takimata sanctus est. Duis autem vel eum iriure
  dolor in hendrerit in vulputate velit esse molestie consequat.
- Vel illum dolore eu feugiat nulla facilisis at vero eros et accumsan
  et iusto odio. Dignissim qui blandit praesent luptatum zzril delenit
  augue duis dolore te feugait nulla facilisi. Consectetuer adipiscing
  elit. Sed diam nonummy nibh euismod tincidunt.
- Ut laoreet dolore magna aliquam erat volutpat. Ut wisi enim ad minim
  veniam. Quis nostrud exerci tation.
- Vel illum dolore eu feugiat nulla facilisis at vero eros et accumsan
  et iusto odio. Dignissim qui blandit praesent luptatum zzril delenit
  augue duis dolore te feugait nulla facilisi. Consectetuer adipiscing
  elit. Sed diam nonummy nibh euismod tincidunt.

</div>

And to fix it you have to enclose the image within
`<div class="tlist">...</div>`:

    <div class="tlist">
    [[File:wavelet_contrast_buttons.png|thumb]]
    </div>
    * At vero eos et accusam et justo duo dolores et ea rebum. Sed diam nonummy nibh euismod tincidunt. Quis nostrud exerci tation. Stet clita kasd gubergren, no sea takimata sanctus est. Duis autem vel eum iriure dolor in hendrerit in vulputate velit esse molestie consequat.
    * Vel illum dolore eu feugiat nulla facilisis at vero eros et accumsan et iusto odio. Dignissim qui blandit praesent luptatum zzril delenit augue duis dolore te feugait nulla facilisi. Consectetuer adipiscing elit. Sed diam nonummy nibh euismod tincidunt.
    * Ut laoreet dolore magna aliquam erat volutpat. Ut wisi enim ad minim veniam. Quis nostrud exerci tation.
    * Vel illum dolore eu feugiat nulla facilisis at vero eros et accumsan et iusto odio. Dignissim qui blandit praesent luptatum zzril delenit augue duis dolore te feugait nulla facilisi. Consectetuer adipiscing elit. Sed diam nonummy nibh euismod tincidunt.

<div class="image-sample">
<div class="tlist">

![300px-wavelet_contrast_buttons.png](/images/300px-wavelet_contrast_buttons.png "300px-wavelet_contrast_buttons.png")

</div>

- At vero eos et accusam et justo duo dolores et ea rebum. Sed diam
  nonummy nibh euismod tincidunt. Quis nostrud exerci tation. Stet clita
  kasd gubergren, no sea takimata sanctus est. Duis autem vel eum iriure
  dolor in hendrerit in vulputate velit esse molestie consequat.
- Vel illum dolore eu feugiat nulla facilisis at vero eros et accumsan
  et iusto odio. Dignissim qui blandit praesent luptatum zzril delenit
  augue duis dolore te feugait nulla facilisi. Consectetuer adipiscing
  elit. Sed diam nonummy nibh euismod tincidunt.
- Ut laoreet dolore magna aliquam erat volutpat. Ut wisi enim ad minim
  veniam. Quis nostrud exerci tation.
- Vel illum dolore eu feugiat nulla facilisis at vero eros et accumsan
  et iusto odio. Dignissim qui blandit praesent luptatum zzril delenit
  augue duis dolore te feugait nulla facilisi. Consectetuer adipiscing
  elit. Sed diam nonummy nibh euismod tincidunt.

</div>

Same thing to align the image to the left side of list items. You will
have to enclose the image `<div class="tlist tleft-list">...</div>`. But
**it will only work well with first level list items and indented text**
(`:indented text`):

    * '''WRONG WAY'''. At vero eos et accusam et justo duo dolores et ea rebum. Sed diam nonummy nibh euismod tincidunt. Quis nostrud exerci tation. Stet clita kasd gubergren, no sea takimata sanctus est. Duis autem vel eum iriure dolor in hendrerit in vulputate velit esse molestie consequat.
    * Vel illum dolore eu feugiat nulla facilisis at vero eros et accumsan et iusto odio. Dignissim qui blandit praesent luptatum zzril delenit augue duis dolore te feugait nulla facilisi. Consectetuer adipiscing elit. Sed diam nonummy nibh euismod tincidunt.
    <div class="tlist">
    [[File:wavelet_contrast_buttons.png|thumb]]
    </div>
    * Ut laoreet dolore magna aliquam erat volutpat. Ut wisi enim ad minim veniam. Quis nostrud exerci tation.
    * Vel illum dolore eu feugiat nulla facilisis at vero eros et accumsan et iusto odio. Dignissim qui blandit praesent luptatum zzril delenit augue duis dolore te feugait nulla facilisi. Consectetuer adipiscing elit. Sed diam nonummy nibh euismod tincidunt.
    * Ut laoreet dolore magna aliquam erat volutpat. Ut wisi enim ad minim veniam. Quis nostrud exerci tation.
    * Vel illum dolore eu feugiat nulla facilisis at vero eros et accumsan et iusto odio. Dignissim qui blandit praesent luptatum zzril delenit augue duis dolore te feugait nulla facilisi. Consectetuer adipiscing elit. Sed diam nonummy nibh euismod tincidunt.


    * '''RIGHT WAY'''. At vero eos et accusam et justo duo dolores et ea rebum. Sed diam nonummy nibh euismod tincidunt. Quis nostrud exerci tation. Stet clita kasd gubergren, no sea takimata sanctus est. Duis autem vel eum iriure dolor in hendrerit in vulputate velit esse molestie consequat.
    * Vel illum dolore eu feugiat nulla facilisis at vero eros et accumsan et iusto odio. Dignissim qui blandit praesent luptatum zzril delenit augue duis dolore te feugait nulla facilisi. Consectetuer adipiscing elit. Sed diam nonummy nibh euismod tincidunt.
    <div class="tlist tleft-list">
    [[File:wavelet_contrast_buttons.png|thumb]]
    </div>
    * Ut laoreet dolore magna aliquam erat volutpat. Ut wisi enim ad minim veniam. Quis nostrud exerci tation.
    * Vel illum dolore eu feugiat nulla facilisis at vero eros et accumsan et iusto odio. Dignissim qui blandit praesent luptatum zzril delenit augue duis dolore te feugait nulla facilisi. Consectetuer adipiscing elit. Sed diam nonummy nibh euismod tincidunt.
    * Ut laoreet dolore magna aliquam erat volutpat. Ut wisi enim ad minim veniam. Quis nostrud exerci tation.
    * Vel illum dolore eu feugiat nulla facilisis at vero eros et accumsan et iusto odio. Dignissim qui blandit praesent luptatum zzril delenit augue duis dolore te feugait nulla facilisi. Consectetuer adipiscing elit. Sed diam nonummy nibh euismod tincidunt.

<div class="image-sample">

- **WRONG WAY**. At vero eos et accusam et justo duo dolores et ea
  rebum. Sed diam nonummy nibh euismod tincidunt. Quis nostrud exerci
  tation. Stet clita kasd gubergren, no sea takimata sanctus est. Duis
  autem vel eum iriure dolor in hendrerit in vulputate velit esse
  molestie consequat.
- Vel illum dolore eu feugiat nulla facilisis at vero eros et accumsan
  et iusto odio. Dignissim qui blandit praesent luptatum zzril delenit
  augue duis dolore te feugait nulla facilisi. Consectetuer adipiscing
  elit. Sed diam nonummy nibh euismod tincidunt.

<div class="tlist">

![300px-wavelet_contrast_buttons.png](/images/300px-wavelet_contrast_buttons.png "300px-wavelet_contrast_buttons.png")

</div>

- Ut laoreet dolore magna aliquam erat volutpat. Ut wisi enim ad minim
  veniam. Quis nostrud exerci tation.
- Vel illum dolore eu feugiat nulla facilisis at vero eros et accumsan
  et iusto odio. Dignissim qui blandit praesent luptatum zzril delenit
  augue duis dolore te feugait nulla facilisi. Consectetuer adipiscing
  elit. Sed diam nonummy nibh euismod tincidunt.
- Ut laoreet dolore magna aliquam erat volutpat. Ut wisi enim ad minim
  veniam. Quis nostrud exerci tation.
- Vel illum dolore eu feugiat nulla facilisis at vero eros et accumsan
  et iusto odio. Dignissim qui blandit praesent luptatum zzril delenit
  augue duis dolore te feugait nulla facilisi. Consectetuer adipiscing
  elit. Sed diam nonummy nibh euismod tincidunt.

<!-- -->

- **RIGHT WAY**. At vero eos et accusam et justo duo dolores et ea
  rebum. Sed diam nonummy nibh euismod tincidunt. Quis nostrud exerci
  tation. Stet clita kasd gubergren, no sea takimata sanctus est. Duis
  autem vel eum iriure dolor in hendrerit in vulputate velit esse
  molestie consequat.
- Vel illum dolore eu feugiat nulla facilisis at vero eros et accumsan
  et iusto odio. Dignissim qui blandit praesent luptatum zzril delenit
  augue duis dolore te feugait nulla facilisi. Consectetuer adipiscing
  elit. Sed diam nonummy nibh euismod tincidunt.

<div class="tlist tleft-list">

![300px-wavelet_contrast_buttons.png](/images/300px-wavelet_contrast_buttons.png "300px-wavelet_contrast_buttons.png")

</div>

- Ut laoreet dolore magna aliquam erat volutpat. Ut wisi enim ad minim
  veniam. Quis nostrud exerci tation.
- Vel illum dolore eu feugiat nulla facilisis at vero eros et accumsan
  et iusto odio. Dignissim qui blandit praesent luptatum zzril delenit
  augue duis dolore te feugait nulla facilisi. Consectetuer adipiscing
  elit. Sed diam nonummy nibh euismod tincidunt.
- Ut laoreet dolore magna aliquam erat volutpat. Ut wisi enim ad minim
  veniam. Quis nostrud exerci tation.
- Vel illum dolore eu feugiat nulla facilisis at vero eros et accumsan
  et iusto odio. Dignissim qui blandit praesent luptatum zzril delenit
  augue duis dolore te feugait nulla facilisi. Consectetuer adipiscing
  elit. Sed diam nonummy nibh euismod tincidunt.

</div>

### Animated images

Animated images must be encoded in GIF format.

You can add animated gifs whenever you want like any other image, with
the exception of **not changing the native image of the gif** : due to
some internal Mediawiki problems, it may happen that the resized version
shows up as a static image. If you need a smaller animation, resize it
in Gimp, and then upload the new, smaller version to the server.

When you add an animation as any other image, it will show up in an
endless loop (or in any loop/iterations it was encoded whith).

If you want to show an animation starting as a still image, and showing
the animation itself when interacting with it, follow these steps:

- create an animation and export it in GIF format
- save the first frame as an static image
- encode the animation like this:

<!-- -->

    <div class="thumb tnone">
    <div class="thumbinner" style="width: 310px;">
    [[File:Case3.png|class=animated thumbimage]]
    [[File:Case3.gif|class=animated thumbimage]]
    <div class="thumbcaption">
    An animation of a curve shape change
    </div>
    </div>
    </div>


Where the width should ideally be the same size as the gif animation.
The first item is the static image, and the second item is the
animation.

<div class="thumb tnone">
<div class="thumbinner" style="width: 310px;">

![](case3.png "case3.png") ![](case3.gif "case3.gif")

<div class="thumbcaption">

An animation of a curve shape change

</div>
</div>
</div>

The text «**Mouseover me!**» is hardcoded in the stylesheet, while the
caption shown when you place your pointer over the animation, is written
in the previous code.

There's a catch though, and it can't be overcommed because of the way
browsers deal with gif animations: the first time you place your mouse
over the animation, it starts from the gif starting point, and if you
move the pointer outside the boundaries of the image the animation
stops. However, if you go back over the image, the animation **starts
from the point it was when you stopped the animation**. The only way to
start from the beginning is reloading the page.

**If you want a localized text to be shown instead of *Mouseover me!*,
you will have to add another class:**

- for Spanish pages, add «**tcap-es**» in the caption div:
  `<div class="thumbcaption tcap-es">`, and the text will show as
  «**¡Pasa el ratón!**»
- for French pages, add «**tcap-fr**» in the caption div:
  `<div class="thumbcaption tcap-fr">`, and the text will show as
  «**Survol de la souris!**»
- for Italian pages, add «**tcap-it**» in the caption div:
  `<div class="thumbcaption tcap-it">`, and the text will show as
  «**¡Passare sopra!**»

### Sliding curtain comparison images

When an interactive comparison is needed, you can add a sliding
comparison, where the image on top of the background is shown or hidden
by the curtain slider.

To add such comparison into RawPedia, you have to code it like this:

    <div class="img-comp-wrapper">
    <div class="thumbinner thumbcompare tnone" style="width: 500px">
    <imgcomp img1='Wavelets_residual_SHneg_original.png' img2='Wavelets_residual_SHneg_old.png'  width=500 />
    <div class="thumbcaption">
    '''Left side:''' the image without changes applied


    '''Right side:''' the image with the new processing
    </div>
    </div>
    </div>

Where you have to set:

- the desired width in pixels: it doesn't need to be the exact width of
  the images to be compared, but it is highly advised, as otherwise
  MediaWiki will have to resize them, and may tamper with the real
  differences between the images
- img1: is the image to be shown or hidden by the curtain (the image on
  top of the background)
- img2: is the image to be shown as a background
- in the *thumbcaption* div you may set the appropriate caption
  explaining which image is which in the comparison

Finally, with the example code above you will get this comparison,
centered on screen and without text surrounding it:

<div class="img-comp-wrapper">
<div class="thumbinner thumbcompare tnone" style="width: 500px">

<imgcomp img1='Wavelets_residual_SHneg_original.png' img2='Wavelets_residual_SHneg_old.png'  width=500 />

<div class="thumbcaption">

**Left side:** the image without changes applied

**Right side:** the image with the new processing

</div>
</div>
</div>

If you wish to place the comparison to the left or right of the text,
which will wrap around the comparison, you will need to add an extra
class, either `img-comp-right` to place it at the right side of the
page, or `img-comp-left` to place it at the left side. So the previous
example placed at the right side of the page will be coded as:

    <div class="img-comp-wrapper img-comp-right">
    <div class="thumbinner thumbcompare tnone" style="width: 500px">
    <imgcomp img1='Wavelets_residual_SHneg_original.png' img2='Wavelets_residual_SHneg_old.png'  width=500 />
    <div class="thumbcaption">
    '''Left side:''' the image without changes applied


    '''Right side:''' the image with the new processing
    </div>
    </div>
    </div>

And will show as:

<div class="image-sample">
<div class="img-comp-wrapper img-comp-right">
<div class="thumbinner thumbcompare tnone" style="width: 500px">

<imgcomp img1='Wavelets_residual_SHneg_original.png' img2='Wavelets_residual_SHneg_old.png'  width=500 />

<div class="thumbcaption">

**Left side:** the image without changes applied

**Right side:** the image with the new processing

</div>
</div>
</div>

**Mauris dui erat, viverra ac magna eu, egestas consequat mi. Integer
tristique, justo quis dignissim vehicula, leo quam tincidunt mi, nec
porttitor nunc augue quis enim. Nunc id sapien ipsum. Fusce diam mauris,
placerat eu arcu vitae, fringilla pulvinar magna. Orci varius natoque
penatibus et magnis dis parturient montes, nascetur ridiculus mus. Nam
eget hendrerit ex. Donec posuere dictum nunc eu placerat. Curabitur sed
turpis vestibulum, euismod purus et, laoreet tellus. Mauris eget ex
nisl. Mauris ultrices consequat felis sit amet euismod. Mauris dui erat,
viverra ac magna eu, egestas consequat mi. Integer tristique, justo quis
dignissim vehicula, leo quam tincidunt mi, nec porttitor nunc augue quis
enim. Nunc id sapien ipsum. Fusce diam mauris, placerat eu arcu vitae,
fringilla pulvinar magna. Orci varius natoque penatibus et magnis dis
parturient montes, nascetur ridiculus mus. Nam eget hendrerit ex.
Curabitur sed turpis vestibulum, euismod purus et, laoreet tellus.
Mauris eget ex nisl. Mauris ultrices consequat felis sit amet euismod.
Mauris dui erat, viverra ac magna eu, egestas consequat mi. Integer
tristique, justo quis dignissim vehicula, leo quam tincidunt mi, nec
porttitor nunc augue quis enim. Nunc id sapien ipsum. Sed diam nonumy
eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam
voluptua. Vel illum dolore eu feugiat nulla facilisis at vero accumsan
et iusto odio dignissim qui blandit. Praesent luptatum zzril delenit
augue duis dolore te feugait nulla facilisi. Nam liber tempor cum soluta
nobis eleifend option congue nihil imperdiet doming id quod. Lorem ipsum
dolor sit amet, consetetur sadipscing elitr. At vero eos et accusam et
justo duo dolores et ea rebum. Stet clita kasd gubergren, no sea
takimata sanctus est Lorem ipsum dolor sit amet. Duis autem vel eum
iriure dolor in hendrerit in vulputate velit esse molestie consequat.
Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Ut wisi enim
ad minim veniam, quis nostrud exerci tation ullamcorper. Nam liber
tempor cum soluta nobis eleifend option congue nihil imperdiet doming
id. Lorem ipsum dolor sit amet, consetetur sadipscing elitr.**

</div>

### Galleries

Galleries are mainly lists of images, shown one next to another, but
**it's important to remember that they are NOT coded the MediaWiki
way**.

The stylesheet is ready to let you show 2, 3 or 4 images side by side.
Whenever you need to show more images altogether, consider breaking them
into groups, with each group in one row. Or even use a [workflow
gallery](#Workflow_galleries.md) as explained later in this
section.

To code a gallery you will follow these steps:

1.  enclose every row of the gallery inside a **`<div>`**
2.  start each row of the gallery as an unordered list, and assign to it
    the `leftalign` class
3.  each list element will be assigned a class depending on the number
    of images to show in a row:
    - `RPgallery` is the class to assign when there will be 4 images in
      a row
    - `RP3inarow` will be the choice for 3 images
    - `RPside2side` for 2 images, usually big images to compare them
      with enough detail
4.  include in every list element the images as inline images, with the
    options `thumb`, `left`, the image width, and the caption

#### 4 images in a row

With this example code:

    <div><ul class="leftalign">
    <li class="RPgallery"> [[File:wavelet_pic.png|thumb]] </li>
    <li class="RPgallery"> [[File:wavelet_contrast_15C+_WL.png|thumb]] </li>
    <li class="RPgallery"> [[File:wavelet_contrast_15C+_H3S6.png|thumb]] </li>
    <li class="RPgallery"> [[File:wavelet_contrast_15C+_H3S6_Str50.png|thumb]] </li>
    </ul></div>

the images will render as:

<div>

- ![660px-wavelet_pic.png](/images/660px-wavelet_pic.png "660px-wavelet_pic.png")

- ![660px-wavelet_contrast_15c+_wl.png](/images/660px-wavelet_contrast_15c+_wl.png "660px-wavelet_contrast_15c+_wl.png")

- ![660px-wavelet_contrast_15c+_h3s6.png](/images/660px-wavelet_contrast_15c+_h3s6.png "660px-wavelet_contrast_15c+_h3s6.png")

-
![660px-wavelet_contrast_15c+_h3s6_str50.png](/images/660px-wavelet_contrast_15c+_h3s6_str50.png "660px-wavelet_contrast_15c+_h3s6_str50.png")

</div>

On bigger screens, the images will be shown all in a row, no matter if
the size set as an option is bigger. But when the screen gets smaller,
there will be a breakpoint where those images will be too small, so they
split into a couple of rows, and then the image size set as an option
becomes really important (the image could get four times as big). Thus,
when coding galleries intended for 4 images in a row, it's wise to set
their sizes around 300-400 pixels.

#### 3 images in a row

In this case, with this example code:

    <div><ul class="leftalign">
    <li class="RP3inarow"> [[File:wavelet_chrom_Link_50_Str50.png|thumb]] </li>
    <li class="RP3inarow"> [[File:wavelet_toning_opBYfull.png|thumb]] </li>
    <li class="RP3inarow"> [[File:wavelet_toning_opBYfull_curve.png|thumb]] </li>
    </ul></div>

the images will render as:

<div>

- ![660px-wavelet_chrom_link_50_str50.png](/images/660px-wavelet_chrom_link_50_str50.png "660px-wavelet_chrom_link_50_str50.png")

- ![660px-wavelet_toning_opbyfull.png](/images/660px-wavelet_toning_opbyfull.png "660px-wavelet_toning_opbyfull.png")

- ![280px-wavelet_toning_opbyfull_curve.png](/images/280px-wavelet_toning_opbyfull_curve.png "280px-wavelet_toning_opbyfull_curve.png")

</div>

Notice that not all images must have the same width set.

#### Images compared side to side

Now we have the chance to show a couple of big images, to appreciate the
differences between them.

If we code like this:

    <div><ul class="leftalign">
    <li class="RPside2side"> [[File:wavelet_smc_original.png|thumb]] </li>
    <li class="RPside2side"> [[File:wavelet_clarity_ML60MC30.png|thumb]] </li>
    </ul></div>

Will get:

<div>

- [900px-wavelet_smc_original.png](/images/900px-wavelet_smc_original.png "900px-wavelet_smc_original.png")

- ![20200623062937!wavelet_clarity_ml60mc30.png](/images/20200623062937!wavelet_clarity_ml60mc30.png "20200623062937!wavelet_clarity_ml60mc30.png")

</div>

And the images will remain side to side until you look at them in a
really small screen.

Essentially the `RPside2side` class is meant to keep the images side to
side, to reinforce the idea of a comparison.

## Formulae

MediaWiki doesn't have a native way to nicely and correctly render a
formula. There are extensions to accomplish this, but in RawPedia you
will just use images.

There are a couple classes to add to such images, though: one class for
the image, and another for the caption (where you explain the meanings
of the different components of the formula). So you add the class
`formulae` to the image, and the class `formulae-caption` to the
paragraph (`<p>...</p>`) that will enclose the caption. Like this:

    [[File:gamma_formula.png|class=formulae|none|thumb|
    <p class="formulae-caption"><big>'''V<small>out</small>'''</big> is the output value<br/>
    <big>'''A'''</big> and <big>'''B'''</big> are constants<br/>
    <big>'''V<small>in</small>'''</big> is the input value<br/>
    <big><big>'''γ'''</big></big> is the gamma value</p>]]

And it will look like:

\[\[<File:gamma_formula.png%7Cclass=formulae%7Cnone%7Cthumb>\|

<big>**V<small>out</small>**</big> is the output value
<big>**A**</big> and <big>**B**</big> are constants
<big>**V<small>in</small>**</big> is the input value
<big><big>**γ**</big></big> is the gamma value

\]\]

## Workflow pages

Whenever you need to create workflow tutorials to show how to work with
a tool, you will need to create 2 pages:

- the first one will be the index page, and it will usually be located
  in the main index page of the website (the index in your language)
- the second will be the tutorial, where you explain step by step how to
  process an image

In the **index page**, the gallery will be coded as:

    <gallery mode="packed-hover" heights=220px>
    File:20190820_Südpark_Blüten_8112_B.jpg|''Macro shot''|link=macro_shot
    File:2009-04-04 at 12-30-44.jpg|''Landscape''|link=landscape
    File:D700_20090529_9255.jpg|''Wildlife''|link=wildlife
    File:DSCF2716.jpg|''Industrial''|link=industrial
    File:20180429194518_Turkey.jpg|''Architecture''|link=architecture
    File:DSCF9442.jpg|''Still life''|link=still_life
    </gallery>

To note:

- the selected heights: as you will be able to set the size you wish,
  but it's wiser that they are in the range of 200-350px
- the links: they must match the name of an existing page
- and how it will show as an automatically arranged group of thumbnails:
  this is automatically done by MediaWiki, and sometimes there will be
  some odd sizes or arrangements

The previous code is rendered as:

<div class="code-result">

<File:20190820_Südpark_Blüten_8112_B.jpg>\|*Macro shot*\|link=macro_shot
<File:2009-04-04> at 12-30-44.jpg\|*Landscape*\|link=landscape
<File:D700_20090529_9255.jpg>\|*Wildlife*\|link=wildlife
<File:DSCF2716.jpg>\|*Industrial*\|link=industrial
<File:20180429194518_Turkey.jpg>\|*Architecture*\|link=architecture
<File:DSCF9442.jpg>\|*Still life*\|link=still_life

</div>

In the **workflow page**, the points will be coded as:

    <div class="workflow-list">
    Lorem ipsum dolor sit amet, consetetur sadipscing elitr:
    # At vero eos et accusam et justo duo dolores et ea rebum.
    # Stet clita kasd gubergren, no sea takimata sanctus est.
    #* Duis autem vel eum iriure dolor in hendrerit in vulputate velit esse molestie consequat.
    #* Vel illum dolore eu feugiat nulla facilisis at vero eros et accumsan et iusto odio.
    #* Dignissim qui blandit praesent luptatum zzril delenit augue duis dolore te feugait nulla facilisi.
    #** Consectetuer adipiscing el
    #** Sed diam nonummy nibh euismod tincidunt.
    # Ut laoreet dolore magna aliquam erat volutpat.
    #* Ut wisi enim ad minim veniam.'''
    </div>

and they will be shown as:

<div class="workflow-list">

Lorem ipsum dolor sit amet, consetetur sadipscing elitr:

1.  At vero eos et accusam et justo duo dolores et ea rebum.
2.  Stet clita kasd gubergren, no sea takimata sanctus est.
    - Duis autem vel eum iriure dolor in hendrerit in vulputate velit
      esse molestie consequat.
    - Vel illum dolore eu feugiat nulla facilisis at vero eros et
      accumsan et iusto odio.
    - Dignissim qui blandit praesent luptatum zzril delenit augue duis
      dolore te feugait nulla facilisi.
      - Consectetuer adipiscing el
      - Sed diam nonummy nibh euismod tincidunt.
3.  Ut laoreet dolore magna aliquam erat volutpat.
    - Ut wisi enim ad minim veniam.'''

</div>

## Responsive tables

Tables in RawPedia are created *[the MediaWiki
way](https://www.mediawiki.org/wiki/Help:Tables)*, but with some
additions.

Let's not forget that MediaWiki is famous for its non-responsive skins,
and tables are specially difficult to deal with when making them
responsive.

One way to get a better solution to standard MediaWiki tables is to
allow them to be scrolled horizontally on smaller screens. It's by far
the least ideal solution, but is better than standard tables. In this
customized skin there's a way to get that behaviour: setting the class
**RPwt-table**. That is, starting the table as:

`{| class="RPwt-table"`

and then you could add as many columns as you need.

On the other hand, this skin has a way to show really responsive tables
but it's not straightforward, so let's see how to code them by means of
a step by step example. Essentially it all boils down to define a table
structure, then add *metadata* to every and each cell, and enclose
everything in a wrapper `div`:

- **open a `div`** setting the style `grid-table-wrapper`


`<div class="grid-table-wrapper">`

- **defining the table structure**: you don't need to tell MediaWiki how
  many columns the table will have. But there's a hardcoded limit on 6
  columns. There are no rules for tables with 7 columns and up, but it
  shouldn’t be too difficult to add if needed, although the columns
  would be too narrow


`{| class="RP6c-grid"`

- **table title**: you just need to point to the **tablegrid-caption**
  class. No `colspan` needed anymore


`! class="tablegrid-caption" | Magna aliquyam erat, sed diam voluptua.`

<!-- -->


**HOWEVER**, if you are creating tables with just 2-3 narrow columns,
double check that this caption is not too long, or it will stretch the
table boundaries, making it look incorrectly

- **column headers**: every table should have table headers, where you
  declare what kind of data lies in that column cells, so the first
  group of cells (the first row of cells) will all be column headers,
  and that should be coded like this:


`! role="columnheader"`

<!-- -->


The **role** is mostly for semantic purposes, but it’s also needed for
styling purposes (it **must** be present)

- **attributes of cells** (*metadata* ): now comes the tricky and
  tedious part, because to make the table responsive you have to
  manually add the appropriate attribute to each cell.


Let’s take a look at how the first column header has to be coded:

<!-- -->


`data-colh1="Ipsum" | Ipsum`

<!-- -->


The **data-colh1** part is an attribute that has to be set to **every**
cell that will be a part of that column. *data-colh2* would be present
in every cell that is part of the second column, and so on.

<!-- -->


**NOTE: The contents of the attribute must be the same text as the
header text**.

::\* **full code for the first column header**:



`! role="columnheader" data-colh1="Ipsum" | Ipsum`

::\* **full code for the first 3 column headers**:

    ! role="columnheader" data-colh1="Ipsum" | Ipsum
    ! role="columnheader" data-colh2="Hendrerit" | Hendrerit
    ! role="columnheader" data-colh3="Adipiscing" | Adipiscing

::\* **what if you want row headers too?** Then you have to add a new
empty column header at the beginning (we will see how to set the row
headers below):

    ! role="columnheader" |
    ! role="columnheader" data-colh1="Ipsum" | Ipsum
    ! role="columnheader" data-colh2="Hendrerit" | Hendrerit
    ! role="columnheader" data-colh3="Adipiscing" | Adipiscing



Note that there’s a new *first column* , but you don’t take it into
account when setting the column attributes (that’s odd, but it has to be
that way in case you don’t need row headers, so the stylesheet is the
same for both kind of tables). Don’t miss the fact that in tables
without row headers you will have up to 6 columns of comparison data,
while in tables with row headers you will only have up to 5 columns of
comparison data, plus an extra column of row headers

::\* **how to add row headers, then?** The first cell in a row will be
the *row header* , and will be coded as:



`! role="rowheader"| Lorem ipsum dolor sit amet, consetetur sadipscing elitr.`

<!-- -->



Don’t forget the exclamation mark (`!`) at the beginning

- **now the data to be compared in the table**: when adding the cells
  with the data you will have to set the appropriate attribute for the
  column it will be in:

<!-- -->

    ! role="rowheader"| Lorem ipsum dolor sit amet, consetetur sadipscing elitr.
    | data-colh1="Ipsum" | At vero eos et accusam et justo duo dolores et ea rebum.
    | data-colh2="Hendrerit" | Stet clita kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor sit amet.
    | data-colh3="Adipiscing" | Duis autem vel eum iriure dolor in hendrerit in vulputate velit esse molestie consequat.


I have added the row header for completeness, and for you to see which
one is the *first column* , according to the stylesheet. If you were to
create a 3 columns table without row headers, the full row will be coded
as this:

<!-- -->

    | data-colh1="Ipsum" | At vero eos et accusam et justo duo dolores et ea rebum.
    | data-colh2="Hendrerit" | Stet clita kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor sit amet.
    | data-colh3="Adipiscing" | Duis autem vel eum iriure dolor in hendrerit in vulputate velit esse molestie consequat.


That is, no row header cell, and everything else the same

- **finally close the `div`**


`</div>`

- **the final code**: after you had coded all the cells in every row of
  the table, it will look similar to this:

<!-- -->

    <div class="grid-table-wrapper">
    {| class="RP6c-grid"
    ! class="tablegrid-caption" | Magna aliquyam erat, sed diam voluptua.
    |-
    ! role="columnheader" |
    ! role="columnheader" data-colh1="Ipsum" | Ipsum
    ! role="columnheader" data-colh2="Hendrerit" | Hendrerit
    ! role="columnheader" data-colh3="Adipiscing" | Adipiscing
    ! role="columnheader" data-colh4="Consequat" | Consequat
    ! role="columnheader" data-colh5="Consectetuer" | Consectetuer
    |-
    ! role="rowheader"| Lorem ipsum dolor sit amet, consetetur sadipscing elitr.
    | data-colh1="Ipsum" | At vero eos et accusam et justo duo dolores et ea rebum.
    | data-colh2="Hendrerit" | Stet clita kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor sit amet.
    | data-colh3="Adipiscing" | Duis autem vel eum iriure dolor in hendrerit in vulputate velit esse molestie consequat.
    | data-colh4="Consequat" | Lorem ipsum dolor sit amet, consectetuer adipiscing elit.
    | data-colh5="Consectetuer" | Ut wisi enim ad minim veniam, quis nostrud exerci tation ullamcorper suscipit.
    |-
    ! role="rowheader"| Sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua.
    | data-colh1="Ipsum" | Vel illum dolore eu feugiat nulla facilisis at vero accumsan et iusto odio dignissim qui blandit.
    | data-colh2="Hendrerit" | Praesent luptatum zzril delenit augue duis dolore te feugait nulla facilisi.
    | data-colh3="Adipiscing" | Nam liber tempor cum soluta nobis eleifend option congue nihil imperdiet doming id quod.
    | data-colh4="Consequat" | Lorem ipsum dolor sit amet, consetetur sadipscing elitr.
    | data-colh5="Consectetuer" | At vero eos et accusam et justo duo dolores et ea rebum.
    |-
    ! role="rowheader"| Stet clita kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor sit amet.
    | data-colh1="Ipsum" | Duis autem vel eum iriure dolor in hendrerit in vulputate velit esse molestie consequat.
    | data-colh2="Hendrerit" | Lorem ipsum dolor sit amet, consectetuer adipiscing elit.
    | data-colh3="Adipiscing" | Ut wisi enim ad minim veniam, quis nostrud exerci tation ullamcorper.
    | data-colh4="Consequat" | Nam liber tempor cum soluta nobis eleifend option congue nihil imperdiet doming id.
    | data-colh5="Consectetuer" | Lorem ipsum dolor sit amet, consetetur sadipscing elitr.
    |}
    </div>


**Don’t miss the fact that in this example we have defined a 6 columns
table, but only 5 columns will be used for actual data, because we have
used an extra column for row headers**

<!-- -->


And this is how it will look:

<div class="grid-table-wrapper">

| Magna aliquyam erat, sed diam voluptua.                                                            |
|----------------------------------------------------------------------------------------------------|
|                                                                                                    |
| Lorem ipsum dolor sit amet, consetetur sadipscing elitr.                                           |
| Sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua. |
| Stet clita kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor sit amet.                 |

</div>

The column headers visible on large screens become small flags on medium
to smaller displays, and that transformation happens because of the cell
attributes added. That’s why those attributes must have the same text as
the column header. **BUT, if some column header text is too long, it
will be clipped in the flag, so in such case you may wish to change the
cell attribute text, to fit the flag size**.

## Sidebar links

Those are the links with an icon shown on the left side of the screen,
either always shown or after clicking the top left *hamburguer*. It goes
without saying that the procedure to create or edit them needs that you
have special (high) privileges in the server.

The procedure is a bit convoluted, so let's take it one step at a time.

### Creating the links

1.  the MediaWiki Sidebar has to be edited, so search for
    «MediaWiki:Sidebar» and follow the link
2.  edit the existing list adding the target and the text to be shown on
    the appropriate group (section)
3.  save the Sidebar page and force a reload of the website
4.  open the Developer Tools of your browser (press F12)
5.  look for the `li id="` value of your newly added link and copy the
    *id*
6.  create a new rule in the stylesheet:
    - it has to start with `#` then paste the copied *id* (it will look
      like `#n-xxxxxxx`)
    - follow it with `a:before {content: “\fXXX”;}`, where *XXX* is the
      unicode number of the fontawesome icon to be used (it has to be
      one of the [v.4.7
      icons](https://fontawesome.com/v4.7.0/cheatsheet/))
    - if the id has a reserved character (typically a dot `.`), you
      **WILL HAVE to escape it**, so `Eek.21` becomes `Eek\.21` in the
      css rule
7.  save the stylesheet and force reload the browser.

### Creating the tooltips

If you also wish to create or edit a tooltip for the links, follow this
steps:

1.  browse this page on the wiki: `index.php/MediaWiki:Sidebar`
2.  copy the `li id="` value of the link that’s gona receive the tooltip
3.  browse this page: `index.php/MediaWiki:Tooltip-xxxxxxxxxxxxx`, where
    *xxxxxxxxxxxxx* is the copied *id* (you have to paste the id as it
    is, without escaping any character)
4.  edit the page (or most probably, create it) and add the desired
    tooltip text: the way it looks in the editor is how it will look in
    the tooltip, so if you force new lines, the tooltip will look as it
    shown in the editor
5.  save the page and you will already have the tooltip working

And now a warning: **if the text shown in a link changes, the stylesheet
has to be edited or the corresponding icon won’t show up, and the
tooltip page has to be created again with the new id (the page with the
old text will become useless)**.

On the other hand, the text shown in the tooltips can be freely changed
by just editing the appropriate page (`MediaWiki:Tooltip-n-xxxxxxx`)
