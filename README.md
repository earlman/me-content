# My [Blog's](https://earlman.me) Content

This repository contains only the content (articles, notes, tweets, creations, etc) of my blog at [earlman.me](https://earlman.me). It has two responsibilities:

1) Track the content and changes to the content
2) Don't do anything besides what's mentioned in item 1

[The rest of the website's code can be found here](https://github.com/earlman/me)

## Usage

This file is to be used as a [submodule](https://git-scm.com/book/en/v2/Git-Tools-Submodules) of the [main repository](https://github.com/earlman/me).

### Updating the Main Repo

In order to get the latest content synced to the main repository, first initialize the submodules: `git submodule init`, then `git submodule update`

Change to the submodule's directory `cd content`

Switch the submodule's branch to master: `git checkout master`

Pull the latest changes: `git pull`

Commit the main repository: `cd .. && git commit`

## Formatting

This content will be stored as Markdown files, with properties formatted as YAML.

There will eventually be requirements for the properties of each piece of content.
