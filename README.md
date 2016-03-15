# flycheck-google-cpplint.el

Add Google C++ Style checker for [Flycheck](https://github.com/flycheck/flycheck).

If you're want to write code according to the
[Google C++ Style Guide](http://google-styleguide.googlecode.com/svn/trunk/cppguide.xml)
, this will help a great deal.

I recommend that the package
[google-c-style](http://melpa.milkbox.net/#/google-c-style)
also installed with.

## Installation

As usual, from [MELPA](http://melpa.milkbox.net).

In your [Cask](http://cask.github.io) file:

```
(source gnu)
(source melpa)

(depends-on "flycheck-google-cpplint")
```

In your `init.el`:

```
(eval-after-load 'flycheck
  '(progn
     (require 'flycheck-google-cpplint)
     ;; Add Google C++ Style checker.
     ;; In default, syntax checked by Clang and Cppcheck.
     (flycheck-add-next-checker 'c/c++-cppcheck
                                '(warning . c/c++-googlelint))))
```

If you not use `cppcheck`. You have need to change `flycheck-add-next-checker`.

```
(flycheck-add-next-checker 'c/c++-clang
                           '(warning . c/c++-googlelint))
```

## Usage

### Install cpplint.py

```
$ wget http://google-styleguide.googlecode.com/svn/trunk/cpplint/cpplint.py
$ sudo mv cpplint.py /usr/local/bin/cpplint.py
$ sudo chmod 755 /usr/local/bin/cpplint.py
```

You should be able to run the `cpplint.py` command in Emacs.
If above location,

```
(executable-find "cpplint.py") ; => "/usr/local/bin/cpplint.py"
```

or

```
(custom-set-variables
 '(flycheck-c/c++-googlelint-executable "/usr/local/bin/cpplint.py"))
```

### Configure for cpplint.py

```
(custom-set-variables
 '(flycheck-googlelint-verbose "3")
 '(flycheck-googlelint-filter "-whitespace,+whitespace/braces")
 '(flycheck-googlelint-root "project/src")
 '(flycheck-googlelint-linelength "120"))
```

## License

This program is free software: you can redistribute it and/or modify it under
the terms of the GNU General Public License as published by the Free Software
Foundation, either version 3 of the License, or (at your option) any later
version.

This program is distributed in the hope that it will be useful, but WITHOUT ANY
WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.  See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along with
this program.  If not, see http://www.gnu.org/licenses/.

See
[COPYING](https://github.com/flycheck/flycheck-google-cpplint/blob/master/COPYING)
for details.
