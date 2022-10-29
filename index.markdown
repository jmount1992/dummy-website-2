---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: default
---

Hi, I am a dummy website. Time to change the theme.

1. Ignore the instructions on [GitHub Pages Documentation](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/adding-a-theme-to-your-github-pages-site-using-jekyll). It will lead you astray.
2. However, we can still use any of the supported [themes](https://pages.github.com/themes/)
3. We will use the Cayman theme.
4. In `Gemfile` comment out line 12: `gem "minima", "~> 2.5"`
5. In `_config.yml` (can check out the [repo](https://github.com/jmount1992/dummy-website-2) for more insights):
    - Remove or comment out the line: `theme: minima`
    - Add the line: `remote_theme: cayman`
    - To the list of plugins add: `jekyll-remote-theme`
6. Feel free to check out how it looks by serving the website locally.
7. Once you are happy, push this now up to Github and watch the live site change.