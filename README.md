# Act as GoodReads

A GoodRreads books/reviews export script built out of frustration with their CSV export.

Disclaimer: This is raw, like Sushi, so haters to the left!

## What you get

* Download all, or from specific shelves, books/reviews for a given user ID (https://www.goodreads.com/user/show/9999999-mybuddy => 9999999 is the ID).
* All books/reviews are saved as separate files, with the name of the book as its name, but downcased, hyphenated and special characters removed (e.g, On Anger (Annotated) => `on-anger-annotated` ~ ISBN will also be prepended if any).
* Book/Review file extension is configurable (e.g, .txt, .org, etc...).
* The review body can optionally be saved as either HTML (default), Markdown or Text format.
* See `act-as-gr --help` for the rest of the options.

## What it looks like

Each book/review will look somewhat like (`on-anger-annotated.org`):

```org
* On Anger (Annotated)
ISBN:
Author: Seneca
Date Added: Mon Jan 12 14:17:37 -0800 2015
Shel{f,ves}: read,rome,philosophy,humorist
Goodreads Review Link: http://www.goodreads.com/review/show/1166234449
Goodreads Book Link: https://www.goodreads.com/book/show/19417143-on-anger
Rating: 0
State: published

** Markdown Review:
Learn to laugh.

```

## What you need

* An API key that you can get here: https://www.goodreads.com/api/keys
* A Bash console
* Ruby programming language installed
* `httparty`, `nokogiri`, `reverse_markdown` gems

## What you do

To install, `act-as-gr` is just a Ruby script, so drop it somewhere and make sure it's added to your `$PATH`. Or you can just use the following one-liner from your console:

```bash
$ sudo sh -c "curl https://raw.githubusercontent.com/jpablobr/act-as-gr/master/act-as-gr -o /usr/local/bin/act-as-gr && chmod +x /usr/local/bin/act-as-gr"
```

There's also couple of dependencies you'll need to install as well:

```bash
$ (sudo) gem install httparty, nokogiri, reverse_markdown
```

Once that's well and good run `$ act-as-gr -h` to see its further options, also to ensure everything has been install properly.


```bash
$ act-as-gr -h
Usage: act-as-gr [options]

Example: act-as-gr -v -u 9999999 -k YOUR-KEY -s read,to-read,i-want-money

    -u, --user_id                    User ID to download from
    -k, --key                        API key
    -a, --all                        Download all books (all shelves)
        --html                       Add a HTML format section of the review body
        --text                       Add a Text format section of the review body
        --markdown                   Add a Markdown format section of the review body
        --books-directory            Directory in which books will be downloaded
    -s, --shelves x,y,z              Books in given shelves
    -v, --verbose                    Run verbosely
    -o, --overwrite                  Overwrites books
    -c, --write-config-file          Creates config file

    -h, --help                       Print this help

```

You can also save some of the options in a config file (`~/.act-as-gr.yml`) allowing you not having to pass as many options to the script. To have the script create that config file for you just run:

```bash
act-as-gr --write-config-file
```

Note 1: Console options take precedence over config file options.

Note 2: The directory where all the book/reviews go, has to exist  and by default it is: `~/meta-library`.

Note 3: I went with the `~/meta-library` name because:

  - I don't always write reviews.
  - My reviews at times are just a bunch of notes that only make sense to me.
  - Being able to scan the meta data (status, authors, shelves, etc...) to come up with other meaningful and more holistic data is another priority of mine, but I'll try to address that in another way, not specifically with this script.

## What is next

* Better book/review export format/layout configurability.
* Option to get specific reviews by book/user id.
* Option to include comments too?
* Anything else?

## What I need

* A better API.

## What to Test

No tests. *shrug* lol

<3<3<3, yours truly
