# wget Commands

## To clone a website for offline use:

1. mkdir for site
2. cd to that dir
3. `wget --limit-rate=200k --no-clobber --convert-links --random-wait -r -p -E -e robots=off -U mozilla https://www.SOME_WEBSITE.com`

source:  https://gist.github.com/stvhwrd/985dedbe1d3329e68d70


## To download all files in directory, FebruaryFiles of a url:

`wget -r --no-parent  https://www.ponomar.net/maktabah/FebruaryFiles/`

Note: “-r” is recursive
