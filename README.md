# Purple Prism

A [theme component](https://gohugo.io/hugo-modules/theme-components/) for the
[Hugo](https://gohugo.io/) static site generator, layered on top of the
[LoveIt theme](https://github.com/dillonzq/LoveIt).

Primarily this theme component is meant to be a stylistic "skin" on top of
LoveIt, affecting the visual appearance but retaining the underlying
functionality that makes LoveIt great.

## Using this theme component

Purple Prism is meant to be installed as a
[Hugo module](https://gohugo.io/hugo-modules/), and will only have practical
effect if used alongside LoveIt.

### Prerequisites

If your site is already using Hugo modules, you can skip this section.

1. [Go must be installed](https://go.dev/dl/) on your local machine.
2. Make sure you have a reasonably-recent version of Hugo (`hugo version`).
   Modules were introduced in 0.55, but additional module-related commands and
   settings have continued to appear up through at least 0.84.2.
3. Run `hugo mod help` and make sure you get back something that isn't an error,
   which confirms that the first two requirements have been met.
4. From your Hugo site directory, run `hugo mod init <repo_url>`, where
   `<repo_url>` is the protocol-less URL to your site's repo. For instance, this
   repo's URL would be `github.com/exotica-jewelry/purple-prism`. This will
   create `go.mod` and `go.sum` files, which you should commit to your repo.

If you are new to Hugo modules, see
[rootwork/hugo-module-site](https://github.com/rootwork/hugo-module-site) and
[its resources](https://github.com/rootwork/hugo-module-site#additional-resources)
for more information.

### Installation

Open your Hugo `config.toml` file and find the line beginning with `theme =`.
Replace that line with the following:

```toml
[module]
  [[module.imports]]
    path = "github.com/exotica-jewelry/purple-prism" # Theme components
  [[module.imports]]
    path = "github.com/dillonzq/LoveIt" # Project theme
```

Hugo modules override from bottom to top, so this first imports the LoveIt
theme, then imports the Purple Prism theme components which selectively override
parts of LoveIt.

Run `hugo` or `hugo server` and Hugo will automatically download the modules.

### Configuration and sample posts

If you are beginning a new site, you'll probably want to use LoveIt's
`exampleSite`, prefilled with configuration options and sample Hugo posts. From
your Hugo site directory, run:

```sh
wget -O - https://github.com/dillonzq/LoveIt/archive/master.tar.gz | tar xz && cp -a LoveIt-master/exampleSite/* . && rm -rf LoveIt-master && rm -f config.toml
```

Whether you're modifying an existing site or starting fresh, take a look at
[dillonzq/LoveIt/exampleSite/config.toml](https://github.com/dillonzq/LoveIt/blob/master/exampleSite/config.toml)
and copy over everything (except the `theme` and `themesDir` items) to your
site's configuration file, modifying the values as needed.
[Consult LoveIt's configuration documentation here.](https://hugoloveit.com/theme-documentation-basics/#3-configuration)

### Pulling in theme updates

Hugo modules are not updated automatically. To update all of your modules, from
your Hugo site directory run:

```sh
hugo mod get -u ./...
```

There are
[other options](https://github.com/rootwork/hugo-module-site#updating-a-module)
for updating an individual module or updating to a specific version.

### Modifying the theme

Settings from both Purple Prism and LoveIt can be overridden in the usual Hugo
way: Adding files to your site subdirectories (`assets`, `static`, `data`,
`i18n`, etc.) with the same name as files in either theme will override those
files.

Additionally, LoveIt provides `_override.scss` and `_custom.scss` files in
[`exampleSite/assets/css`](https://github.com/dillonzq/LoveIt/tree/master/exampleSite/assets/css).
See the
[LoveIt documentation](https://hugoloveit.com/theme-documentation-basics/#33-style-customization)
for details.
