## Every Layout with Svelte

This is a quick'n'dirty implementation of the publicly available layouts on https://every-layout.dev

You should buy the book :) You can then use this repo as a starting point to implement the rest
(it's rather simple, actually).

### What's here

**CSS**

- [Modern CSS reset](https://hankchizljaw.com/wrote/a-modern-css-reset/) (see App.svelte styles)
- [Measure](https://absolutely.every-layout.dev/rudiments/axioms/)
- [Modular scale](https://absolutely.every-layout.dev/rudiments/modular-scale/)

**Layout**

- [Stack](https://every-layout.dev/layouts/stack/)
- [Sidebar](https://every-layout.dev/layouts/sidebar/)
- [Cover](https://every-layout.dev/layouts/cover/)

Components have the same API as the custom components in the book.

### Screenshot

- A composition showcase from `App.svelte`
- All elements have their width constrained to `60ch` (see [Measure](https://every-layout.dev/rudiments/axioms/)).

<img width="1456" alt="Screenshot 2020-02-04 at 12 16 18" src="https://user-images.githubusercontent.com/32768/73740755-16449700-4749-11ea-8a51-9969ec28bb91.png">


---

## Run locally

```bash
npm run dev
```

Navigate to [localhost:5000](http://localhost:5000). 