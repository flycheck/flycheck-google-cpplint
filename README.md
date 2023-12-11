[![License: GPL v3](https://img.shields.io/badge/License-GPL%20v3-green.svg)](https://www.gnu.org/licenses/gpl-3.0)
[![MELPA](https://melpa.org/packages/flycheck-google-cpplint-badge.svg)](https://melpa.org/#/flycheck-google-cpplint)
[![MELPA Stable](https://stable.melpa.org/packages/flycheck-google-cpplint-badge.svg)](https://stable.melpa.org/#/flycheck-google-cpplint)

# flycheck-google-cpplint.el

[![CI](https://github.com/flycheck/flycheck-google-cpplint/actions/workflows/test.yml/badge.svg)](https://github.com/flycheck/flycheck-google-cpplint/actions/workflows/test.yml)

Add Google C++ Style checker for [Flycheck](https://github.com/flycheck/flycheck).

If you're want to write code according to the
[Google C++ Style Guide](https://google.github.io/styleguide/cppguide.html)
, this will help a great deal.

I recommend that the package
[google-c-style](https://melpa.org/#/google-c-style)
also installed with.

## 💾 Installation

As usual, from [MELPA](https://melpa.org/#/).

In your [Cask](http://cask.github.io) file:

```
(source gnu)
(source melpa)

(depends-on "flycheck-google-cpplint")
```

In your `init.el`:

```el
(eval-after-load 'flycheck
  '(progn
     (require 'flycheck-google-cpplint)
     ;; Add Google C++ Style checker.
     ;; In default, syntax checked by Clang and Cppcheck.
     (flycheck-add-next-checker 'c/c++-cppcheck
                                '(warning . c/c++-googlelint))))
```

If you not use `cppcheck`. You have need to change `flycheck-add-next-checker`.

```el
(flycheck-add-next-checker 'c/c++-clang
                           '(warning . c/c++-googlelint))
```

## 🔧 Usage

### Install `cpplint` through `pip`

```
$ pip install cpplint
```

*P.S. Make sure cpplint is in your environment path settings*

### Configure for cpplint.py

```el
(custom-set-variables
 '(flycheck-googlelint-verbose "3")
 '(flycheck-googlelint-filter "-whitespace,+whitespace/braces")
 '(flycheck-googlelint-root "project/src")
 '(flycheck-googlelint-linelength "120"))
```

## 🛠️ Contribute

### 🔬 Development

To run the test locally, you will need the following tools:

- [Eask](https://emacs-eask.github.io/)
- [Make](https://www.gnu.org/software/make/) (optional)

Install all dependencies and development dependencies:

```sh
$ eask install-deps --dev
```

To test the package's installation:

```sh
$ eask package
$ eask install
```

To test compilation:

```sh
$ eask compile
```

**🪧 The following steps are optional, but we recommend you follow these lint results!**

The built-in `checkdoc` linter:

```sh
$ eask lint checkdoc
```

The standard `package` linter:

```sh
$ eask lint package
```

*📝 P.S. For more information, find the Eask manual at https://emacs-eask.github.io/.*

## ⚜️ License

This program is free software; you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see <https://www.gnu.org/licenses/>.

See [`COPYING`](./COPYING) for details.

