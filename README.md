#Elfstats.org

Branch `gh-pages-jekyll` contains source codes of [elfstats.org](http://elfstats.org) web site created with [Jekyll](http://jekyllrb.com). Branch `gh-pages` contains HTML pages generated with Jekyll and proudly hosted by [GitHub Pages](http://pages.github.com). This separation is done because we use some custom plugins that cannot be properly processed on GitHub side during automatic pages generation, thus we have to generate content locally and manually release pre-generated files.

##Build elfstats.org locally from `gh-pages-jekyll`

Requirements: 

* Ruby
* RubyGems
* Bundler
* ImageMagick: `brew install imagemagick`
* rmagick: `gem install rmagic`

Build and launch server: `bundle exec jekyll serve`

Go to `http://localhost:4000`

##Deploy to GitHub Pages

* Build site using Jekyll as described above
* Copy the contents of `_site/` to `gh-pages` branch. 
* Push `gh-pages` branch to GitHub.



