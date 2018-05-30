---
title: "Building this blog part I: Going Hugo"
date: 2018-05-27
categories:
- web
tags:
- blogging
keywords:
- hugo
- github
- gitlab

autoThumbnailImage: false
thumbnailImagePosition: "top"
thumbnailImage: /images/20180527_hugo_filtered.jpg
coverImage: /images/20180522_covering_centred_2.jpg
metaAlignment: center
---
If you want to make a blog like this one, here's how to do it. I'm also noting it down for my own use, in case I need to replicate my setup again. Hugo's straightforward enough that anyone new to it (like me) can quickly be effective with it.
<!--more-->

My current setup uses:

- Hugo - to build the static website
- Github - to host my website and keep my public repository (though I'm going to move to Netlify soon)
- Gitlab - where I have my private repository

## Why Hugo?

Short version: my friend recommended that I give Hugo or Jekyll a shot when he heard that I wanted to start this blog. After comparing the two technologies, I felt the general consensus was that Hugo was faster but had fewer features/ themes (see the [full version]({{<relref "#why-hugo-full">}}) at the bottom).

I'm currently using Ubuntu LTS 16.04 and so binary executables aren't a thing. In fact you'll have an easier time if you're using windows, since you can just download and use the GUI installers.

Although it's possible to install Hugo directly from the Ubuntu software centre or just using `apt-get`, don't! I couldn't get the website to build initially, because of an out-of-date version of Hugo.

Instead, go to the [Hugo release page] (https://github.com/gohugoio/hugo/releases) and download the most recent version of Hugo. Make sure that you've git installed to make things easier.

If needed, check that the download completed successfully against the checksums txt (on the release page) by using `md5sum`.

{{< codeblock "" "bash">}}
cd Downloads;\
md5sum hugo*.deb
{{< /codeblock >}}

Go ahead and install it.

{{< codeblock "" "bash">}}

# Assuming you're also using Ubuntu
sudo dpkg -i hugo*.deb;\

# Now let hugo do its magic...
hugo new site myblog
{{< /codeblock >}}

The last line allowed hugo to build the skeleton for a website.

Hugo doesn't come with a default theme, and after hunting around a bit I settled for [tranquilpeak](https://tranquilpeak.kakawait.com/). For this example, I'll use the [ananke](https://themes.gohugo.io/gohugo-theme-ananke/) theme as an example instead since it's a bit easier to start off with, but feel free to [hunt around] (https://themes.gohugo.io/). You can also follow the [quick start guide](https://gohugo.io/getting-started/quick-start/).

Note that using `git submodule` over `git clone` is important if you want to use netlify.

{{< codeblock "" "bash">}}
cd myblog;\

# Initialise Git
git init;\

# Download the Tranquil peak theme
# Make sure to change to the right URL if you prefer another theme
git submodule https://github.com/budparr/gohugo-theme-ananke.git themes/ananke;\

# Now tell hugo the theme you want to use
echo 'theme = "ananke"' >> config.toml;\

# Say hello to the world
hugo new posts/hello-world.md
{{< /codeblock >}}

Note that you can also just open the configuration file with any text editor and add in `theme = "ananke"` directly, instead of through the terminal.

So fire up `hugo server` to host from your local machine.
{{< codeblock "" "bash">}}
hugo server
{{< /codeblock >}}

Pour yourself a cup of coffee, open up your favourite browser, `Ctrl+L` (gotta love this shortcut) to the URL bar, type in `localhost:1313', and sit back to enjoy the ananke theme.

## Why Hugo (full version)? {#why-hugo-full}

The rise of the static website generators over the past few years is well-documented, for example [here](https://www.smashingmagazine.com/2015/11/modern-static-website-generators-next-big-thing/). The leading contenders really came down to Hugo and Jekyll, as my friend had recommended.

Despite the name, static websites generator can form part of the [jamstack](https://jamstack.org/), which you can build dynamic & interactive websites with.

Advantages of Hugo:

- It's fast - it's the only static website generator written in a static type language (golang) out of the top twenty most popular, according to [StaticGen](https://www.staticgen.com/). In a nutshell, something that's static means that the computer has fewer things to decide at runtime, and that makes things *fast* to build, deploy and load.
- It's easy to use. OK, it's not quite point and click ([FrontPage](https://en.wikipedia.org/wiki/Microsoft_FrontPage), anyone?), but anyone happy to play around with some configuration files and markdown will be able to produce a decent website.
- You have loads of themes to choose from. Granted, not as many as Jekyll, but likely more than enough for the most folks. Of course, if you really can't find one to your liking, you can always build your own.

Disadvantages of Hugo:

- It's static so it won't be, well, so dynamic. But then that's not really a huge issue any more in the current landscape, as mentioned previously. 'Static' websites can do many things previously limited to 'dynamic' websites, such as [content management](https://gohugo.io/content-management/),  [comments](https://gohugo.io/content-management/comments/) and even [search](https://gohugo.io/tools/search/)
- It's not quite as full-featured as Jekyll, so you won't see a plugin API like that of Jekyll's. On the other hand, this wasn't a major obstacle for me.

For me, the benefits of Hugo far outweighed the downsides - it was perfect for my blog.

Oh, and did I mention, Hugo is *fast*?
