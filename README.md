# Flipper Community wiki
This is the repo for the [Flipper community wiki](https://flipper.wiki).
If you'd like to contribute to this wiki, you may fork the repo and offer your changes as a pull request.
Please be sure submissions meet the [contribution guidelines](https://flipper.wiki/contributing/).

# Technical docs
This wiki is built using the mkdocs builder using the material theme

# Quick and Dirty How-To Setup Guide

## Adding New Pages
1. clone/fork this repo
1. optionally install mkdocs if you dont have it to preview pages
    - python: `pip install mkdocs-material`
    - to preview, `cd` to `flip-wiki` and run `mkdocs serve` and open the localhost link given
    - any changes you make to files while doing this will be auto added live in your web browser view
1. enter the `flip-wiki/docs` folder
1. create whatever doc files you want in named `.md` files.
1. once done, add them to the `flip-wiki/mkdocs.yml` towards the bottom under the `Navigation Heirarchy` section, following the pattern of the other `.md` files.
1. if the preview looks good when using `mkdocs serve`, submit a pull request. 

for more in depth features, see the [MkDocs-material guide](https://squidfunk.github.io/mkdocs-material/reference/)
