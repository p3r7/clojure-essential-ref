# clojure-essential-ref

Emacs packages providing commands to browse the Clojure documentation of a symbol in book [Clojure, The Essential Reference](https://livebook.manning.com/book/clojure-the-essential-reference/):

 - `clojure-essential-ref`: browse the default way (see _Configuration_)
 - `clojure-essential-ref-web`: browse online in the web version of the book (_liveBook_)
 - `clojure-essential-ref-nov`: browse offline in a local ebook (provided by optional sibling package `clojure-essential-ref-nov.el`, depends on [nov.el](https://depp.brause.cc/nov.el/))

They require a CIDER session to be launched to perform fully-qualified symbol resolution.

They behave similarly to `cider-clojuredocs-web`, including the default proposal of _symbol-at-point_. They are a nice companion to the latter (alongside `cider-doc`).

For more context, read the [accompanying blog post](https://www.eigenbahn.com/2020/06/04/emacs-clojure-essential-ref).


## Installation

The packages are not yet available on [Melpa](https://melpa.org/).

For now, the recommended way to install is with [use-package](https://github.com/jwiegley/use-package), [quelpa](https://github.com/quelpa/quelpa) and [quelpa-use-package](https://github.com/quelpa/quelpa-use-package).

To get only the web browsing mode:

```el
(use-package clojure-essential-ref
  :quelpa (clojure-essential-ref :fetcher github :repo "p3r7/clojure-essential-ref"))
```

Optionally, to get the offline ebook browsing mode (depends on [nov.el](https://depp.brause.cc/nov.el/)):

```el
(use-package clojure-essential-ref-nov
  :ensure nil
  :after clojure-essential-ref
  :init
  (setq clojure-essential-ref-nov-epub-path "~/Downloads/Clojure_The_Essential_Reference_v29_MEAP.epub"))
```

## Configuration

#### ebook file

The offline ebook browing mode needs you to configure the path to the book (EPUB format):

```el
(use-package clojure-essential-ref-nov
  ;; ...

  :init
  (setq clojure-essential-ref-nov-epub-path "~/Downloads/Clojure_The_Essential_Reference_v29_MEAP.epub")
```

#### Default browsing mode

The default browing mode (command `clojure-essential-ref`) is the online _liveBook_.

To use the offline ebook browing mode instead:

```el
(use-package clojure-essential-ref-nov
  ;; ...

  :init
  (setq clojure-essential-ref-default-browse-fn #'clojure-essential-ref-nov-browse)
```


## Usage

Under a CIDER session, just call the command:

    M-x clojure-essential-ref

For convenience sake, you can bind it to a keyboard shortcut:

```el
(use-package clojure-essential-ref
  ;; ...
  :bind (
         :map cider-mode-map
         ("C-h F" . clojure-essential-ref)
         :map cider-repl-mode-map
         ("C-h F" . clojure-essential-ref)))
```


## Legibility

This code uses form feeds (`^L` character) as separators.

Package [form-feed](https://github.com/wasamasa/form-feed) makes them appear as intended.
