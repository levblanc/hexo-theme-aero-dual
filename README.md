# Aero Dual Hexo Theme

A hexo theme with aero, responsive design. **Easy switch of dark and light style by simple config ([will explain below](https://github.com/levblanc/hexo-theme-aero-dual#configuration)).** You can also change theme color by modifying corresponding stylesheet. Each style has **FIVE** colors ready to use ([check it out!](https://github.com/levblanc/hexo-theme-aero-dual#change-theme-color)).

[See It Live Here](https://levblanc.github.io/) (configured as light theme style, blue theme color).

**Please note:**

This theme **does not** support widgets(other than tag, category and archive) and article comments(Disqus and others) out of the box. Adding them would be a **big maybe**, depending on my current workload. 

If you really like this theme, feel free to tweak and play with it on adding them by yourself. Also, checking out other hexo themes may help. :)

![Dark and Light Style Switch](https://github.com/levblanc/hexo-theme-aero-dual/blob/master/source/img/aero-dual-thumbnail.jpg)

![Theme Color Switch](https://github.com/levblanc/hexo-theme-aero-dual/blob/master/source/img/aero-dual-color-change.jpg)


## Third party libraries used
- [Bootstrap](http://getbootstrap.com/css/)
- [Highlight.js](https://highlightjs.org/) (for code highlight)
- [Typo.css](https://github.com/sofish/typo.css) (for better Chinese reading experience)


## Installation

### Install

``` bash
$ git clone https://github.com/levblanc/hexo-theme-aero-dual.git themes/aero-dual
```

**Aero-dual was developed under Hexo 3.2.2, other hexo versions' capatabilities are not tested yet.**


### Enable

Modify `theme` setting in your blog's main `_config.yml` to `aero-dual`.


``` yaml
# Extensions
## Plugins: http://hexo.io/plugins/
## Themes: http://hexo.io/themes/
theme: aero-dual
```


### Update

``` bash
cd themes/aero-dual
git pull
```


## Configuration

You will have to start `hexo server` locally to see the changes.


### Change Theme Style

In your blog's main `_config.yml`, configure `theme_style` as `dark` or `light` (this is where `dual` in the theme's name comes in to play). **Restart** your server after modifying the `theme_style` to see the change.

``` yaml
# theme_style is default to 'light'
theme_style: dark
```

### Change Theme Color

To do this, you need to dig into the theme's stylesheets.

But **RELAX**, it's **SIMPLE**.

Under the following path:

``` bash
<your-blog>/themes/aero-dual/source/css/
```

There are two stylesheet files: `style.light.styl` and `style.dark.styl`.
(OK, if you really don't know how to find them following the above path, just **search the files by name** in your project :) )

Let's use `style.light.styl` as example. You will see colors already pre-configured in this file:

``` stylus
/* basic colors */
$color-white      = #FFF
$color-black      = #555
$color-beige      = #F0E8DF
$color-grey       = #85878A
$color-light-grey = #E1E1E1

/* theme colors */
$light-red    = #F03838
$light-pink   = #EA4D8A
$light-orange = #ff6347
$light-blue   = #1999EC
$light-purple = #B27DF4

/* modify value of $theme-color to theme colors specify above
  to enable different theme colors */
$theme-color            = $light-blue   
$theme-text-color       = $color-black
$theme-background       = $color-white
$theme-code-background  = $color-beige
$theme-seperator        = $color-light-grey
$theme-dotted-seperator = $color-grey
```

Now Change `$light-blue` to `$light-orange`, and save the file.

``` stylus
$theme-color = $light-orange
```

If you have `hexo-browsersync` installed locally, the page will automatically refresh when you change the `$theme-color` value. If you haven't installed this package, just refresh the page by yourself.

This way, you can add even more colors to the stylesheet and change it whenever you want. `style.dark.styl` works just the same.

Even more, you can configure all colors in this stylesheet to your content.

PS: I haven't figured out the way to pass settings in `_config.yml` into stylesheets. If this can be done, it would be much easier to configure colors, rather than having users to change values in stylesheets. Please send me an email or open a new issue if any one knows how to do this. Thanks!


### Banner image

Modify `use_header_cover` to enable/disable banner.
Modify `index_cover` in the theme's `_config.yml` to change banner image.

``` yaml
# Set to false to disable banner
use_header_cover: true

# URL of the banner image
# Put your custom banner image under
# the theme's img folder: your-blog/themes/aero-dual/source/img/
# and modify index_cover's value like so:
# index_cover: /img/your-custom-banner.jpg
# or
# Put your custom banner image under
# your blog's images folder: your-blog/source/images/
# and modify index_cover's value like so:
# index_cover: /images/your-custom-banner.jpg
# or
# Specify an online resource like so:
# index_cover: http://somewhere.com/path/to/banner.jpg
index_cover: /img/default-banner-dark.jpg
```

Up till this step, even if you don't change the theme color, you'll have at lease **FOUR** variations of the theme: `dark` style with or without home page banner; `light` style with or without home page banner.


### Post's Banner Image

Home page banner and post page banner is set to be the same by default.
You can specify a custom cover in the front-matter:

``` markdown
title: My awesome title
date: 2016-07-25 18:38:45
tags: ["awesome"]
cover: /images/awesome-bg.jpg  # <= remember to add this line in your post
---
```

You will need to create an `images` folder under your blog's `source` folder, and put your own `awesome-bg.jpg` in it for the above config to work. Of course, you can use whatever folder and image names you want, but be sure to reference them correctly in the `cover` line.

``` bash
your-blog
├── _config.yml
├── node_modules
├── package.json
├── public
├── scaffolds
├── source
│    ├── _posts
│    └── images   # <= here
└── themes
```

Also, be aware of the color of the cover image you choose, since the title and menu color are set to white by default. Texts are very hard to distinguish in white backgrounds, although I've given the texts some shadow already.


### Menu

Modify `menu` values in the theme's `_config.yml`.
You can change `GitHub` and `Email` to other menu item names you want. Or you can just change these two keys' values to your own info.

``` yaml
# Header Menu
menu:
  Home: /
  Archives: /archives
  # change github and email values to your own info
  Github: https://github.com/levblanc
  Email: mailto:levblanc@163.com
```


### Configuable texts

Default words used for post title, category, tag, excerpt (when not specified) and archive page title are configured in the theme's `languages/en.yml` and `languages/zh_CN.yml`.

``` yaml
# en.yml
untitled_post: Untitled Post
uncategorized: Uncategorized
untagged: Untagged
no_excerpt: No Post Excerpt
archive_title: Blog Archives
```


### Other Configs

Configure your Google Analytics Tracking ID, favicon in the theme's `_config.yml`.

``` yaml
# favicon
favicon: /favicon.png

# Google Analytics Tracking ID
google_analytics:
```
