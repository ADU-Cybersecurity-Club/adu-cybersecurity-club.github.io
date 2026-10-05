# ADU Cybersecurity Club

The website of the ADU Cybersecurity Club: <https://adu-cybersecurity-club.github.io>

It is a [Jekyll](https://jekyllrb.com) site using the [Chirpy](https://github.com/cotes2020/jekyll-theme-chirpy) theme. Every push to `main` builds and publishes the site through GitHub Actions (`.github/workflows/pages-deploy.yml`).

## Write a post

Add one Markdown file to `_posts/`, named `YYYY-MM-DD-short-name.md`, and open a pull request.

## Run it locally

```bash
bundle install
bundle exec jekyll serve
```

Then open <http://127.0.0.1:4000>.

To run the same check the deploy runs:

```bash
JEKYLL_ENV=production bundle exec jekyll b
bundle exec htmlproofer _site --disable-external \
  --ignore-urls "/^http:\/\/127.0.0.1/,/^http:\/\/0.0.0.0/,/^http:\/\/localhost/"
```

## Where things are

| Path | What it is |
|---|---|
| `_config.yml` | Site name, tagline, links, avatar |
| `_posts/` | Posts, one file each |
| `_tabs/about.md` | The About page |
| `assets/img/` | Logo, favicons and post images |

## License

The theme files come from [chirpy-starter](https://github.com/cotes2020/chirpy-starter) under the MIT license (see `LICENSE`).
