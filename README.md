---
author: pfd
status: prototype
happy_dev: true
---

# SheerID Public Docs

This is a prototype Jekyll site, set up as a model for the forthcoming (March 2019) release of the public docs
for the new JavaScript library. 

## Requirements
  - Ruby

## Building Locally

1. Clone the pangaea repo
    ```
    $ git clone git@github.com:sheerid/pangaea.git
    ```
1. Navigate to the `/sheerid-docs` directory.
1. Run through the [Jekyll Quickstart](https://jekyllrb.com/docs/) so that your local environment is able to build from this directory.

    **Note**: You will probably need to set up [rbenv](https://github.com/rbenv/rbenv) if your local ruby environment is fussy.
1. Build the local server.
    ```
    $ bundle exec jekyll serve
    ```
1. browse to http://localhost:4000
1. If you have trouble, ping in #happy_devs Slack channel.

## Site structure

Currently this site is 3 different Jekyll themes hacked together:

* Home page is based on the [Bootstrap docs theme](https://github.com/twbs/bootstrap).
* The docs pages are based on the [Just the Docs theme](https://github.com/pmarsceill/just-the-docs).
* The API reference (3-column layout) is based on the [Aviator Jekyll template](https://github.com/CloudCannon/aviator-jekyll-template).

## Site features

### Admonitions

There are 4 admonitions available: note, success, warning, and danger, which are defined in the `_includes` directory. Example usage:

{% include note.html content="This is my sample note." %}

{% include success.html content="yay!" %}

{% include warning.html content="There may or may not be dragons in thar." %}

{% include danger.html content="This could be bad." %}


## TODOS

* user guide documentation
* uplevel concepts to a directory √
* create "customization" page, probably as a like 2nd-level tutorial. Start with it in Getting Started...maybe it goes elsewehre


## Development Notes

* We should follow bootstrap style and render the H1 and the lead class text from the title and description in the frontmatter. √ 
* set up a preview site for the Product team to review/comment. Github pages?


