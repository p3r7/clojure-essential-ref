# clojure-essential-ref

An Emacs package to provide a command to browse the Clojure documentation of a symbol in book [Clojure, The Essential Reference](https://livebook.manning.com/book/clojure-the-essential-reference/).

It needs a CIDER session to be launched to perform fully-qualified symbol resolution.

It behaves similarly to `cider-clojuredocs-web`, including the default proposal of _symbol-at-point_. As such it's a nice companion to the latter (alongside `cider-doc`).

For more context, read the [accompanying blog post](https://www.eigenbahn.com/2020/06/04/emacs-clojure-essential-ref).


## Installation

The package is not yet available on [Melpa](https://melpa.org/).

For now, the recommended way to install is with [use-package](https://github.com/jwiegley/use-package), [quelpa](https://github.com/quelpa/quelpa) and [quelpa-use-package](https://github.com/quelpa/quelpa-use-package).

```el
(use-package clojure-essential-ref
  :quelpa (with-shell-interpreter :fetcher github :repo "p3r7/clojure-essential-ref"))
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
