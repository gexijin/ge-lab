# ge-lab.org

Static site built by GitHub Pages with Jekyll (custom minimal theme in `_layouts/` and `assets/css/style.css`). There's nothing to install:
commit a change and the site rebuilds in about a minute.

## Common edits

- **Add a blog post:** create `_posts/YYYY-MM-DD-short-title.md`:

  ```markdown
  ---
  layout: post
  title: "My post title"
  ---

  Text in Markdown...
  ```

- **Edit the home tagline:** `index.md`. Publications link: `scholar` in `_config.yml`.
- **Add or edit a tool card:** `_data/software.yml`.
- **Add an image:** put it in `assets/images/` and write `![alt text]({{ site.baseurl }}/assets/images/file.png)`
  (the `{{ site.baseurl }}` prefix keeps links working on both github.io and ge-lab.org).
- **Footer links (`social`), title:** `_config.yml`.
- **Short link (e.g. ge-lab.org/idep):** add a file in `redirects/` like `redirects/idep.md`:

  ```markdown
  ---
  permalink: /idep/
  redirect_to: https://bioinformatics.sdstate.edu/idep/
  ---
  ```

Images and files from the old WordPress site are in `assets/uploads/`.
