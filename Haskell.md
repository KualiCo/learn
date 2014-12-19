Learn Haskell
=============

Kuali.co specific haskell resources, tutorial, etc. 

Installation
-----------

Install GHC 7.8 and Cabal 1.20 on a mac: http://ghcformacosx.github.io/. Run the app and follow the instructions.

Install dev tools
-------------------------

Install all of your global dependencies at once, to avoid conflicts. Only install dev tools globally.

    cabal update
    cabal install alex happy ghc-mod hdevtools

Books and Curricula
-------------------

[Learn You a Haskell for Great Good!](http://learnyouahaskell.com/chapters) - Great at the theory. Gets confusing around chapter 11, so ask for help at that point. Preferred by both Jamison and Murphy

[CIS 194: Introduction to Haskell](http://www.seas.upenn.edu/~cis194/spring13/index.html) - This is a full class with homework assignments you can do. Sean liked it, but Jamison said it was confusing. The homework assignments are great though. 

[Bitemyapp's Curriculum](https://github.com/bitemyapp/learnhaskell) - this is a "meta curriculum" like this document and points to the above two in a particular order. Check it out if you want a list of more resources.

Problems
--------

[HackerRank Functional Problems](https://www.hackerrank.com/domains/fp/intro) - Good easy problems to get your feet wet. These are only good for chapters 1-10 in LYAH. They don't do anything to help you understand how to build a webserver. 

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

You should check in `my-project.cabal` and `cabal.config`, but ignore `cabal.sandbox.config`. Here's a sample `.gitignore`

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

Why Haskell
-----------

MAINTENANCE

We can maintain a project 10x larger before hitting the Great Slowdown. Our code will also be more reliable.

- Functional - Factoring code functionally - divides code into smaller pieces. Much more composable. Much less monolithic. 
- Functional - Focus on what, not how
- Type system - We can edit a foreign codebase with much more confidence. Haskell solves the bus problem. 
- Type system - Enforces the original authors intent in a way that does not need be maintained separately
- Type system - Reduces the complexity of inter-service communication (using servant)
- QuickCheck - much better testing made possible through types

COMMUNITY

The Haskell community is awesome, and will have a positive impact on our culture and our ability to ship. Programming as a whole headed that direction.

- Community builds off each others' work better. 
- Community is helpful, inventive, positive, and growing.
- Programming is headed towards stricter types (see Rust, Go)
- Types themselves are a area of huge advancement and research (See Idris)

OUR TEAM

- plenty of people who are enthusiastic about Haskell
- people who know it are awesome programmers

OTHER

- We need higher level abstractions to create larger programs. You give up understanding how things work sometimes in exchange for the ability to reason at the next level. (Assembly vs C, C vs Javascript, Javascript vs Haskell)
- runtime performance
- emphasizes safety

MORE READING

- [Real World Haskell: Why functional Programming? Why Haskell?](http://book.realworldhaskell.org/read/why-functional-programming-why-haskell.html)
- [Why the world needs Haskell](http://www.devalot.com/articles/2013/07/why-haskell.html)

COMPANIES USING HASKELL

- [IMVU: What it's like to use Haskell](http://engineering.imvu.com/2014/03/24/what-its-like-to-use-haskell/) 
- [Haskell at JanRain](http://janrain.com/blog/haskell-janrain/)
- [Quora: What startups use Haskell for production work?](http://www.quora.com/What-startups-use-Haskell-for-production-work)
- [MailRank: Running a startup on Haskell](http://bos.github.io/strange-loop-2011/talk/talk.html)
- [FP Complete Case Studies](https://www.fpcomplete.com/page/case-studies) Bump, Janrain, Silk, Netrium, SAFE, and Scrive. 





FAQ
---

### I can't get cabal to install a new package. It says that packages conflict. 

If the errors message says you can try to forcing reinstalls, go ahead and see if it works

    cabal install --force-reinstalls

Otherwise, if you are installing cabal packages globally:

    # remove all installed cabal packages
    rm -r ~/.ghc

    # reinstall global packages (add the one you want to the end of this list)
    cabal install alex happy ghc-mod hdevtools

If you are working in a project, first [make sure you are using sandboxes](#using-cabal)

    rm -r .cabal-sandbox
    cabal install --only-dependencies

Optionally, if that doesn't work, remove `cabal.config` before running the above, then run `cabal freeze` when you are done to clear out the specific dependencies.



    






