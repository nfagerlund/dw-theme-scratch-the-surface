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
    1. Create a new "style-specific" layer.
        - Type: "theme"
        - Style: "Tabula Rasa"
    2. Find the new layer in the list and click "edit".
    3. Paste in the content from scratch.s2; save and compile.
    4. Leave it open in a tab, in case you want to iterate on it.
2. From [Advanced Customization](https://www.dreamwidth.org/customize/advanced/), go to "Your Styles".
    1. Create a new style with an identifying name. (This won't end up displayed anywhere.)
    2. Click its "edit" button.
    3. Make sure it's set to core2.
    4. Switch the "layout layer" to "Tabula Rasa".
        * By the way, you might need to click the "change" buttons on each of these steps before it'll reveal the form fields for the next step.
    5. Switch the "theme layer" to the layer you recently created. The name of that layer is taken from the actual S2 code that you pasted in and compiled, so in this case it'll say "Scratch the Surface".
    6. Save changes.
3. Go back to "Your Styles".
    1. To preview your journal in a style without changing what other people see yet, click on the link made of numbers next to the style's name. You can edit the theme layer source and refresh as you iterate on it.
        * This all works via an extra URL parameter, which btw you can add to just about any page.
    2. To switch styles publicly, click "Use".
4. Eventually you might want to iterate on your style further, in ways that might temporarily break the layout. Best way to do that:
    1. Do this entire process again, creating a new layer and style.
        * Name the style `<SOMETHING>/staging` or something, so you can tell it apart.
        * For the layer, well, they're gonna have the same name unless you change it in the S2 source code, but the ID number should be larger for the staging version since you created it later, so you can use that to tell them apart. Also, in the "Your Layers" view, any currently in-use layers (which should include your "prod" theme version) are highlighted in the table.
    2. Use the staging style's number link to preview it while you iterate, and have a tab open nearby showing your "real" style so you can compare.

