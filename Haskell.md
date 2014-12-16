Learn Haskell
=============

Kuali.co specific haskell resources, tutorial, etc. 

Installation
-----------

Install GHC 7.8 and Cabal 1.20 on a mac: http://ghcformacosx.github.io/. Run the app for instructions.

Install dev tools
-------------------------

Install all of your top-level dependencies at once, to avoid conflicts

    cabal install alex happy ghc-mod hdevtools

Books and Curricula
-------------------

[Learn You a Haskell for Great Good!](http://learnyouahaskell.com/chapters) - Great at the theory. Gets confusing around chapter 11, so ask for help at that point. Preferred by both Jamison and Murphy

[CIS 194: Introduction to Haskell](http://www.seas.upenn.edu/~cis194/spring13/index.html) - This is a full class with homework assignments you can do. Sean liked it, but Jamison said it was confusing. The homework assignments are great though. 

[Bitemyapp's Curriculum](https://github.com/bitemyapp/learnhaskell) - this is a "meta curriculum" like this document and points to the above two in a particular order. Check it out if you want a list of more resources.

Problems
--------

[Hackerrank Functional Problems](https://www.hackerrank.com/domains/fp/intro) - Good easy problems to get your feet wet. These are only good for chapters 1-10 in LYAH. They don't do anything to help you understand how to build a webserver. 

Tutorials
---------

[Making a website with Haskell](http://adit.io/posts/2013-04-15-making-a-website-with-haskell.html) - tutorial for scotty, which is like express.js. NOTE: on step 2, you must remove the constraints from the build-depends field. Ask jamison if you get stuck. 


Configuring Vim
---------------

There are multiple ways to do this, but this is what @seanhess currently recommends.

Note: Make sure you installed hdevtools <a href="#install-dev-tools">as described above</a>

Vim Plugins

- [Syntastic](https://github.com/scrooloose/syntastic)
- [vim-hdevtools](https://github.com/bitc/vim-hdevtools)

Vim Configuration

```
Plugin 'wlangstroth/vim-haskell'
Plugin 'bitc/vim-hdevtools'
Plugin 'scrooloose/syntastic'
Plugin 'scrooloose/nerdcommenter'


let g:syntastic_aggregate_errors = 1
let g:syntastic_always_populate_loc_list = 1
let g:syntastic_auto_loc_list=1
let g:syntastic_haskell_checkers = ['hdevtools']

let g:NERDCustomDelimiters = {
    \ 'haskell': { 'left': '--' },
    \ }

```

Now you should be able to do the following:

- single-line comments
- on save it will update errors
- see errors in the error window
- see erorrs highlighted inline
- `:HdevtoolsInfo` will show you the type of a function and where it is defined

Configuring Sublime Text
------------------------

[Sublime Haskell](https://github.com/SublimeHaskell/SublimeHaskell)


Using Cabal
-----------

    # always work in a sandbox
    cabal sandbox init

    # Create a `.cabal` file for your project
    cabal init

    # Add dependencies to the build-depends field and then install them
    cabal install --only-dependencies

    # At some point, when you have your main dependencies specified
    cabal freeze

You should check in `my-project.cabal` and `cabal.config`, but ignore `cabal.sandbox.config. Here's an wample `.gitignore`

    dist
    cabal-dev
    *.o
    *.hi
    *.chi
    *.chs.h
    .virtualenv
    .hsenv
    .cabal-sandbox/
    cabal.sandbox.config

FAQ
---

### I can't get cabal to install a new package. It says that packages conflict. 

If you are installing cabal packages globally: remove `~/.cabal` and reinstall all the global packages you need at once. 

    rm -r ./cabal
    # add your package to the end of this
    cabal install alex happy ghc-mod hdevtools

If you are working in a project, first [make sure you are using sandboxes](#using-cabal)

    rm -r .cabal-sandbox
    cabal install --only-dependencies

Optionally, if that doesn't work, remove `cabal.config` before running the above, then run `cabal freeze` when you are done to clear out the specific dependencies.
    






