# Portfolio template (Jekyll)

A portfolio site where all content lives in two places:

Name, bio, skills, contact, resume, site-wide SEO: `_data/site.yml`
Each project (text, images, per-project SEO): `_projects/<project-name>/index.md`

## Editing the site info

Open `_data/site.yml`.
The headshot is `assets/images/headshot_james-evans.png` and the resume is `assets/james-evans_resume.pdf` (set via `hero.headshot` and `hero.resume_file`). Drop a social-preview image at `assets/images/og-image.png` (1200x630).
`name` is the short name shown in the nav and hero; `full_name` is used in page titles and search-engine data.

The "About" story lives in `about.md` (served at `/about/`), and the music placeholder page in `music/index.html` (set to `noindex`).

## Adding a project

1. Create a folder in `_projects/` (the folder name becomes the web address), e.g. `_projects/my-project`.
2. Put the project's images in that same folder.
3. Copy `_templates/project-template.md` to `index.md` in that folder: the content in between the '---' lines holds the title, summary, tags, cover image and SEO;
   - Everything below is the project write-up in Markdown.
   - Reference images by file name only: `![Alt text](screenshot.jpg)`.
4. Optional front matter: `year` (shown as "Date", e.g. `November 2026`), a single `link`, `tools:` (chips, each with a Font Awesome `icon` and a `label`) and `links:` (the "Deliverables" tiles, each with `icon`, `text` and `url`). See any existing project for the format.
5. For side-by-side text and images, galleries, captions and video embeds, see the HTML blocks (`side-by-side`, `image-grid`, `caption`, `video-embed`, `hint`) in any existing project.

**Reordering:** change `order:` (lower = first). **Hiding:** add `published: false`.

### Per-project SEO

By default the page title is `Project title | Your Name`, the description is the `summary`, and the share image is the `cover`.
Override with `seo_title`, `seo_description`, `seo_image` in the front matter.

## Running locally

```sh
bundle install
bundle exec jekyll serve
```

Then open http://localhost:4000. The `url` in `_data/site.yml > seo` must be set to the live address
before launch (it is used for canonical links, social previews and the sitemap).

## Deploying

The output is plain static files (`bundle exec jekyll build` -> `_site/`), so Netlify, Cloudflare Pages,
Vercel or GitHub Pages (via a GitHub Actions workflow) all work. If deploying to a sub-path, set `baseurl` in `_config.yml`.

`sitemap.xml` and `robots.txt` are generated automatically.
