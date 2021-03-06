See the [Fabricator 'Materials' documentation](http://fbrctr.github.io/building-a-toolkit/materials.html) for basic guidelines.

Materials have been extended in the following way:

1. By adding "front-matter" data, you can also add code-highlighted CSS to any material. Be aware, there should already be a JavaScript utility running that collects the relevant rules and properties for each material and adds that code to the styles section for each component.

    "Front-matter" `css` data is written in the `f-item-content.html` template with `{{data.css}}`. It is rendered as highlighted code in the `Styles` section of the material. The `css` block needs *some* content in order to render, but this content will automatically be replaced by the generated content. The current standard is to add the comment `<!-- display CSS -->`.

```markup
---
notes: This is a note in `markdown`.
css: <!-- display CSS -->
base: .alert
variations:
  - .alert-primary
  - .alert-secondary
---
```

2. Component Variations can be generated by adding `variations` front-matter.

    Each Variation needs to be set up as above with `variations:` appearing on one line, followed by <code>  - .</code> and your variation class name. If there is a **base class** that is needed to create the variation (as is the case with buttons and alerts), list that class above the variations block. The guide supports multiple base classes, so if you need more than one, separate the classes with commas. If there is no base class data, `(none)` will be generated in the class list (as is the case with **paragraph**s).

3. Generating `reset` buttons on components

    If a component includes a `<script>` block, the component will automatically have a `reset` button generated. Components without `<script>` blocks (even ones that are scripted in the *toolkit script*) won't receive a reset button by default.

    Ideally, all scripts that can be incorporated into the `toolkit.js` file should be included there instead (see [Guide vs Output](#guide-vs-output)).

    To force a reset button to appear, simply add an empty script block (`<script></script>`) to the end of the the component file. If you're forcing the appearance of a reset button in this way, it's recommended that you wrap the `script` block in a `sample` block so that that the script block will be omitted from the component's HTML documentation.
