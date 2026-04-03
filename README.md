
# Academic Pages

![pages-build-deployment](https://github.com/academicpages/academicpages.github.io/actions/workflows/pages/pages-build-deployment/badge.svg)

Academic Pages is a Github Pages template for academic websites.


# Getting Started

1. Register a GitHub account if you don't have one and confirm your e-mail (required!)
1. Click the "Use this template" button in the top right.
1. On the "New repository" page, enter your repository name as "[your GitHub username].github.io", which will also be your website's URL.
1. Set site-wide configuration and add your content.
1. Upload any files (like PDFs, .zip files, etc.) to the `files/` directory. They will appear at https://[your GitHub username].github.io/files/example.pdf.  
1. Check status by going to the repository settings, in the "GitHub pages" section
1. (Optional) Use the Jupyter notebooks or python scripts in the `markdown_generator` folder to generate markdown files for publications and talks from a TSV file.

See more info at https://academicpages.github.io/

## Running Locally

For this repository on macOS, the commands below are the ones that work:

```bash
cd /Users/jiachaobo/Desktop/code/jcbjcbjc.github.io

brew install ruby@3.2
export PATH="/opt/homebrew/opt/ruby@3.2/bin:$PATH"

bundle config set --local path vendor/bundle
bundle config set --local without development
CPLUS_INCLUDE_PATH="$(xcrun --show-sdk-path)/usr/include/c++/v1" bundle install

# auto-kill anything listening on port 4000
kill -9 $(lsof -tiTCP:4000 -sTCP:LISTEN) 2>/dev/null || true

# bundle exec jekyll serve -H localhost -l
/opt/homebrew/opt/ruby@3.2/bin/bundle exec jekyll serve -H localhost -l
```

Then open:

```text
http://localhost:4000
```

Notes:

1. If you update `_config.yml`, stop the server and rerun `/opt/homebrew/opt/ruby@3.2/bin/bundle exec jekyll serve -H localhost -l`.
1. If you do not want to kill the existing process on `4000`, use `/opt/homebrew/opt/ruby@3.2/bin/bundle exec jekyll serve -H localhost -P 4001 -l`.
1. The `CPLUS_INCLUDE_PATH=... bundle install` step is needed on this machine so the `eventmachine` native extension can compile successfully.

## Redeploy

After you confirm the local preview is correct, redeploy to GitHub Pages with:

```bash
git add .
git commit -m "update site"
git push origin master
```

GitHub Pages will rebuild automatically after the push.

# Maintenance 

Bug reports and feature requests to the template  should be [submitted via GitHub](https://github.com/academicpages/academicpages.github.io/issues/new/choose). For questions concerning how to style the template, please feel free to start a [new discussion on GitHub](https://github.com/academicpages/academicpages.github.io/discussions).

This repository was forked (then detached) by [Stuart Geiger](https://github.com/staeiou) from the [Minimal Mistakes Jekyll Theme](https://mmistakes.github.io/minimal-mistakes/), which is © 2016 Michael Rose and released under the MIT License (see LICENSE.md). It is currently being maintained by [Robert Zupko](https://github.com/rjzupkoii) and additional maintainers would be welcomed.

## Bugfixes and enhancements

If you have bugfixes and enhancements that you would like to submit as a pull request, you will need to [fork](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/working-with-forks/fork-a-repo) this repository as opposed to using it as a template. This will also allow you to [synchronize your copy](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/working-with-forks/syncing-a-fork) of template to your fork as well.

Unfortunately, one logistical issue with a template theme like Academic Pages that makes it a little tricky to get bug fixes and updates to the core theme. If you use this template and customize it, you will probably get merge conflicts if you attempt to synchronize. If you want to save your various .yml configuration files and markdown files, you can delete the repository and fork it again. Or you can manually patch.
