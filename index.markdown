---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: my_layout
---

Hi, I am a dummy website. Time to change the theme. The steps below can be used as an approximate guide.

## Changing The Theme

We are using [Dummy-Website-1 Repo](github.com/jmount1992/dummy-website-1) as a starting point. Feel free to fork or download a zip copy to get started.

1. Ignore the instructions on [GitHub Pages Documentation](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/adding-a-theme-to-your-github-pages-site-using-jekyll). It will lead you astray.
2. However, we can still use any of the supported [themes](https://pages.github.com/themes/)
3. We will use the Cayman theme.
4. In `Gemfile` comment out line 12: `gem "minima", "~> 2.5"`
5. In `_config.yml` (can check out the [repo](https://github.com/jmount1992/dummy-website-2) for more insights):
    - Remove or comment out the line: `theme: minima`
    - Add the line: `remote_theme: cayman`
    - Change the list of plugins to only include: `jekyll-remote-theme`
4. In the `index.markdown` add links to the About and Post pages. Can check out the [repo](https://github.com/jmount1992/dummy-website-2) if you are unsure on how to do this.
6. Serve the website locally.
    - You will probably find the theme is not applied.
    - Look at the warnings, you will see `Layout 'post' requested in ... `
    - Change the layout in the front matter of the pages to `default`. The available layouts are found in `_layouts`.
7. Once you are happy, push this now up to Github and watch the live site change.

Links:
- [Link to About](about)
- [Link to Post](_posts/2022-10-29-welcome-to-jekyll.markdown)


## Repurposing Provided Elements and Hacking Themes

Many things can be easily "hacked" by simply repurposing elements. In the Cayman theme, for example, if we turn on `show_downloads`, on of the configuration variables specific to this theme (it may also be available in other themes), we will get three buttons underneath the heading. If we read a little further in the theme's [documentation](https://github.com/pages-themes/cayman), we see we can override the URLs. Let's try that!

1. In `_config.yml` add the following lines:
```yaml
github: # the following URLS were found by looking in the _site folder built 
  repository_url: index
  zip_url: about/index
  tar_url: jekyll/update/2022/10/29/welcome-to-jekyll
```
    - These keys were found by reading the theme's documentation and looking at the `_layouts/default.html` [file](https://github.com/pages-themes/cayman/blob/master/_layouts/default.html#L22).
    - The valus were found by looking in the locally built _site folder and finding the path to the desired files. Note the `.html` extension for each is dropped. 
    - These three variables are injected by GitHub pages.

2. Serve the page locally, and try clicking on these buttons. You will find they work if the URL is initially `http://127.0.0.1:4000/` but if the URL is anything else the links don't work. We can easily fix this!

3. If you read the [Jekyll Theme Documentation](https://jekyllrb.com/docs/themes/) you will see that we can create our own layouts, or overwrite the standard theme layouts. Create a folder called `_layouts` and create a new layout file in this folder called `my_layout.html`. Open up this file and perform the following (see explanations below for reasoning/details):
    1. Copy the default layout into the `my_layout.html` file by going [here](https://raw.githubusercontent.com/pages-themes/cayman/master/_layouts/default.html) and copying the contents (warning this is the default layout for the Cayman theme, if you chose a different theme go to its default)
    2. Change line 22 to: `<a href="{{ site.github.repository_url | relative_url }}" class="btn">Home</a>`
    3. Change line 25 to: `<a href="{{ site.github.zip_url | relative_url }}" class="btn">About Me</a>`
    4. Change line 26 to: `<a href="{{ site.github.tar_url | relative_url }}" class="btn">An Article</a>`

4. Change the layout of the index, about, and post page to use our new `my_layout` layout. Serve the page locally again and check out the results.

5. Okay push the changes to GitHub and see how it goes. You might find out that you get a 404 error. If this is a project page website (see [here](https://docs.github.com/en/pages/getting-started-with-github-pages/about-github-pages#types-of-github-pages-sites) for defintions) we need to make sure we set the `baseurl` in `_config.yml`. In this example we set it to `baseurl: "/dummy-website-2"`.

### Some Explanations
The {% raw %}`{% %}`{% endraw %} and {% raw %}`{{ }}`{% endraw %} is [Liquid](https://shopify.github.io/liquid/basics/introduction/) syntax. The {% raw %}`{% %}`{% endraw %} are tags and these create logic and control flows. The {% raw %}`{{ }}`{% endraw %} are objects and these are [variables](https://jekyllrb.com/docs/variables/) that contain content will be displayed on the page. Liquid also has a lot of in-built filters to help do things, and Jekyll as provided several additional handy [filters](https://jekyllrb.com/docs/liquid/filters/). The `relative_url` is one such filter added by Jekyll, and it tells that the URL held within the variables are relative to the home directory.

Depending on your OCD level. You may not wish to overwrite the three variables created and injected by GitHub Pages. Instead you may wish to create your own, more appropriate variables. Creating [Jekyll variables](https://jekyllrb.com/docs/variables/) are fairly straight forward. However, if you read that documentation you will notice we instead could have used the following instead of overwriting variables:

- {% raw %}`{{ site.url }}`{% endraw %} for our home page link
- {% raw %}`{{ site.url }}/about`{% endraw %} for our about page link.
- {% raw %}`{{ site.url }}/jekyll/update/2022/10/29/welcome-to-jekyll`{% endraw %} for our about page link.

Obviously, templating the article link how we did is likely to end up broken (page is likely to be moved, renamed, etc). However, using this sort of technique for pages unlikely to change location within the website structure (e.g., about me, publication lists, etc.) is okay.