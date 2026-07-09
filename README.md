# Bifocal

Light/dark mode for *audience*. One page carries a plain-reader and a technical version of its copy in the same DOM; a tiny switcher toggles between them, like a theme.

[bifocal.dev](https://bifocal.dev) is built with bifocal. Flip the Plain/Technical switch and the page rewrites itself for the other reader.

## Why

Most tech-forward sites serve two readers and fail one of them. Write it simply and engineers think it's fluff; write it precisely and everyone else bounces. Bifocal lets you ship both versions and let the reader pick, the same way dark mode lets them pick a palette.

## The contract

Wrap the audience-specific parts of your copy in paired spans:

```html
<p>We <span data-bf="plain">keep your data safe</span><span data-bf="dev">encrypt at rest with AES-256</span>.</p>
```

One attribute on `<html>` decides which lens shows; one CSS rule hides the other:

```css
[data-audience="dev"]   [data-bf="plain"] { display: none; }
[data-audience="plain"] [data-bf="dev"]   { display: none; }
```

Unmarked content is shared and always shows. Works inline (a phrase) or block-level (a diagram for one reader, a code block for the other, both in the DOM, CSS picks). No build step, no runtime LLM, no dependency.

## Status

v0. This repo is the switcher contract and the self-demonstrating page at `index.html`. Two pieces are on the roadmap: a build-time generator (an LLM writes the second lens from your existing copy, you review it before publish) and a URL assessor (paste a link, see which reader your current site ignores). The standalone `bifocal.js` referenced on the site is not published yet.

## License

MIT.
