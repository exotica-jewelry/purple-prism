# Purple Prism

A [theme component](https://gohugo.io/hugo-modules/theme-components/) for the
[Hugo](https://gohugo.io/) static site generator, layered on top of the
[Hyas theme](https://github.com/h-enk/hyas).

This theme component adds a stylistic "skin" on top of Hyas, affecting the
visual appearance, as well as adding some shortcodes -- but it retains the
underlying functionality that makes Hyas great.

## Using this theme component

Purple Prism is meant to be installed as a
[Hugo module](https://gohugo.io/hugo-modules/).

### Prerequisites

1. Hyas requires [Node.js](https://nodejs.org/) v16.x to be installed on your
   local machine.

2. Hugo modules require [Go to be installed](https://go.dev/dl/) as well.

3. Make sure you have a reasonably-recent version of Hugo (`hugo version`).
   Modules were introduced in 0.55, but additional module-related commands and
   settings have continued to appear up through at least 0.84.2.

4. Run `hugo mod help` and make sure you get back something that isn't an error,
   which confirms that the first two requirements have been met.

If you are new to Hugo modules, see
[rootwork/hugo-module-site](https://github.com/rootwork/hugo-module-site) and
[its resources](https://github.com/rootwork/hugo-module-site#additional-resources)
for more information.

### Installation

1. To begin a new site, run `hugo new site <site_name>`, where `<site_name>` is
   the path-friendly name of your site. If you want to have your Hugo-related
   files as a subdirectory of your project repo, run `hugo new site hugo` to put
   it in a subdirectory named `hugo`. If you have an existing site you want to
   integrate these themes into, it may be easiest to run these steps in a
   separate folder and then copy things over selectively.

2. `cd` into the directory you just created and run:

```sh
wget https://github.com/h-enk/hyas-child-theme/archive/refs/heads/master.zip -O master.zip && unzip master.zip && cp -a hyas-child-theme-master/* . && rm -rf hyas-child-theme-master && rm -f theme.toml && rm -f config.toml && rm master.zip
```

Optionally, you may want to remove the parent theme's Markdown files and Netlify
configuration. Be sure to leave the Node `package*.json` files in place.

3. Run `hugo mod init <repo_url>`, where `<repo_url>` is the protocol-less URL
   to your site's repo. For instance, this repo's URL would be
   `github.com/exotica-jewelry/purple-prism`. This will create a `go.mod` file.

4. Run `hugo mod get github.com/exotica-jewelry/purple-prism`. This will create
   a `go.sum` file.

5. Open the `config/_default/config.toml` file and find the `[module]` section.
   At the top of that section, before the `[[module.mounts]]` items, insert the
   following (note indentation is important!):

```toml
  [[module.imports]]
    path = "github.com/exotica-jewelry/purple-prism" # Theme components
```

6. Run `npm install` (`yarn` won't work here, unfortunately) to pull in the Doks
   dependencies.

7. Run `hugo server` to automatically download the Hugo modules and serve the
   site, viewable at [http://localhost:1313](http://localhost:1313).

### Updating themes and dependencies

[To update Hyas](https://gethyas.com/docs/help/how-to-update/) and Hyas
dependencies, run `npm outdated` to get a list of Node packages (including Hyas)
that have available updates, then run `npm update <pkg>` to update them
selectively.

To update Purple Prism, run:

```sh
hugo mod get github.com/exotica-jewelry/purple-prism
```

Or, if you have additional Hugo modules, you can update all of them by running:

```sh
hugo mod get -u ./...
```

There are
[other options](https://github.com/rootwork/hugo-module-site#updating-a-module)
for updating to a specific version.

### Modifying the theme

Settings from both Purple Prism and Hyas can be overridden in the usual Hugo
way: Adding files to your site subdirectories (`assets`, `static`, `data`,
`i18n`, etc.) with the same name as files in either theme will override those
files.
