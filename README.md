# My [Blog's](https://earlman.me) Content

This repository contains only the content (articles, notes, tweets, creations, etc) of my blog at [earlman.me](https://earlman.me). It has two responsibilities:

1) Track the content and changes to the content
2) Don't do anything besides what's mentioned in item 1

[The rest of the website's code can be found here](https://github.com/earlman/me)

## Usage

This file is to be used as a [submodule](https://git-scm.com/book/en/v2/Git-Tools-Submodules) of the [main repository](https://github.com/earlman/me).

### Updating the Main Repo

In order to get the latest content synced to the main repository, first go to the submodule's directory: `cd content`

Switch the submodule's branch to master: `git checkout master`

Pull the latest changes: `git pull`

Stage the main repository: `cd .. && git add .`

Commit the the new submodule reference: `git commit -m "update content submodule"`

[These instructions were adapted from here.](https://chrisjean.com/git-submodules-adding-using-removing-and-updating/)

## Folder Structure

For the initial version of this blog, the folder structure will be as follows:

    content
    ├── articles
    ├── notes
    └── experience
        ├── books
        ├── movies
        └── shows
    
Eventually, this will be expanded:

    content
    ├── articles
    ├── notes
    ├── action_upcoming
    │   ├── creations_upcoming
    │   └── career_upcoming
    │   
    └── experience
        ├── books
        ├── movies
        ├── shows
        ├── games_upcoming
        └── music_upcoming


content/note/: A short idea that's worth holding on to, without the need for further context. 
content/article/: A pieces of content where the author is arguing an opinion or explaining a point of view. In contrast a `note` has no obligation to further explain what's contained.  

## Formatting

This content will be stored as Markdown files, with properties formatted as YAML.

There will eventually be requirements for the properties of each piece of content.

---

## Metadata

### Experience

- `title`
- `creator`
    - `/books`: Use author
    - `/movies`: Use director
    - `/shows`: Use author (as used in Wikipedia)
- `date-completed`: The date or approximate date of the experience. See [DateTime](#DateTime) for formatting.
- `date-published`: The date the file was created in the earlman.me content repository. See [DateTime](#DateTime) for formatting..
- `rating`: An object or array of objects with the following properties
    - `score`: A score between -5 and 5
    - `date`: The date the rating was created. Useful information for replays and noting delayed ratings/bias. By default should show latest rating?
- `link`
    - `/books`: NOT USED
    - `/movies`: Wikipedia page
    - `/shows`: Wikipedia page. Link to either the "season" page or "show" page, depending on what the file refers to. See `season` field.
- `isbn`
    - `/books`
    - `/movies`: NOT USED
    - `/shows`: NOT USED
- `season`
    - `/books`: NOT USED
    - `/movies`: NOT USED
    - `/shows`:
        - `all`: Denotes a show completed in its entirety and implies rating includes all seasons.
        - `<int>`: Implies review only pertains to this season.

### Articles
- `title`:
- `date-published`:
- `date-created`:
- `date-updated`:
- `tags`:
- `category`: Accepts `action`, `maintenance`, or `experience`

### Notes
- `date-published`:
- `date-created`:
- `date-updated`:
- `tags`:
- `private`: boolean. when 'true', tweet cannot be accessed unless logged in


* Notes do not allow for heading in body





### DateTime
The accepted date format is extended format according to [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601):

`YYYY-MM-DDThh:mm:ssTZD`

**Note:** This standard only refers to the plain-text version, as it's stored in the database. Implementations of the data can and should adjust the format to make it easier to read.