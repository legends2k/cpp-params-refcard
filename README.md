A reference card / cheat sheet for choosing the right kind of function parameter to receive and return objects in C++ functions.  Download [reference card][card].

C++ gives fine-grained control over argument passing and returning that many options exits.  There’s been enough over-thinking and discussions in the community.  Thankfully [experts have noticed this and have arrived at sane defaults](https://github.com/CppCon/CppCon2014/blob/master/Presentations/Back%20to%20the%20Basics!%20Essentials%20of%20Modern%20C%2B%2B%20Style/Back%20to%20the%20Basics!%20Essentials%20of%20Modern%20C%2B%2B%20Style%20-%20Herb%20Sutter%20-%20CppCon%202014.pdf).  Since the options are more and involved, having a ready reckoner is useful when coding.

The reference card is written in the venerated [Org mode][].

# Dependencies

* Emacs with Org mode
* [CheatSheet][] by [Musa Al-hassy][]
* [pdfTeX][] with some additional packages
* [Pygments][] for syntax highlighting (`$PATH` should have `pygmentize`; optional)

On Arch Linux, I’d to install these packages

* `texlive-bin` (for `pdflatex`)
* `texlive-latexextra` (for `wrapfig.sty`)
* `texlive-fontsextra` (for `bbold.sty`)
* `texlive-science` (for mathematic symbols `stmaryrd.sty`; optional)
* `community/pygmentize`

As a single command

``` shell
yay -S --needed extra/texlive-latexextra extra/texlive-fontsextra extra/texlive-science community/pygmentize
```

Other Linux repositories should have equivalent packages to get these.

## Emacs Packages

* [org-plus-contrib][] (from https://orgmode.org/elpa/)
* [org-ref][] (optional, for citations, bibliography, …)

[card]: https://github.com/legends2k/cpp-params-refcard/releases
[CheatSheet]: https://github.com/alhassy/CheatSheet
[pdfTeX]: http://www.tug.org/applications/pdftex/
[Org mode]: https://orgmode.org/
[org-plus-contrib]: https://orgmode.org/worg/org-contrib/
[org-ref]: https://github.com/jkitchin/org-ref
[pygments]: https://pygments.org/
[Musa Al-hassy]: http://www.cas.mcmaster.ca/~alhassm/

Append this to your Emacs configuration

``` elisp
;; for the the CheatSheetSetup.org section headings to be ignored
(require 'ox-extra)
(ox-extras-activate '(ignore-headlines))

;; for syntax highlighting source blocks
(setq org-latex-listings 'minted
      org-latex-packages-alist '(("" "minted"))
      org-latex-pdf-process
      '("pdflatex -shell-escape -output-directory %o %f"
        "biber %b"
        "pdflatex -shell-escape -output-directory %o %f"
        "pdflatex -shell-escape -output-directory %o %f"))
```

# Generation

* Edit `cpp-params-refcard.org`
* Save
* Export <kbd>C-c C-e l o</kbd>

# To Do

* Add horizontal rules between sections
* Use _mononoki_ font for monospace using `fontspec` package

# See Also

* [LaTeX cheetsheet template](https://wch.github.io/latexsheet/) used to prepare [Math Cheatsheet](https://antongerdelan.net/teaching/3dprog1/maths_cheat_sheet.pdf) by Anton Gerdelan
  - [Preparing Cheatsheets - TeX.SE Post](https://tex.stackexchange.com/questions/8827/preparing-cheat-sheets)
