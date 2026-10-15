# PowerPoint Not Fullscreen

A Quarto RevealJS format for the most familiar video-call presentation experience: PowerPoint's editing window, ribbon, thumbnails, notes pane and all.

The slides still behave like a normal RevealJS deck. Arrow-key navigation works, the thumbnail selection follows the current slide, and clicking a thumbnail changes slides. The tiny slide-show icon in the status bar even does what the presenter should have done in the first place.

Thumbnail generation and the interactive shell are implemented by a small JavaScript controller injected by the format. Selecting the custom format loads it automatically; users do not need any additional settings.

## Install

Once this repository is on GitHub, install it into a Quarto project with:

```bash
quarto add YOUR-GITHUB-USERNAME/quarto-powerpoint-not-fullscreen
```

For local development, copy the `_extensions/powerpoint-not-fullscreen` directory into your project's `_extensions` directory.

## Use

Select the extension format in your presentation front matter:

```yaml
---
title: "Quarterly Synergy Update"
author: "Your name"
format: powerpoint-not-fullscreen-revealjs
---
```

Then write ordinary RevealJS slides:

```markdown
## First slide {data-short-title="A shorter thumbnail label"}

Your content here.

## Next slide

More content.
```

Render or preview as usual:

```bash
quarto preview presentation.qmd
```

The fake PowerPoint filename is taken from the document title. Thumbnail labels come from each slide heading, or from an optional `data-short-title` attribute.

## Customise

Add a CSS file after the extension theme to replace the small organisation mark on each slide:

```scss
.reveal .slides section::after {
  content: "ACME RESEARCH";
}
```

You can also override `--ppt-red` and `--ppt-dark-red` to alter the fake PowerPoint chrome.

## Develop

This repository is itself a runnable example. It requires R and `ggplot2`
because the example charts are generated from visible R code:

```bash
quarto render index.qmd
```

The example renders the themed deck to `quarterly-update.html` and an
unmodified RevealJS comparison to `index.html`, both alongside `index.qmd`.
No `_quarto.yml` project file is required.

The controller source is in
`_extensions/powerpoint-not-fullscreen/powerpoint-ui.html`.
