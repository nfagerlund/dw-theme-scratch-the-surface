# Cutting Corners / Scratch the Surface

Cutting Corners is a layout style for [Dreamwidth](https://dreamwidth.org), an old-fashioned social blogging platform.

It's a lot like the underlying "Tabula Rasa" style, which most of the default styles are based on. In particular, it sticks to CSS and leaves the default core2 page markup alone (with one minor exception), and it doesn't really mess with the basic configurable float-based layout.

Here's what _is_ different:

- It uses round-cornered cards with solid headers for everything, which IMO gives it a friendly and modern look! 🌻 (You can set `rectangle_radius` to 0 if you want square corners instead.)
- It adds a tiny shortcut menu to the header on mobile. Jump down to your modules (or between your reading/recent pages) without having to scroll forever.
    - Needed improvements: Right now they're emoji, which is kind of janky and non-standard.
- **It avoids busting the layout on mobile at all costs.**

    The thing about Dreamwidth's reading page is, it is basically inevitable that some content you don't control is going to overflow a box somewhere. And in every other layout I've ever seen, that turns into full-page sideways slop, especially on mobile! It's annoying and embarrassing, especially because it should be almost completely avoidable.

    Anyway, here's how this layout tries to keep flist content in its lane:

    - Independent scrolling overflow for each entry/comment/module's content and header. If someone needs to express themselves with a five-minute keyboard smash or a huge `<table>`, you can get the full-fidelity experience without it trashing the rest of the page.
    - Compact comment threading, indicating thread position with dotted lines instead of huge indents.
    - More squish for collapsed comments in very very deep threads. (Visible comments still have a readable minimum width and can force the page to scroll, but the placeholders don't need all that room.)
    - Hack: [Quick-reply on entry pages doesn't blow out the page on mobile.](./cuttingcorners.s2#L1321-L1369) 🙌🏼 (Basically makes it work more like the reading page quick-reply.)
        - (This shouldn't be a style concern, and I'd like to see a fix for it in the site code.)
    - Hack: [Icon browser pop-up isn't completely broken on mobile.](./cuttingcorners.s2#L1370-L1432) 🙌🏼
        - (This shouldn't be a style concern, and I'd like to see a fix for it in the site code.)
    - Images _always_ stay inside their container width, even on desktop. Want a closer look? Rightclick/tap-hold and "view image."
    - Images have a reasonable max-height on desktop, so that portrait-orientation images will mostly fit above the fold in most windows. (Not a concern on mobile, since the max-width kicks in so early.)
    - Metadata lines can break mid-word. (Things like current music, crosspost links, IPv6 address, etc. often have long runs of junk, but are short enough that an emergency linebreak won't hurt readability.)

    Basically, my attitude is that it's fine for extreme situations to result in extreme layouts, but the existing styles treat way too many perfectly normal situations as extreme.


## Stuff

This started as just a theme layer over Tabula Rasa, but eventually I split it into a proper theme/layout division, once I felt like it was doing enough useful stuff that someone else might want to use it.

Files:

- [cuttingcorners.s2](./cuttingcorners.s2) — An S2 "layout" layer for a style called "Cutting Corners." You can style it with your own "theme" layer, which should mostly just set colors and fonts and stuff.
- [scratch.s2](./scratch.s2) — An S2 "theme" layer on top of Cutting Corners. Probably no one should want to use my specific color set (although idk, apparently baby-aspirin orange is Having A Moment!), but it shows you about 70% of the stuff you can tweak for your own style.

## Shortcuts

Relevant links:

- [Advanced Customization](https://www.dreamwidth.org/customize/advanced/) — This is where you can get to your own layers and styles.
- [Public Layers](https://www.dreamwidth.org/customize/advanced/layerbrowse) — View source and info for the built-in stuff.
- [Source: Core2](https://www.dreamwidth.org/customize/advanced/layersource?id=550&fmt=html)
    - [Source: Tabula Rasa](https://www.dreamwidth.org/customize/advanced/layersource?id=551&fmt=html)
        - [Source: Practicality](https://www.dreamwidth.org/customize/advanced/layersource?id=165554&fmt=html)
    - [Source: Transmogrified](https://www.dreamwidth.org/customize/advanced/layersource?id=5927&fmt=html)
- [S2 Language tutorial (on wiki)](http://wiki.dwscoalition.org/wiki/index.php/S2_Guide:_Language_Tutorial) —

I had all that stuff saved locally, but there's no need to check it all into this repo.

Best thing to do when editing is open two duplicate views of your homepage in the target style (and a third in a related style), then start editing the layer source and refreshing ONE of the duplicates. That way you can compare the differences on the fly.

## Installing/etc.

1. From [Advanced Customization](https://www.dreamwidth.org/customize/advanced/), go to "Your Layers".
    1. Create a new "top-level" layer.
        - Type: "layout"
        - Core version: 2
    1. Create a new "style-specific" layer.
        - Type: "theme"
        - Style: The ID number of the layout layer you just added — should be at the bottom, probably won't have a display name yet.
    1. Paste content into both of those new layers:
        1. Find the new layer in the list and click "edit".
        1. Paste in the content from the appropriate s2 file; save and compile.
        1. You can leave it open in a tab if you want to iterate on it.
1. From [Advanced Customization](https://www.dreamwidth.org/customize/advanced/), go to "Your Styles".
    1. Create a new style with an identifying name. (This won't end up displayed anywhere.)
    1. Click its "edit" button.
    1. Make sure it's set to core2.
    1. Switch the "layout layer" to the new layout layer you made.
        * By the way, you might need to click the "change" buttons on each of these steps before it'll reveal the form fields for the next step.
        * The names of these layers in the menus are taken from the actual S2 code that you pasted in and compiled, so in this case it'll say "Cutting Corners".
    1. Switch the "theme layer" to the new theme layer you made.
    1. Save changes.
1. Go back to "Your Styles".
    1. To preview your journal in a style without changing what other people see yet, click on the link made of numbers next to the style's name. You can edit the theme layer source and refresh as you iterate on it.
        * This all works via an extra URL parameter, which btw you can add to just about any page.
    1. To switch styles publicly, click "Use".
1. Eventually you might want to iterate on your style further, in ways that might temporarily break the layout. Best way to do that:
    1. Do this entire process again, creating two new layers and a new style.
        * Name the style `<SOMETHING>/staging` or something, so you can tell it apart.
        * For the layer, well, they're gonna have the same name unless you change it in the S2 source code, but the ID number should be larger for the staging version since you created it later, so you can use that to tell them apart. Also, in the "Your Layers" view, any currently in-use layers (which should include your "prod" theme version) are highlighted in the table.
    1. Use the staging style's number link to preview it while you iterate, and have a tab open nearby showing your "real" style so you can compare.

