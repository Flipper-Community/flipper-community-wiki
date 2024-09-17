# Flipper Community wiki
This is the repo for the [Flipper community wiki](https://flipper-community.github.io/flipper-community-wiki/).
If you'd like to contribute to this wiki, you may fork the repo and offer your changes as a pull request

# Technical docs
This wiki is built using the mkdocs builder

# tl;dr How to Guides

## Adding New Pages
1. clone/fork this repo
1. optionally install mkdocs if you dont have it to preview pages
    - python: `pip install mkdocs`
    - to preview, `cd` to `flip-wiki` and run `mkdocs serve` and open the localhost link given
    - any changes you make to files while doing this will be auto added live
1. enter the `flip-wiki/docs` folder
1. create whatever doc files you want in named `.md` files.
1. once done, add them to the `flip-wiki/mkdocs.yml`, following the pattern of the other `.md` files.
1. if the preview looks good when using `mkdocs serve`, submit a pull request. 

for more in depth features, see the [MkDocs official getting started guide](https://www.mkdocs.org/getting-started/)