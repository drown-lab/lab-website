# Drown Lab Website

A static Jekyll site that incorporates with [Forestry CMS](https://forestry.io). Many thanks to the folks at Forestry for providing a template.

## Deployment

The site is currently deployed via <https://netlify.com>. Ask Bryon about details.

## Running locally

### Requirements

- Ruby 4.0 (the exact version is in `.ruby-version`; Netlify builds with it too)
- Bundler 4
- Jekyll 4.4 (installed by Bundler)

On Windows, install Ruby with [RubyInstaller](https://rubyinstaller.org/) (the x64 "with Devkit" build).

Once you've cloned the repository:

```{bash}
# Install project dependencies
bundle install

# Run a local server to preview your work 
bundle exec jekyll serve
```

### Running with Docker instead

If you'd rather not install Ruby, Docker can build and serve the site with the
same Ruby version Netlify uses:

```{bash}
docker run --rm -it -p 4000:4000 -v "$PWD:/site" -w /site -e JEKYLL_ENV=preview ruby:4.0.7 \
  bash -c "bundle install && bundle exec jekyll serve --host 0.0.0.0 --force_polling"
```

(`JEKYLL_ENV=preview` keeps links relative; otherwise they point at `0.0.0.0`,
which browsers won't open.)

Then open <http://localhost:4000>.

## Editing content

- **Group meeting schedule:** `_data/group_meetings.yml`, once per semester
- **Navigation links:** `_data/navigation.yml`
- **Research programs:** one file per program in `_projects/`, ordered by `order:`
- **Contact details** (header, footer, Contact page): `_data/information.yml`
