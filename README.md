# Communication Primer

This is a small Jekyll site for a communication-theory primer. The site is built for GitHub Pages and uses Markdown content, one shared HTML layout, and Sass variables for the basic visual system.

## Content ownership

The page copy currently in the repository is starter text. It gives the six pages a coherent structure, but it is not a substitute for your research, argument, citations, or editorial judgment. You are in charge of the content: verify claims, add the sources required by your assignment, revise the examples for your intended audience, and remove any wording that does not sound like you.

## Site map

The navigation follows this sequence:

1. **The Transmission View and Its Limits**: Shannon-Weaver and the humanist critique.
2. **Meaning and Culture**: semiotics and the production of meaning.
3. **Interpretation and Power**: Stuart Hall's encoding/decoding model.
4. **Interpretation and Intention**: Eco's intentions plus `intentio algorithmi`.
5. **What the Reader Should Do**: practical personal and professional guidance.
6. **How I Built This Site**: the stack, layout, content process, and agent involvement.

The files retain descriptive legacy filenames in `pages/`, but their public URLs and navigation labels use the new sequence. The public URL is controlled by each page's `permalink` value.

## How to create or revise a page

1. Open the relevant Markdown file in `pages/`.
2. Keep the YAML front matter at the top. A minimal page looks like this:

	 ```yaml
	 ---
	 layout: default
	 title: A Page Title
	 permalink: /pages/a-page-title/
	 ---
	 ```

3. Write the page in Markdown. Use one `#` heading for the page title, `##` headings for major sections, paragraphs for explanation, and lists for steps or examples.
4. Use specific examples to connect theory to an everyday or AI-mediated communication problem. Define specialist terms before relying on them.
5. Add sources as normal Markdown links or a short references section. Do not present the starter copy as finished scholarship.
6. If you add a new page, add its link to the navigation list in `_layouts/default.html`. Choose a unique permalink ending in `/`.

The existing `<section class="panel">` blocks are optional. They create a bordered reading block using the site's shared style. Each block should have a unique `aria-labelledby` value that matches the `id` on its heading, for example:

```html
<section class="panel" aria-labelledby="example-heading">
	<h2 id="example-heading">Example heading</h2>
	<p>Explain the idea and show why it matters.</p>
</section>
```

## Customize the basic CSS

The main stylesheet is `assets/css/style.scss`. Edit the variables in `:root` first; the rest of the stylesheet reuses them.

```scss
:root {
	--navy: #0b1f3a;       // header and footer
	--light-blue: #d8e9ff; // page background
	--mid-blue: #4f7fbf;   // panel accent
	--white: #ffffff;      // panel and light text color
	--text: #10233d;       // body text
	--focus: #ffd166;      // keyboard focus color
}
```

Keep contrast strong when changing colors, especially for body text, links, navigation, and keyboard focus. For larger visual changes, edit the matching selector below the variables. The layout is intentionally lightweight, so avoid changing the shared `.container`, `.site-nav`, or `.panel` rules unless you want the change across every page.

## Run the site locally

Install Ruby and Bundler, then install the locked dependencies:

```bash
bundle install
```

Start Jekyll with the repository's base URL:

```bash
bundle exec jekyll serve --baseurl /comm-primer
```

Open `http://localhost:4000/comm-primer/`. Jekyll rebuilds pages as you edit them. Stop the server with `Ctrl+C`.

Before publishing, check that every navigation link works, headings are in a logical order, links have useful text, and the page still reads clearly on a narrow screen. Build-only verification can be run with:

```bash
bundle exec jekyll build
```
