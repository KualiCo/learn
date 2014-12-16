Learn Haskell
=============

Kuali.co specific haskell resources, tutorial, etc. 

Installation
-----------

Install GHC 7.8 and Cabal 1.20 on a mac: http://ghcformacosx.github.io/

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

System dependencies

- [`cabal install hdevtools`](https://github.com/bitc/hdevtools)

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





