<style>
.reveal h1, .reveal h2, .reveal h3 {
  word-wrap: normal;
  -moz-hyphens: none;
}
</style>

Building a Personal Website with Blogdown and Github Pages
========================================================
author: Joseph Carl
date: June 3, 2017
autosize: true

Why Blogdown?
========================================================

- Build your Entire Site in RStudio
  + Not Just for Blogs, Projects too!
- Easier to Incorporate RMarkdown in Blog Posts
- Hugo Doesn't Require Ruby/Other Dependencies

Getting Started: Set Up Two Repos
========================================================

- Create Two Repos on Github
  + You could use one repo with a subbranch
- Repo 1: `<yourusername>.github.io`
  + This is where your site will be built
  + Must be named in this format
- Repo 2: `blog` (or whatever you want to call it)
  + This is for the source code to build your site
- Create Two Local Folders and Clone Your Repos
  + Delete `README.md` if it exists

Getting Started: In RStudio
========================================================


```r
# Install blogdown package
devtools::install_github('rstudio/blogdown')

# Load blogdown package and install Hugo
library(blogdown)
install_hugo()

# Change working directory to where you will build your site(s)
setwd("~/Documents/Github")
```

Creating the Website
========================================================


```r
# Create new site in the cloned blog repository
new_site(dir = 'blog', # Local repo folder name
         theme = 'kakawait/hugo-tranquilpeak-theme',
         format = 'toml') # 'toml' or 'yaml'

# Change working directory to 'root' folder of site in order to serve site/write new posts
setwd("~/Documents/Github/blog")

# Rebuild and preview the website
serve_site()
```

<small>After calling `serve_site()`, go to `localhost:4321` in browser</small>

Creating the Website
========================================================


```r
# Create a new post
new_post(title = 'your-post.Rmd')
```

Every time you save your page, RStudio calls `serve_site()`

![blogpost](blogpost_rmd.png)

Editing the .toml/.yaml File
========================================================

This file is the backbone of your site, where most options are set

Some of the important options:

- `baseurl = "https://<yourusername>.github.io/"`
- `theme = "hugo-tranquilpeak-theme"` 
  + (replace with your theme name)
- `publishDir = "../<yourusername>.github.io"`
  + This is the path to your other local repo <yourusername>.github.io
  + This will hold your site's published content, which you push to Github

Building Your Site
========================================================

In RStudio: `build_site()`

In Terminal:
- `cd ~/Documents/Github/<yourusername>.github.io`
- `git add .`
- `git commit -m "building site with blogdown"`
- `git push origin master`

Open `<yourusername>.github.io` in your browser

Finished Site
========================================================

![photo2](homepage.png)

You Can Add More than Blog Posts!
========================================================

![photo1](resume.png)

Resources
========================================================

- Blogdown Documentation
  + https://bookdown.org/yihui/blogdown/
- Two-Repo Tutorial
  + https://tclavelle.github.io/blog/blogdown_github/
- Repo with Subbranch Tutorial
  + https://proquestionasker.github.io/blog/Making_Site/
- Hugo Themes
  + http://themes.gohugo.io/
