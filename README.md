# isumanth.com

My personal site. Plain HTML, no build step, no framework. Served by GitHub Pages
from `main`, root directory. The domain is set in `CNAME`.

## Files

```
index.html                        home page
404.html                          not-found page
og.png                            social preview card, 1200x630
robots.txt, sitemap.xml           crawler stuff
writings/<slug>/index.html        one folder per essay
tools/deal-slip/                  internal margin calculator, noindex
```

Each page is self-contained: its own CSS in a `<style>` block, its own script at
the bottom. The writing pages copy the home page's colour variables, so if I
change a colour I change it in every file.

## Editing

**Hero**: the `<h1>` and the `.hero-sub` line, near the top of the body. The words
that cycle after "I" live in the `words` array in the script.

**Writing**: copy an existing `<a class="w-card">` block and change the href,
title, summary, date and source. `w-kind` is the label in the corner: Essay,
Column or Note. Newest goes first. Add the URL to `sitemap.xml` too.

**A new essay**: make `writings/<slug>/index.html`, copy an existing essay page as
the starting point, replace the meta tags at the top (title, description, og,
canonical, JSON-LD) and the article body. Then add a card on the home page and a
line in the sitemap.

**Library**: copy a `<div class="book">` block. `data-review` is the text that
shows when someone clicks the spine. Spine and cover colours are set inline to
roughly match my actual copy of the book.

**Now**: the three `.now-item` spans in the dark band.

**Photos**: the `DECK` array in the script, base64 encoded. Click cycles through them.

## Rules I keep breaking and shouldn't

- No em dashes anywhere a reader can see. Colon, comma, or two sentences.
- The logo is two-tone. At low opacity or in one colour it reads as a dollar sign,
  so no watermarks and no single-colour versions.
- `.reveal.on` sets `transform:none`, which kills any rotation on the element.
  Put `.reveal` on a container, never on a card that is tilted.
- Anything animated needs a `prefers-reduced-motion` escape.

## Deploying

Commit to `main`. Pages rebuilds in about a minute. Check the live URL with a hard
reload, and scroll, because sections stay invisible until the scroll observer fires.
