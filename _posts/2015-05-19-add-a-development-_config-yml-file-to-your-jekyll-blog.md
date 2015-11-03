---
layout:     post
title:      "Add a development _config.yml file to your jekyll blog"
subtitle:   "Your settings are different when programming"
date:       2015-05-19 19:55:29
author:     "Benoit VALLON"
header-img: "/img/2015-05-19-add-a-development-_config-yml-file-to-your-jekyll-blog/post-add-a-development-_config-yml-file-to-your-jekyll-blog.jpg"
comments:   true
categories: tips
tags:       [jekyll, config]
---

# Running your jekyll blog on your machine

Jekyll made running your blog on your machine very easy. You just need to `jekyll serve` it and it will be available on your localhost port 4000.

```bash
jekyll serve

        Generating... done.
  Configuration file: _config.yml
      Server address: http://127.0.0.1:4000/
    Server running... press ctrl-c to stop.
```

By default, this command runs jekyll using the default configuration file `_config.yml` which is very convenient.

After adding other settings to your `_config.yml` file, you may start to want something to manage your configuration based on your environment. For example, you probably do not want to activate Google Analytics when you are programming or when you are working on a new post locally.

# Adding another `_config-dev.yml` file

Jekyll offers the option `--config` with its CLI tool which allows you to specify a list of files that will be used as a configuration. To use it, simply list all your configuration files and settings in the later files will override settings in earlier files.

```bash
jekyll serve --config _config.yml,_config-dev.yml

        Generating... done.
  Configuration file: _config.yml
  Configuration file: _config-dev.yml
      Server address: http://127.0.0.1:4000/
    Server running... press ctrl-c to stop.
```

with the following on `_config.yml`:

```yaml
disqus: benoitvallon
google_analytics: UA-63129957-1
google:
  webmaster-tools: 702z24ksUQH2oG6USnrPutOqAgBgNmvqe8hI9_qgvPk
```

and the following on `_config-dev.yml`:

```yaml
disqus: #benoitvallon
google_analytics: #UA-63129957-1
google:
  webmaster-tools: #702z24ksUQH2oG6USnrPutOqAgBgNmvqe8hI9_qgvPk
```

As those settings are empty in the second file (I just commented them) `_config-dev.yml` then those settings will not be injected in your blog. You will also need to make some modifications in your code to handle those cases. For example, my `analytics.html` file now includes a check on whether the setting `site.google_analytics` is set or not.

```html
{{ "{% if site.google_analytics " }}%}
    <!-- Google Analytics -->
    <script>
      Google Analytics script
    </script>
    <!-- End Google Analytics -->
{{ "{% endif " }}%}
```

# Bonus jekyll option `-w`

Run your `jekyll serve` with the `-w` option every times. Is will enable auto-regeneration of your site when the files are modified.

```bash
jekyll serve -w --config _config.yml,_config-dev.yml
```
