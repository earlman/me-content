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

For `/articles` and `/notes`, the textual content should go under the properties, as expected. 

## Reviews, Book Notes, Updates

Items in an `/experience` category may have optional notes stored in markdown as well.    However, these types of notes can often have a different nature to normal articles. There can also be many separate notes, written at different times, for each piece of content [more information below](). Therefore, some conventions should be put in place to maintain some organization, both in the database and the user interface.

**1)** New thoughts should be put at the top of the file (this does not include book notes being added while the book is still in progress).

**2)** New thoughts should be separated with a thematic break (`---`) and contain a date with h6 format like so: `###### Updated November 6, 2019`

**3)** Comments on the review itself such as *why it was written* or *how my previous mindset may have altered review* should be written in a `meta` container like so:
    
    ::: meta
    I fell asleep for a couple episodes in the middle of this but I really don't think they would've change my opinion of the show as a whole
    :::
    
    ::: meta
    I actually new nothing of the Manson Murders before watching this movie. I imagine living through those would have drastically changed my experience of the final scene, and perhaps of the rising action as well. 
    :::

#### Why not put all the reviews into `/articles`?

There's a good argument to be made for only allowing YAML in the `/experience` directory. This would allow a nice separation of concerns, keeping `/experience` as a log of events or a collection of experiences--cleanly separated from random musings and often-unfinished thoughts that I wanted to write down.

However, as editor-in-chief, it's extremely important that the main page for each piece of art displays **all** the associated thoughts. So, as a programmer, it's just not worth it to have to 1) figure out a data scheme that allow references between each piece of art and all related content 2) design and develop a way to display all of that content on the same page. 

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