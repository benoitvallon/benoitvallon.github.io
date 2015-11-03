# Personal blog

It is available at [blog.benoitvallon.com](http://blog.benoitvallon.com)

# Run it locally

When run locally, it is advise to launch it with the command:

```shell
jekyll serve -w --config _config.yml,_config-dev.yml
```

The different params do the following:

- `-w`: enable auto-regeneration of the site when files are modified
- `--config _config.yml,_config-dev.yml`: specify config files instead of using `_config.yml` automatically. Settings in later files override settings in earlier files. In our specific case, `_config-dev.yml` will disable some analytics tools which is what we want when we run it locally
